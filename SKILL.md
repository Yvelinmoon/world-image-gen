---
name: world-image-gen
description: 世界观生图专家。凡是涉及虚构世界、角色、剧情、设定的生图请求均使用此技能——角色立绘、道具、地图、场景、分镜等。模型无关，适配任何可用的生图工具。
---

# 世界观生图

## 生图工具优先级

按顺序选用当前 session 中可用的工具：nano-banana → neta → 其他可用生图工具。

---

## Step 1：加载世界上下文

从 world-builder 档案或当前 session 中提取：美术风格、色调、已有角色/场景描述。若无任何上下文，先询问用户的世界美术风格再继续。

---

## Step 2：检测已有 IP

用户提到已有 IP（游戏、动漫、小说、影视）时，**不要直接生图**，先读 `refs/existing-ip.md` 获取参考图搜索流程。

---

## Step 3：识别图片类型并加载对应 ref

| 用户说 | 类型 | 读取 |
|--------|------|------|
| 角色 / 立绘 / 人物 / character / portrait | 角色立绘 | `refs/character.md` |
| 道具 / 武器 / 物品 / item / weapon / prop | 道具图 | `refs/prop.md` |
| 设定图 / 参考图 / 三视图 / design sheet | 设定图 | `refs/design-sheet.md` |
| 地图 / map / 地形 / 城市 / 迷宫 | 地图 | `refs/map.md` |
| 图表 / 关系图 / 年表 / 势力图 / diagram | 图表 | `refs/diagram.md` |
| 场景 / 地点 / 环境 / 风景 / scene | 场景图 | `refs/scene.md` |
| 剧情图 / 情节 / 故事画面 / narrative | 剧情图 | `refs/narrative.md` |
| 分镜 / 漫画格 / storyboard / 面板 | 分镜图 | `refs/storyboard.md` |

识别类型后，读取对应 ref 文件，按其中的模板构建 prompt 并执行生图。
