---
name: 前端设计调研方法论
description: 当用户想为某项目（学术/产品/作品集/落地页）设计前端、需要 AI 配合做深度调研和方案输出时使用。覆盖项目理解、反陷阱意识（AI 紫色/文化主题/mascot 等）、用户调研指令模板、三文档输出结构（设计研究+生图提示词+实施 plan）、配色/字体/页面结构/AI 生图/实施 plan 方法论、可用插件映射、基于反馈的迭代调试。本 skill 教方法不教审美——不锁定任何具体配色/字体/风格方向。
license: MIT
allowed-tools:
  - WebSearch
  - mcp__web-search-prime__web_search_prime
  - mcp__web-reader__webReader
  - mcp__markitdown__convert_to_markdown
  - AskUserQuestion
  - Read
  - Write
  - Edit
metadata:
  version: 2.0.0
  language: zh-CN
  category: design-research
  tags: [frontend, design, anti-ai-pattern, methodology]
---

## 配套参考文件（v2.0 新增）

本 skill 拆分为入口 + 3 个独立可引用参考：

| 文件 | 用途 | 何时引用 |
|---|---|---|
| `references/anti-ai-patterns.md` | 反 AI 味陷阱完整清单 + 根因 | Phase 2 详查 |
| `references/ai-image-cn.md` | 中文 AI 生图生态（即梦/通义万相/可灵/豆包） | Phase 8 国内项目 |
| `references/ai-builder-prompts.md` | v0/bolt/lovable 喂养模板 | Phase 9 落地 |

# 前端设计调研方法论

> 把"用户想为项目设计前端"转化为"AI 输出可执行的三文档+迭代调试"的标准工作流。
> **核心约束**：本 skill 只写方法、流程、模板、检查清单，**不锁定具体审美决策**（不写死 hex / 字体名 / 参考站点 / prompt 内容）。

---

## 一、何时使用（When to Use）

### 🚀 Tier 0：快速路径（v2.0 新增，< 2 小时项目走这里）

如果满足以下任一条件，**跳过完整工作流**，直接走简化路径：

| 场景 | 快速路径 |
|---|---|
| 时间预算 < 2 小时 | 跳到 Phase 4 简化版：只输出**单文件 `design.md`**（含配色 + 字体 + 1 张参考站截图） |
| 用户已有 v0/lovable 草稿 | 跳过 Phase 1-3，直接进 **Phase 11 反馈分类迭代**，把现有草稿当作 v0 输入 |
| 用户只要配色方案 | 直接进 **Phase 5 配色方法论**，输出 1 推荐 + 2 备选即可 |
| 用户已有设计稿，只需实施 | 直接进 **Phase 9 实施 plan** + `references/ai-builder-prompts.md` |
| 用户要试新风格 | 直接进 **Phase 8 AI 生图** + `references/ai-image-cn.md`（国内）/ 国际工具 |

主动告诉用户：「这个任务可能不需要完整调研工作流，要不要直接走 Tier 0 快速路径？」

### 触发场景（完整路径）
用户出现以下任意情况时启用本 skill：

- "为我的项目设计前端 / 网页 / 展示页"
- "做个 portfolio / landing page / dashboard"
- 项目核心功能已完成，需要"包装"或"可视化"
- 用户对 AI 默认生成的前端不满意（"一股 AI 味" / "太丑" / "不够高端"）
- "前端该用什么配色 / 字体 / 风格？"
- "去网上深度调研怎么做这个前端"
- "帮我画几张背景图" + 想要的是高端可视化效果

### 不该使用的场景
- 纯后端 / API 任务（无前端需求）
- 用户已经定死了技术栈和设计稿，只需写代码
- 用户明确说"不用调研，直接照我的描述做"

---

## 二、核心原则（Core Principles）

