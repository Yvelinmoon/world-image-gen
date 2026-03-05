# 已有 IP 参考图流程

## 为什么需要参考图

参考图的唯一用途是**锁定画风**——让生图结果与目标 IP 的美术风格保持一致。

**不要从参考图中复制角色特征**（发色、服装、道具、外貌等）。这些内容应来自用户的世界观档案或当前 session 中的角色描述。参考图只提供：渲染风格、线条质感、色彩倾向、光影处理方式。

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

**② 从参考图中只提取画风信息，写入 prompt 开头**

- 整体美术风格（写实 3D / 赛璐璐动画 / 厚涂插画 / 像素等）
- 线条风格（粗线描边 / 细腻线稿 / 无线条等）
- 色彩倾向（高饱和 / 低饱和 / 冷色调 / 暖色调等）
- 光影处理（硬光 / 软光 / 厚涂阴影 / 平涂等）

**不要**从参考图中提取角色发色、服装、道具等具体特征——这些来自世界观档案。

**③ 用提取到的画风 + 世界观档案中的角色描述构建 prompt**

```bash
npm --prefix [neta路径] run start -- make-image \
  -p "[画风风格]，[线条]，[色彩倾向]，[光影]，（以下来自世界观档案）[角色外貌]，[服装]，[姿势]，[背景]" \
  -a [比例]
```

---

## Step 3：prompt 构建原则

参考图只贡献**画风描述词**，放在 prompt 开头；角色的一切具体特征来自**世界观档案**：

```
[画风：渲染风格、线条、色彩倾向、光影] + [角色：外貌/服装/道具，来自档案] + [姿势] + [背景]
```

不要在 prompt 里写 IP 角色名，也不要把参考图角色的外貌特征带入。

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
