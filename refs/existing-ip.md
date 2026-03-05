# 已有 IP 参考图流程

## 为什么需要参考图

不要假设模型熟悉任何 IP 的视觉形象——即使是知名 IP，模型内化的表现也可能不准确，依赖 IP 名称往往生成泛化结果而非原版质感。**参考图是最可靠的还原手段。**

---

## Step 1：搜索并提取真实图片 URL

**首选来源：Fandom wiki**（`*.fandom.com`）

- 覆盖几乎所有主流 IP（游戏、动漫、影视）
- 图片托管于 `static.wikia.nocookie.net`，无需登录，可直接 curl 下载
- 角色页面的 `og:image` meta 标签即为该角色官方主图，一次 WebFetch 即可提取

**两步固定流程，不可跳过：**

**① WebSearch 直接定位角色的 Fandom wiki 页面**

```
WebSearch: "[角色名] [IP名称] site:fandom.com"
```

从结果中取角色专属页面（URL 格式：`https://[ip].fandom.com/wiki/[角色名]`）。

**② WebFetch 该页面，提取 og:image 的值**

```
WebFetch [角色wiki页面URL]
```

在返回内容中找：
```html
<meta property="og:image" content="https://static.wikia.nocookie.net/..."/>
```

`content` 的值就是可直接使用的图片直链。若 `og:image` 指向的是低分辨率图，在页面的角色信息框（infobox）的 `<img src="...">` 中找高分辨率版本。

**Fandom 找不到时的备选顺序：**
1. 游戏 / 动漫官网角色页
2. 该 IP 的专属独立 wiki（如 Bulbapedia、Fire Emblem Wiki 等）
3. 以上都失败 → 跳至文末"搜索失败降级方案"

---

## Step 2：根据当前生图工具选择参考图用法

### 工具 A：nano-banana（有 `-r` 参数，直接传图）

```bash
curl -fsSL "[图片URL]" -o /tmp/ip-ref.jpg
nano-banana "[prompt]" -r /tmp/ip-ref.jpg -a [比例] -s 2K -m pro -o [输出名]
rm /tmp/ip-ref.jpg
```

`-r` 做风格迁移，参考图越准确、prompt 描述越详细，结果越贴近目标。

---

### 工具 B：neta（无参考图参数，先读图再写 prompt）

neta 的 `make-image` 不支持直接传参考图，需要先由 Claude 读取图片内容，将视觉特征转化为详细 prompt：

**① 用 WebFetch 或 Read 读取参考图**

```
WebFetch [图片URL]  ← Claude 读取图片，提取视觉信息
```

**② 从参考图中提取以下信息，写入 prompt**

- 整体美术风格（写实 3D / 赛璐璐动画 / 厚涂插画 / 像素等）
- 角色发色、发型、眼睛颜色
- 服装款式、主要颜色、材质质感
- 标志性道具或装备
- 光影风格、色调倾向

**③ 用提取到的信息构建详细 prompt 调用 neta**

```bash
npm --prefix [neta路径] run start -- make-image \
  -p "[美术风格]，[发色发型]，[眼睛]，[服装颜色与款式]，[标志性道具]，[姿势]，[背景]，[光影氛围]" \
  -a [比例]
```

---

## Step 3：prompt 里描述视觉，不只写名字

无论使用哪种工具，prompt 中都必须明确写出角色的视觉特征，不能只写角色名：

```
[IP的美术风格]，[角色实际外貌：发色、服装颜色、标志性装备]，[姿势]，[背景]
```

---

## 搜索失败时的降级方案

搜不到可用图片时，在 prompt 中把以下信息描述清楚：
- 该 IP 的整体美术风格（写实 3D / 动漫 / 像素等）
- 角色的标志性颜色和轮廓
- 服装材质和关键道具

---

## 准确度预期

| 条件 | 工具 | 预期结果 |
|------|------|---------|
| 有参考图 + prompt 详细 | nano-banana `-r` | 风格与关键特征基本吻合 |
| 有参考图 + prompt 详细 | neta（图转 prompt）| 关键特征吻合，风格近似 |
| 有参考图 + prompt 简略 | 任意 | 风格匹配，细节可能漂移 |
| 无参考图 + prompt 详细 | 任意 | 合理近似，无风格保证 |
| 无参考图 + prompt 只写名字 | 任意 | 泛化结果，基本不像原版 |