| 原则 | 含义 |
|---|---|
| **方法 > 审美** | 教用户怎么决策，不替用户决策具体配色/字体 |
| **反陷阱优先** | 主动识别"AI 设计味破绽"（紫色、文化主题、mascot、mesh gradient 等）|
| **三文档结构** | 任何前端任务都应输出：设计研究 + 生图提示词 + 实施 plan |
| **用户驱动迭代** | 每版必让用户反馈，分阶段推进，不一次定生死 |
| **真实对标** | 配色/字体/风格必须指向真实存在的高质量站点作为锚点 |
| **教用户命令 AI** | 给用户可复用的指令模板，让 ta 学会更好指挥 AI |
| **检查清单驱动** | 每阶段用 checklist 验收，不靠感觉 |

---

## 三、Phase 1：项目理解（必备问题清单）

**触发后第一件事**：先问清楚，再开调研。**禁止跳过此阶段直接写文档**。

### 必问清单（用 AskUserQuestion 一次性问完）

| 维度 | 问题 | 备选答案 |
|---|---|---|
| 项目类型 | 这是什么类型的项目？ | 学术研究 / 产品功能 / 个人作品集 / 公司落地页 |
| 目标受众 | 谁会看这个页面？ | 老师（评分）/ 面试官 / 终端用户 / 自己存档 |
| 核心数据 | 有什么内容必须展示？ | 数字指标 / 文档 / 图表 / 交互 demo / 数据集 / 代码 |
| 已有产物 | 后端是否已有可消费的输出？ | API / JSON / PNG 图 / Markdown 报告 / 都没有 |
| 审美倾向 | 你喜欢哪种调性？ | 极简沉稳 / 大胆锋芒 / 编辑学术 / 技术地下 |
| 反例（关键） | **不喜欢什么样的？** | 让用户举例 ta 觉得丑的网站 / AI 生成示例 |
| 时间预算 | 多少工时可投入？ | 半天 / 1-2 天 / 1 周 |
| 部署目标 | 部署在哪？ | GitHub Pages / Vercel / 自托管 / 仅本地展示 |

### 反例收集技巧
**强烈推荐**让用户提供 1-3 个 ta **不喜欢**的网站截图或 AI 生成图。这比让 ta 描述"喜欢什么"高效 10 倍——负面反馈比正面偏好更精确。

---

## 四、Phase 2：反陷阱意识（**核心特色**）

AI 默认生成的"前端"有 5 大破绽。**任何调研输出前**都要先识别并主动避开。

### 陷阱清单

| # | 陷阱名称 | 表现 | 触发词（出现这些词就要警觉） | 替代策略 |
|---|---|---|---|---|
| 1 | **AI 紫色调** | indigo→violet 渐变 + mesh gradient | `purple / violet / indigo / magenta`、"AI 网站"、"tech background"、"futuristic" | 强制单色 + 一个克制强调色（非紫） |

#### 🔬 紫色调根因（v2.0 补强，2025 多源报道坐实）

AI 默认使用 **Tailwind CSS**（原子化 CSS 无需单独文件），早期 Tailwind 默认背景色是 `bg-indigo-500`（蓝紫），导致训练数据被大量紫色界面污染，AI 形成「现代界面 = 紫色」的固化模式。

