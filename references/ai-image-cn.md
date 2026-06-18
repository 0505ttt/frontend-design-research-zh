# 中文 AI 生图生态（补充主 skill Phase 8）

> 主 skill Phase 8 已覆盖国际工具（Midjourney / DALL-E / Flux / SD），本文件补充中文 AI 生图生态 + Codex 工作流，**国内项目优先考虑**。

---

## 一、工具选型矩阵（中文场景 + Codex 优先）

| 资产类型 | 推荐中文工具 | 推荐国际工具 | **Codex 工作流（推荐）** | 选择标准 |
|---|---|---|---|---|
| Hero / 艺术背景 | **即梦 AI** / 豆包图像 | Midjourney v6+ | **Codex 写 prompt → 即梦/MJ 出图** | 中文 prompt 友好度 / 艺术感 |
| 含文字图（OG / 海报） | **通义万相** | DALL-E 3 | **Codex 直出（GPT-Image-1）** | 中文文字嵌入准确度 |
| Logo / 矢量 icon | Recraft / **即梦 AI 矢量模式** | Recraft | Codex 写 prompt → Recraft | SVG 输出质量 |
| 写实素材 / 产品图 | **通义万相** / 豆包 | Flux.1 | **Codex 直出（GPT-Image-1）** | 写实度 |
| Hero 动态背景视频 | **可灵 AI** | Runway / Sora | Codex 写脚本 → 可灵 | 中文场景理解 |
| **批量 prompt 工程** | — | — | **⭐ Codex 一把梭**（最适合你） | 结构化批量生成 |
| 兜底免费方案 | 即梦（每日免费额度） | Stable Diffusion XL + LoRA | Codex + GPT-Image-1（订阅内） | 零成本可控 |

**核心理念**：Codex 不是直接生图工具，而是**「prompt 工程指挥官」** —— 帮你批量写结构化 prompt，再调度即梦/通义万相/MJ 出图。同时 Codex 集成 ChatGPT 的 GPT-Image-1 模型，可一站式直出含文字图（OG、海报）。

---

---

## 二、各工具详细说明

### 1. 即梦 AI（Jimeng，字节系）
- **入口**：https://jimeng.jianying.com/
- **强项**：
  - 中文 prompt 理解最准（无需翻译）
  - 米国风 / 极简风 / 编辑设计可控
  - 免费额度充足（每日有积分）
  - 矢量图模式（Logo 友好）
- **弱项**：写实人像略输 Flux
- **适用**：网页背景、Hero 图、Logo、icon

### 2. 通义万相（阿里系）
- **入口**：https://tongyi.aliyun.com/wanxiang/
- **强项**：
  - 企业风 / 数据图表强
  - 中文文字嵌入准确（海报、OG 图）
  - 写实产品图优秀
- **弱项**：艺术感不如即梦
- **适用**：B 端 OG 图、产品 hero、信息图

### 3. 可灵 AI（快手系）
- **入口**：https://klingai.com/
- **强项**：
  - 视频生成（hero 动态背景）
  - 中文场景理解强
  - 4-10 秒短视频
- **弱项**：生成为视频，需后处理
- **适用**：动态 hero 背景、产品演示

### 4. 豆包图像（字节系）
- **入口**：通过豆包 App / Coze 平台
- **强项**：
  - 编辑设计语言适配
  - 与即梦互补
  - 集成在豆包生态
- **弱项**：风格偏年轻向
- **适用**：内容卡片、装饰图

### 5. ⭐ Codex（OpenAI，**作者主力工具**）

> Codex 不是图片生成器，而是**「prompt 工程层 + 多模态调度」**。本 skill 假设你日常用 Codex 生成代码和文档，所以应该让它顺便把生图 prompt 也批量产出。

#### 5.1 Codex 的三种生图角色

**角色 A：Prompt 工程指挥官（最常用）**
让 Codex 在写前端代码时，**顺便产出**每个资产的完整 prompt 列表（含主 prompt + 2-3 变体 + 反陷阱负面词），直接喂给即梦/MJ/通义万相。

**角色 B：直接生图（GPT-Image-1）**
ChatGPT Pro / Plus 内的 Codex 可调用 `GPT-Image-1`（原 DALL-E 3 升级版），适合：
- 含文字图（OG、海报、卡片标题）—— 文字嵌入比通义万相更准
- 写实产品图
- 编辑设计风插画
- ⚠️ 弱项：纯艺术感弱于 MJ；中文长 prompt 需先翻译

**角色 C：批量调度**
让 Codex 写一个 Node/Python 脚本，并行调用即梦 API + 通义万相 API + MJ API，一次性生成全部资产。

#### 5.2 Codex Prompt 模板（推荐你常备）