**信息源**：
- [AI 界面设计的「紫色魔咒」（AITNT）](https://m.aitntnews.com/newDetail.html?newId=17685)
- [AI 的「紫色问题」解密（火山引擎）](https://developer.volcengine.com/articles/7537170135619600426)
- [@dotey 推文](https://x.com/dotey/status/1953714406220554279)

**实操对策**：在 `tailwind.config` 中显式移除/重映射 `colors.indigo` 和 `colors.violet`，否则 AI 会反复掉回默认值。

> 完整陷阱清单（含触发词、替代策略、检查 grep）见 [`references/anti-ai-patterns.md`](./references/anti-ai-patterns.md)
| 2 | **文化主题老年味** | 水墨/书法/印章具象、复古 | `ink wash / calligraphy / vermilion / rice paper / seal / Eastern / oriental / vintage / traditional` | 留色彩不留形，主体换抽象几何 / 3D / typography |
| 3 | **Mesh gradient 滥用** | 多彩流动渐变背景 | `mesh gradient / cyberpunk / neon` | 改为单色 + 微噪点 + 单点强调 |
| 4 | **Mascot 拟人化** | Q 版吉祥物 / 拟人形象 | `mascot / character / friendly face / cute` | 改用抽象 3D 几何标识，研究实验室不用吉祥物 |
| 5 | **SaaS 模板感** | 千篇一律 hero + 3 卡 features + 价格表 | ChatGPT 默认输出 / v0 默认 | 加编辑设计语言、打破网格、用真实数据驱动布局 |

### 反陷阱检查清单（每份调研输出前过一遍）

```
□ grep 设计文档：是否有 purple/violet/indigo/magenta？
□ grep 设计文档：是否有 ink/calligraphy/vermilion/rice paper/seal 等文化具象词？
□ 是否有 mascot / 拟人形象？
□ 配色是否 ≤ 3 种主色 + 1 个强调色？
□ 留白是否 > 50%？
□ 是否有真实对标的网站（不只是抽象描述）？
□ 是否给了反例（这种风格会变成什么陷阱）？
```

### 反陷阱 / 设计批判（v2.0 补真实 URL）
- [AI 界面设计的「紫色魔咒」根因（AITNT）](https://m.aitntnews.com/newDetail.html?newId=17685)
- [AI 的「紫色问题」解密（火山引擎）](https://developer.volcengine.com/articles/7537170135619600426)
- [@dotey 推文（X，原始出处）](https://x.com/dotey/status/1953714406220554279)
- [还在 vibecoding 蓝紫色网页吗？DESIGN.md 解决方案（知乎）](https://zhuanlan.zhihu.com/p/2027384262219835165)
- [7 个神级技巧，彻底去除网站的 AI 味儿（程序员鱼皮）](https://www.cnblogs.com/yupi/p/19554255)
- [AI 生成的 UI 太丑？3 步秒变高级感（Skill Hub 中国）](https://www.skill-cn.com/practice/67)
- [4 个实战技巧让 AI 原型有「高级感」（CSDN）](https://blog.csdn.net/this_lol_egg/article/details/147970663)
- [怎么让 AI 写出好看有设计感的网页（53AI）](https://www.53ai.com/news/neirongchuangzuo/2025063095706.html)
- [热门 AI 技巧：高级感网页 UI（YouTube）](https://www.youtube.com/watch?v=0ex74hEqOa0)
- Awwwards / SiteInspire / Are.na（看真实高质量参考）

---

## 五、Phase 3：调研指令模板（**教用户怎么命令 AI**）

给用户的可复用指令模板——把这套教给用户，让 ta 未来能更好指挥任何 AI。

### 启动指令
```
"我想为 [项目类型] 设计前端，目标受众是 [受众]，
核心要展示 [数据/内容]，我已有 [后端产物]，
我喜欢 [审美方向]，不喜欢 [反例]。
请你先深度调研，再输出方案。"
```

### 深度调研指令
```
"去 GitHub / Awwwards / 小红书 / 抖音 / B站 / 知乎 深度调研 [方向]，
重点找 [高端/克制/编辑] 风格的真实案例"
```

```
"结合现有设计文档，去网络深度调研怎么把它做得 [高端/惊艳/不像 AI 生成]"
```

### 反陷阱指令
```
"我生成的图一股 [X] 味（如：国风老年味 / AI 紫色味 / SaaS 模板味），
请你深度调研为什么会这样，以及如何彻底避开"
```

### 完整性补充指令
```
"如果当前文档有未提及或不全面的地方，
请补充到可以直接开始执行的程度（同时去网络深度调研补充）"
```

### 后端验证指令（**重要**）
```
"先检查当前后端产物是否符合要求、是否全面、是否能正常接入前端，
列出缺口并给出补齐方案"
```

### 迭代修正指令
```
"针对 [具体反馈]，结合前端设计文档去网络深度调研该怎么改"
```

### 验收指令
```
"按设计文档逐项验收当前前端实现，列出未达标项"
```

### 每条指令的"AI 应该如何响应"规则
- **必须**先回应理解了用户意图
- **必须**做实际网络调研（不是凭记忆）
- **必须**多渠道交叉验证（GitHub + Awwwards + 社区平台至少 3 个来源）
- **必须**给真实可点击的链接，不要瞎编 URL
- **禁止**直接给"通用建议"，必须针对项目具体内容

---

## 六、Phase 4：三文档输出结构（**铁律**）

任何前端设计任务，最终必须输出**三个相互引用的文档**。不锁定内容，锁定结构。

### 文档 1：`{project}_design_research.md`（视觉设计）

**必含章节**：
1. Context（项目定位 + 受众 + 设计目标）
2. 视觉趋势（当年必看，列具体参考链接）
3. **必须避开的陷阱**（反 AI 设计味清单）
4. 配色方案（1 推荐 + 2 备选 + 混搭方案，每方向含 5 个角色色）
5. 字体方案（中英混排 + 标题/正文/数字/代码 4 层）
6. 页面结构（section 数 + 每 section 用途）
7. CSS 实现技巧（背景图叠加、可读性保障等）
8. 灵感来源（必含真实可点击链接）
9. 动效清单
10. 设计禁忌清单
11. TL;DR

### 文档 2：`{project}_image_prompts.md`（生图提示词）

**必含章节**：
1. 设计哲学（为什么这么写 prompt）
2. 工具推荐（Midjourney / DALL-E / Flux / Recraft 等的分工）
3. **必加关键词清单**（高端感来源）
4. **必加负面词清单**（`--no` 列表）
5. **按资产列出的精确 prompt**（每条含：尺寸、用途、主 prompt、2-3 个变体）
6. 资产清单表（编号 / 路径 / 尺寸 / 必要性 ⭐）
7. 调试方法论（`/describe` 反查、降 stylize、加 `--no`、sref 锁风格）
8. 验收 checklist（反陷阱 + 工程维度）
9. TL;DR

**资产至少覆盖**：Hero / Logo / OG / Favicon / 各 section 装饰 / 404 / Footer / 数据卡片背景

### 文档 3：`{project}_implementation_plan.md`（实施 plan）

**必含章节**：
1. Context（含**后端现状盘点**——哪些产物能直接用 / 哪些缺）
2. 技术栈选择（含理由）
3. API 设计（端点清单 + Pydantic / Zod schema）
4. 页面结构（section × 数据源 × 组件 映射表）
5. 核心组件设计（每个含接口 + 实现要点 + 库）
6. 文件结构树
7. 后端需要新增/导出的数据清单
8. 配色与字体配置代码（Tailwind config / CSS 变量）
9. 动效清单
10. 性能与可访问性目标
11. 部署方案
12. 开发阶段（Phase 0-N，每 phase 标工时 + 插件映射）
13. 验收 checklist（功能 / 视觉 / 工程 / 内容 4 维度）
14. TL;DR

### 三文档交叉引用规则
- design_research 引用 image_prompts 的"按资产 prompt"
- image_prompts 引用 design_research 的"配色方案"
- implementation_plan 同时引用前两者的具体决策（配色 hex、字体名、资产生成状态）

---

## 七、Phase 5：配色方法论

### 输出规则（**强制**）
- **每次给 1 推荐 + 2 备选**（不要 4 个让用户选困难）
- 每方向必含 5 个角色色：背景 / 主色 / 强调 / 高亮 / 文字
- 每方向必标"对标谁"——指向真实存在的高质量网站
- 必给"反例"：这种配色在什么情况下会变成陷阱
- 必给至少 1 个**混搭方案**：融合两个方向的优点

### 决策维度（不写答案，写怎么得到答案）

| 维度 | 决策方法 |
|---|---|
| 亮模式 vs 暗模式 | 看目标受众：学术/编辑偏亮，技术/产品偏暗 |
| 主色选择 | 不要用品牌色直接做主色，从受众审美倾向反推 |
| 强调色数量 | 全局只用 **1 种**强调色，多了就是 mesh gradient 陷阱 |
| 暖色 vs 冷色 | 暖色（米/橙/红）容易陷复古/文化主题；冷色（蓝/绿/灰）容易陷 SaaS——**根据用户反例决定** |
| 对标锚点 | 必须找 1-2 个真实网站，不能只描述抽象风格 |

### 反陷阱检查
```
□ 是否有 purple/violet/indigo？
□ 是否有 cream/beige/ivory + 文化主题词同时出现？
□ 强调色是否超过 1 种？
□ 是否有真实对标站点？
```

---

## 八、Phase 6：字体方法论

### 输出规则
- **中英混排必填**：中文 X 字体 + 英文 Y 字体的配对表
- 4 层字体分层：
  - 标题（display / serif / sans bold）
  - 正文（sans regular）
  - 数字（mono / display，hero 大数字单独配）
  - 代码（mono）
- 必标免费可商用来源（Google Fonts / 思源系列 / HarmonyOS 等）
- 必给"避免字体"清单（Comic Sans、Times New Roman、未授权商用字体等）

### 决策维度

| 维度 | 决策方法 |
|---|---|
| Serif vs Sans | 编辑/学术用 serif，技术/产品用 sans |
| 中文字体 | 默认思源系列或 HarmonyOS（免费可商用） |
| 大数字字体 | 用 mono 或 display（Space Grotesk / Fraunces 等）凸显技术感 |
| 字重 | hero 标题 700-900，正文 400-500，不要全用 bold |

---

## 九、Phase 7：页面结构方法论

### 输出规则
- **section 数不固定**——根据项目实际内容定（学术项目通常 7-12，产品落地页通常 5-7）
- 每 section 必填 4 项：**数据源 / 主要组件 / 库 / 动效**
- 必给"section × 数据源 × 组件"映射表
- 必画 ASCII 结构图（让用户一眼看懂布局）

### 布局选型矩阵

| 项目类型 | 推荐布局 | 理由 |
|---|---|---|
| 学术研究展示 | 编辑流式 + Bento Grid（数据集对比）| 突出数字 + 留白 |
| 数据 dashboard | Bento Grid + 多图表网格 | 信息密度 |
| 产品落地页 | Hero + 3-5 内容 section + Footer | 转化漏斗 |
| 个人作品集 | 大图 hero + 项目卡片网格 | 视觉冲击 |
| 交互 demo | Hero + 输入框 + 实时反馈 + 案例 | 操作流畅 |

### Section 顺序的叙事逻辑
- 起：Hero（一句话讲清这是什么）
- 承：概述 / 4 个核心数字
- 转：架构 / 方法 / 数据
- 合：结果 / 案例 / demo
- 尾：Footer / 链接 / 致谢

---

## 十、Phase 8：AI 生图方法论

### 工作流（**严格按此顺序**）
1. **资产清单化**：先列全部需要的图（hero/logo/OG/favicon/section 装饰/卡片背景/404/footer/credits）
2. **每资产填表**：尺寸 / 用途 / 主 prompt / 2-3 变体 / 负面词
3. **工具选型**：按资产特性选工具（见下表）
4. **批量生成**：每 prompt 跑 4 张选 1
5. **后处理**：裁切、调色、压缩为 WebP

### 工具选型矩阵

| 资产类型 | 推荐工具（国际） | 推荐工具（中文，v2.0 新增） | 理由 |
|---|---|---|---|
| Hero / 艺术背景 | Midjourney v6+ | **即梦 AI** / 豆包 | 艺术感 / 中文 prompt 友好 |
| 含文字图（OG / 海报） | DALL-E 3 | **通义万相** | 中文文字嵌入准 |
| Logo / icon | Recraft | 即梦矢量模式 | SVG 输出 |
| 写实素材 | Flux.1 | 通义万相 / 豆包 | 写实强 |
| 兜底免费方案 | Stable Diffusion XL + LoRA | 即梦（每日免费额度） | 可控 / 零成本 |
| 动态背景视频 | Runway / Sora | **可灵 AI** | hero 动效 |

> 中文 AI 生图工具详情（即梦 / 通义万相 / 可灵 / 豆包）见 [`references/ai-image-cn.md`](./references/ai-image-cn.md)。**国内项目优先用中文工具**，避免 prompt 翻译失真。

### 参数最佳实践
- `--style raw`：必加（关掉 MJ 默认装饰美学）
- `--stylize 80-180`：**不要超过 200**（过度美化）
- `--v 6+`：用最新版
- `--no` 列表：**长负面词列表常驻**
- `--ar`：严格按资产尺寸设

### 负面词清单模板（每 prompt 末尾加）
```
--no purple, violet, indigo, magenta,
       people, faces, mascot, character, realistic human,
       watermark, signature, logo, text artifacts,
       blurry, low quality, cartoon, anime style,
       [项目特定反陷阱词，如 oriental / ink / calligraphy]
```

### 调试方法论（**当用户说"生成的图一股 X 味"**）

| 症状 | 原因 | 解决 |
|---|---|---|
| 还是带文化元素 | `--no` 列表不够长 | 强化：加所有相关词 |
| 太花哨/堆砌 | `--stylize` 太高 | 降到 80-120 |
| 太单调 | `--stylize` 太低 | 升到 150-180 |
| 紫色残留 | prompt 含触发词 | grep 检查 prompt |
| 像照片 | `--style raw` 没加 | 必加 |
| 元素堆砌 | prompt 太长 | 砍到 60 词以内 |

**终极兜底**：让用户找一张 ta 满意的真实网站截图，用 `/describe` 反查得到 prompt，再改色值和尺寸直接用。

---

## 十一、Phase 9：实施 plan 方法论

### 技术栈决策树

```
需要 SEO / 多页面 / 复杂路由？
├─ 是 → Next.js (App Router) + TypeScript + Tailwind
└─ 否
   ├─ 纯静态展示？
   │  ├─ 是 → Astro + Tailwind（更轻）
   │  └─ 否 → Next.js（默认安全选择）
   └─ 极简一次性？
      └─ 单 HTML + Tailwind CDN
```

### 必含内容
- **后端现状盘点表**：每个后端产物 → 前端可用性 → 是否需要包装
- **后端缺口清单**：列出需要新增的 API / 数据导出
- **API schema**：Pydantic / Zod 类型定义 + 端点清单
- **Section × 数据源 × 组件** 映射表
- **核心组件设计**：每个组件含接口 + 库 + 实现要点
- **文件结构树**：`frontend/ + backend/ + scripts/` 三层
- **阶段计划**：Phase 0（设计敲定）→ Phase 1（API）→ Phase 2（骨架）→ Phase 3（核心 section）→ Phase 4（高级可视化）→ Phase 5（QA + 部署）
- **每阶段标工时 + 用什么插件产出什么**
- **验收 checklist**（4 维度：功能 / 视觉 / 工程 / 内容）

### 性能/可访问性目标（**必填**）
- Lighthouse Performance ≥ 85
- Accessibility ≥ 90
- 对比度 ≥ 4.5:1
- 支持 `prefers-reduced-motion`
- 移动端响应式（≥ 375px）

### 🤖 AI 建站工具协作（v2.0 新增，2025-2026 最大落地路径）

三文档完成后，**必须**输出一份「三文档 → AI 建站工具 prompt」让用户能直接喂给 v0/bolt/lovable。

#### 工具选型决策树
```
什么场景？
├─ 纯 UI 组件 / 设计稿探索 → v0.dev（首次提示易错，需多轮）
├─ 全栈 App → bolt.new（审美"性感但乱"，配 Cursor 精修）
├─ 快速 MVP / 结构化 → Lovable.dev
└─ 本地控制 / Cursor 配套 → bolt.diy
```

#### 协作工作流（三选一）
- **A：v0 探索 → 手写最终**（推荐学术/编辑类，避免 v0 审美残留）
- **B：bolt 一把梭 → Cursor 精修**（推荐产品/全栈）
- **C：Lovable 结构化 → 局部替换色值字体**（推荐落地页）

#### v0 多轮调教技巧（解决社区痛点：首次频繁错误）
1. 首轮给压缩 prompt（不要一次贴全部三文档）
2. 第二轮贴设计稿截图（v0 支持图片）
3. 第三轮针对错误：明确「不要紫色」「打破 3 卡网格」
4. 每轮加反陷阱关键词：`avoid SaaS template feel`

> 完整 prompt 模板（v0/bolt/lovable 三套压缩模板 + 多轮调教清单）见 [`references/ai-builder-prompts.md`](./references/ai-builder-prompts.md)

**信息源**：
- [V0 vs Bolt vs Lovable 对比（NxCode）](https://www.nxcode.io/zh/resources/news/v0-vs-bolt-vs-lovable-ai-app-builder-comparison-2025)
- [AI-Driven Prototyping（Addy Osmani）](https://addyo.substack.com/p/ai-driven-prototyping-v0-bolt-and)

---

## 十二、Phase 10：插件集成框架

### 扫描方法
启动前端任务后，**主动列出**当前可用的相关 skill / agent：

```
设计类: ecc:design-system, ecc:design-an-interface, frontend-design
模式类: ecc:frontend-patterns, ecc:nextjs-turbopack, ecc:vite-patterns
图表类: ecc:dashboard-builder
质量类: ecc:accessibility, ecc:webperf, ecc:seo, ecc:click-path-audit
手感类: ecc:make-interfaces-feel-better, ecc:liquid-glass-design
测试类: e2e-testing, browser-qa
```

### 按 Phase 映射法

每个 phase 标注"主要插件 + 辅助插件 + 产出"，例如：

```
Phase 0（设计敲定）:
  主要: ecc:design-an-interface, ecc:design-system
  辅助: ecc:frontend-design-direction, frontend-design
  产出: tokens.json + 设计方向决策

Phase 3（核心 section）:
  主要: frontend-design, ecc:dashboard-builder
  辅助: ecc:make-interfaces-feel-better, ecc:click-path-audit
  ...
```

### 不滥用插件的原则
- 不要每个动作都调插件（开销大）
- 同一类工作选 1 个主插件，不要叠加
- 用户没要求"用 ECC"时不要硬塞

---

## 十三、Phase 11：迭代方法论（**核心特色**）

用户反馈是金矿。基于反馈类型选择**精确**调整策略，不要笼统地"再调调"。

### 反馈分类响应表

| 用户反馈 | 真实问题 | 精确调整策略 |
|---|---|---|
| "一股 X 味"（X = 国风/AI/SaaS）| 触发了 MJ / AI 的训练分布陷阱 | (1) grep 检查 prompt 是否有触发词 (2) 强化 `--no` 列表 (3) 换关键词集合 (4) 用 `/describe` 反查 |
| "太丑 / 没感觉" | 整体方向不对 | 推倒重做 Phase 1-3，重新问受众和反例 |
| "不够高端 / 不够惊艳" | 留白不够 / 配色堆砌 / typography 没主导 | (1) 减少颜色数量 (2) 加大留白到 > 60% (3) 让 typography 主导 (4) 用真实数据驱动布局 |
| "太单调 / 没层次" | 缺少视觉层次 | 加几何 / 3D 雕塑 / 微动效 / 字重对比 |
| "不像 X 公司风格" | 对标错位 | (1) 让用户提供 X 公司截图 (2) 用 `/describe` 反查 (3) 提取色值和字体直接用 |
| "太花 / 太复杂" | 元素堆砌 | 砍资产数量 / 砍强调色 / 增加留白 |
| "前端没问题，但缺 X 功能" | 完整性不足 | 跑验收 checklist，列出未达标项 |
| "后端产物不够全" | 后端有缺口 | 列出后端缺口表 + 补齐方案 |

### 迭代节奏建议
- 每版输出后**必问用户反馈**（不要默认通过）
- 大改不超过 3 轮（否则方向就有问题）
- 小调（颜色微调、字号调整）可以无限轮
- 用户说"可以了"前**禁止**进入下一 phase

### 失败复盘模板
当用户对某版本非常不满时，**主动**问：
1. 具体哪里不喜欢？（颜色？布局？字体？某个元素？）
2. 有没有觉得不错的反例（ta 喜欢的网站）？
3. 是方向错了还是细节错了？

---

## 十四、Phase 12：用户指令模板库

整理一份"用户对 AI 说更好用"的指令模板库，**作为 skill 的输出之一交给用户**，让 ta 未来能更好指挥任何 AI。

### 分类

#### 启动指令（5 条）
1. 完整启动模板（含项目类型/受众/数据/审美/反例）
2. 简易启动模板（快速开始）
3. 仅生图任务启动
4. 仅实施 plan 任务启动
5. 已有设计稿，只需实施

#### 调研指令（5 条）
6. 多渠道深度调研（GitHub + Awwwards + 社区平台）
7. 反陷阱调研（"为什么 AI 生成会陷 X 味"）
8. 标杆站点调研（找真实高质量参考）
9. 趋势调研（当年必看）
10. 配色 / 字体专项调研

#### 修正指令（5 条）
11. "一股 X 味"修正
12. "不够高端"修正
13. "太单调"修正
14. 配色重选
15. 字体重选

#### 验收指令（3 条）
16. 三文档完整性检查
17. 反陷阱清单审计
18. 后端产物可消费性检查

#### 部署指令（2 条）
19. 部署前最终 QA
20. 部署后线上验证

### 模板示例（让用户填空）
```
"我想为 [项目类型] 设计前端。受众是 [受众]。
核心要展示 [内容列表]。后端已有 [产物]。
审美上我喜欢 [方向]，最不喜欢 [反例 + 截图]。
请你先按反陷阱清单检查我的需求，再深度调研，
最后输出三文档（设计研究 / 生图提示词 / 实施 plan）。
所有具体审美决策都要对标真实网站。"
```

---

## 十五、参考资源（让用户深入理解方法论）

### Skill 编写规范（本 skill 自身的元参考）
- [Claude Code Skills 官方文档](https://code.claude.com/docs/en/skills)
- [SKILL.md 格式参考（Agensi）](https://www.agensi.io/learn/skill-md-format-reference)
- [Deep Dive SKILL.md (Medium)](https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996)

### 反陷阱 / 设计批判
- 搜索 "The AI Purple Problem"
- 搜索 "web design trends 2026 do this instead"
- 搜索 "AI design cliché"
- Awwwards / SiteInspire / Are.na（看真实高质量参考）

### AI 生图调试
- Midjourney 官方文档（`--style raw`、`--stylize`、`--no`、`/describe`）
- 搜索 "Midjourney prompt engineering 2026"
- 搜索 "anti AI design aesthetic"

### 工作流捕获
- [How to Supercharge Your Design Workflow with AI (IxDF)](https://ixdf.org/literature/article/how-to-supercharge-your-design-workflow-with-ai)
- [How AI is Redistributing Creative Work (Adobe Research)](https://www.adobe.com/ai/research/202606/ai-is-redistributing-creative-work.html)

---

## 十六、TL;DR（一句话总结）

> **本 skill 是"前端设计任务的标准工作流"**：
> 1. 先问清项目类型 / 受众 / 反例（Phase 1）
> 2. 主动识别反陷阱（Phase 2）
> 3. 给用户调研指令模板（Phase 3）
> 4. 强制输出三文档（Phase 4：研究 + 生图 + 实施）
> 5. 用方法论而非审美决策填充文档（Phase 5-9）
> 6. 按阶段映射插件（Phase 10）
> 7. 基于用户反馈精确迭代（Phase 11）
> 8. 把指令模板库作为输出交给用户（Phase 12）
>
> **铁律**：教方法不教审美，所有具体决策必须由用户反例 + 真实对标驱动，不由 AI 默认填空。

---

## 十七、何时拒绝使用本 skill

以下情况应**主动停用**或转其他 skill：

- 用户说"不用调研，直接照我说的做"——转纯实施任务
- 用户给的设计稿已经很完整，只需写代码——转编码 skill
- 项目是纯后端 / CLI 工具，无前端需求——不该触发
- 时间预算 < 2 小时——本 skill 工作流太重，建议给简化方案
- 用户审美已经完全定死且明确——跳过 Phase 1-5，直接 Phase 9+

主动告诉用户："这个任务可能不需要完整的设计调研工作流，要不要直接 [简化方案]？"