```
我在做 [项目类型] 前端。设计方向：[极简/编辑/技术地下...]。
配色：主色 [hex]，强调色 [hex]（禁止 indigo/violet/purple）。
字体：标题 [font]，正文 [font]。

请按以下表格批量产出 8 个资产生图 prompt（每个含主 prompt + 2 变体 + 反陷阱 --no 列表）：

| # | 资产 | 尺寸 | 用途 |
|---|---|---|---|
| 1 | Hero 背景 | 1920×1080 | 首屏装饰 |
| 2 | Logo | 512×512 SVG | 品牌 |
| 3 | OG 图 | 1200×630 | 社交分享 |
| ... |

输出格式：Markdown 表格，每行一个资产，prompt 字段含完整可复制的中英文 prompt。
反陷阱 --no 列表必须包含：purple, violet, indigo, magenta, ink, calligraphy, mascot
```

#### 5.3 Codex vs 即梦/通义万相 分工

| 任务 | 用 Codex | 用即梦/通义万相 |
|---|---|---|
| 写 prompt | ✅ 强项（结构化、批量） | ❌ 浪费 tokens |
| 含文字 OG / 海报 | ✅ GPT-Image-1 直出 | ⚠️ 通义万相次选 |
| 纯艺术 Hero 背景 | ❌ 艺术感弱 | ✅ 即梦首选 |
| 写实产品图 | ✅ GPT-Image-1 | ✅ 通义万相（中文场景更准） |
| Logo / 矢量 | ⚠️ 不直接出 SVG | ✅ 即梦矢量模式 / Recraft |
| 动态背景视频 | ❌ 不支持 | ✅ 可灵 |

#### 5.4 Codex 工作流（推荐你日常用）

```
1. 在 Codex 里贴上面的 Prompt 模板 → 拿到 8 个资产的批量 prompt 表
2. 把表格里的中文 prompt 复制到即梦（艺术背景）/ 通义万相（含文字）/ 可灵（视频）
3. 把英文 prompt 复制到 MJ（如果需要更艺术感）
4. 出图后让 Codex 写后处理脚本：裁切 / 调色 / 压缩为 WebP / 生成 srcset
```

**优势**：Codex 把"想 prompt"这件最累的事自动化了，你只需要审稿选图。

---

## 三、中文 AI 生图最佳实践

### Prompt 结构（中文）
```
[主体描述]，[风格]，[配色]，[构图]，[情绪/氛围]，
不要：[反陷阱词列表]
```

### 反陷阱中文负面词模板
```
不要：紫色、蓝紫渐变、水墨画、书法、印章、复古、国风具象、
     卡通、Q 版吉祥物、拟人形象、模糊、低质量、水印、文字残留
```

### 中英文 prompt 对照示例
- **Hero 背景图**：
  - 中文：抽象 3D 几何雕塑，深绿色单色调，留白 60%，编辑设计感，不要紫色不要国风
  - 英文：abstract 3D geometric sculpture, deep green monochrome, 60% whitespace, editorial design --no purple violet indigo ink oriental mascot

### 国内项目优先级（Codex 优先版）
1. **⭐ 你日常的工作流**：Codex 写批量 prompt → 即梦出艺术图 / 通义万相出含文字图 / 可灵出视频
2. 服务器在国内 / 用户主要在中国 → 即梦 + 通义万相（Codex 调度）
3. 需要视频背景 → Codex + 可灵
4. 含文字图（OG / 海报）→ Codex 直出 GPT-Image-1（最准）
5. 海外项目 / 艺术感要求极高 → Codex 写英文 prompt → Midjourney

---

## 四、调试方法论（中文场景特化）

| 症状 | 中文场景原因 | 中文工具解决方案 |
|---|---|---|
| 还是带水墨元素 | 中文 prompt 含「中式」「东方」等暗示词 | 即梦重写：明确「现代抽象几何」 |
| 紫色残留 | 即梦/豆包训练数据也有污染 | 强化「不要紫色」到 prompt 头部 |
| 文字糊 | 通义万相文字嵌入失败 | 改用 DALL-E 3 或后处理叠加文字 |
| 风格太"年轻" | 豆包偏年轻向 | 切换到即梦 + 「编辑设计」关键词 |

---

## 五、参考资源

- [AI 生成的 UI 太丑？3 步秒变高级感（Skill Hub 中国）](https://www.skill-cn.com/practice/67)
- [怎么让 AI 写出好看有设计感的网页（53AI）](https://www.53ai.com/news/neirongchuangzuo/2025063095706.html)
- [热门 AI 技巧分享：如何做高级感的网页 UI（YouTube）](https://www.youtube.com/watch?v=0ex74hEqOa0)
