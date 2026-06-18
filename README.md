# 前端设计调研方法论 · Frontend Design Research Skill (zh-CN)

> 🇨🇳 一套**中文母语**的前端设计调研方法论 Claude Code Skill —— 教你**反 AI 味陷阱**、**三文档输出**、**v0/bolt/lovable 协作**、**中文 AI 生图生态**。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Made for Claude Code](https://img.shields.io/badge/Made%20for-Claude%20Code-blueviolet.svg)](https://claude.com/claude-code)
[![Language: zh-CN](https://img.shields.io/badge/Language-zh--CN-red.svg)](#)
[![Version](https://img.shields.io/badge/version-2.0.0-green.svg)](#)

**English abstract**: A Chinese-native Claude Code Skill that turns "design a frontend for my project" into a structured workflow — anti-AI-pattern awareness (purple/Tailwind indigo-500 cultural mascot/mesh gradient), three-document output (design research + AI image prompts + implementation plan), real-world AI builder collaboration templates (v0/bolt/lovable), and a curated CN AI image ecosystem (Jimeng/Tongyi Wanxiang/Kling/Doubao + Codex orchestrator). Teaches **method**, not aesthetic decisions.

---

## 🎯 解决什么问题

如果你用 AI（Claude / Cursor / v0 / Lovable / Bolt）做前端，大概率遇到过：

| 痛点 | 表现 | 本 Skill 的对策 |
|---|---|---|
| 🟣 **AI 紫色调** | hero 一片 indigo→violet 渐变 | 解释 Tailwind `indigo-500` 训练污染根因，给强制覆盖 `tailwind.config` 的对策 |
| 🎨 **文化主题老年味** | 水墨 / 书法 / 印章具象 | "留色彩不留形"，主体换抽象几何 |
| 🌀 **Mesh gradient 滥用** | 多彩流动渐变背景 | 改单色 + 微噪点 + 单点强调 |
| 🐶 **Mascot 拟人化** | Q 版吉祥物 / friendly face | 抽象 3D 几何 / typography |
| 📐 **SaaS 模板感** | 千篇一律 hero + 3 卡 features | 加编辑设计语言，打破网格 |
| 🤖 **v0/bolt/lovable 不知怎么喂** | 三文档输出后无法落地 | 提供 3 套工具的压缩 prompt 模板 + 多轮调教技巧 |
| 🇨🇳 **国际生图工具中文 prompt 失真** | 翻译掉语义 | 整合即梦/通义万相/可灵/豆包 + Codex 工程化 |

---

## ✨ 核心特色

### 1. 反陷阱意识（核心特色）
5 大 AI 设计陷阱 + 触发词清单 + 替代策略 + 根因解释。**每份调研输出前过一遍检查清单**。

### 2. 三文档输出铁律
任何前端任务必须输出三个相互引用的文档：
- `{project}_design_research.md` — 视觉设计研究
- `{project}_image_prompts.md` — AI 生图提示词
- `{project}_implementation_plan.md` — 实施 plan

### 3. AI 建站工具协作（2026 落地主路径）
- **v0.dev**：UI 组件专精，但首次提示易错 → 给多轮调教技巧
- **bolt.new**：全栈一把梭 → Cursor 精修审美
- **Lovable**：结构化输出 → 局部替换色值字体

### 4. 中文 AI 生图生态
即梦 / 通义万相 / 可灵 / 豆包 + **Codex 作为 prompt 工程指挥官**（让 Codex 批量写 prompt，调度其他工具出图）。

### 5. 反馈分类精确迭代
用户说"一股 X 味" / "太丑" / "不够高端" / "太单调" → 每类反馈对应**精确调整策略**，不笼统"再调调"。

### 6. Tier 0 快速路径
< 2 小时项目不走完整工作流，直接出简化版 `design.md`。

---

## 📦 安装

### 方式 1：Claude Code Marketplace（推荐）

```bash
/plugin marketplace add 0505ttt/frontend-design-research-zh
```

然后在 Claude Code 里：
```
/plugin install frontend-design-research-zh@frontend-design-research-zh
```

### 方式 2：手动 clone

```bash
git clone https://github.com/0505ttt/frontend-design-research-zh.git
cp -r frontend-design-research-zh ~/.claude/skills/前端设计调研方法论
```

重启 Claude Code，在 `/skills` 列表中应看到 **前端设计调研方法论**。

### 方式 3：单文件使用

只需要 `SKILL.md` 一个文件即可工作（references/ 是详细参考，按需引用）：
```bash
mkdir -p ~/.claude/skills/前端设计调研方法论
curl -o ~/.claude/skills/前端设计调研方法论/SKILL.md https://raw.githubusercontent.com/0505ttt/frontend-design-research-zh/main/SKILL.md
```

---

## 🚀 使用

### 触发方式
对 Claude 说以下任意一句：
- 「为我的项目设计前端 / 网页 / 展示页」
- 「做个 portfolio / landing page / dashboard」
- 「前端该用什么配色 / 字体 / 风格？」
- 「去网上深度调研怎么做这个前端」
- 「我生成的前端一股 AI 味，怎么改？」

### 完整工作流（12 个 Phase）

```
Phase 0  → 项目理解（必问清单：类型/受众/数据/审美/反例）
Phase 1  → 反陷阱意识（5 大陷阱 + 根因 + 检查清单）
Phase 2  → 调研指令模板（教用户怎么命令 AI）
Phase 3  → 三文档输出（design_research + image_prompts + implementation_plan）
Phase 4  → 配色方法论（1 推荐 + 2 备选 + 5 角色色 + 真实对标）
Phase 5  → 字体方法论（中英混排 + 4 层字体分层）
Phase 6  → 页面结构方法论（布局矩阵 + section 叙事）
Phase 7  → AI 生图方法论（资产清单 + 工具选型 + 调试表）
Phase 8  → 实施 plan（技术栈决策树 + 后端现状盘点 + 阶段计划）
Phase 9  → 插件集成框架（按 phase 映射 ecc/frontend-design 等）
Phase 10 → 反馈分类迭代（精确调整策略）
Phase 11 → 用户指令模板库（20 条可复用指令）
```

**Tier 0 快速路径**：< 2 小时项目直接走简化版（单文件 design.md）。

---

## 📁 项目结构

```
frontend-design-research-zh/
├── README.md                          ← 你正在看的介绍页
├── LICENSE                            ← MIT
├── SKILL.md                           ← 主 Skill 文件（17 章 / 643 行）
├── .claude-plugin/
│   └── plugin.json                    ← Claude Code plugin manifest
├── references/                        ← 详细参考（独立可引用）
│   ├── anti-ai-patterns.md            ← 反陷阱完整清单 + Tailwind 紫色根因
│   ├── ai-image-cn.md                 ← 中文 AI 生图生态（即梦/通义万相/可灵/豆包/Codex）
│   └── ai-builder-prompts.md          ← v0/bolt/lovable 喂养模板
└── examples/                          ← （占位）示例输出
```

---

## 🆚 与其他 Skill 的差异

| 维度 | 本 Skill | anthropics/skills/frontend-design | ecc:design-system |
|---|---|---|---|
| 语言 | 🇨🇳 中文母语 | 🇺🇸 英文 | 🇺🇸 英文 |
| 定位 | 方法论 / 教方法 | 执行 / 写代码 | 设计系统 / 落地 |
| 反 AI 味 | ✅ 核心（5 大陷阱 + 根因） | ❌ | ❌ |
| 中文 AI 工具 | ✅ 即梦/通义万相/可灵/豆包 | ❌ | ❌ |
| v0/bolt/lovable 协作 | ✅ 完整模板 | ❌ | ❌ |
| 三文档输出 | ✅ 铁律 | ⚠️ 单文件 | ⚠️ 设计 tokens |
| 反馈分类迭代 | ✅ 8 类精确策略 | ❌ | ❌ |

**适合人群**：
- ✅ 中文用户
- ✅ 对 AI 默认审美不满意
- ✅ 国内项目（需要中文 AI 工具）
- ✅ 想用 v0/bolt/lovable 但不知怎么调教

---

## 🔬 反 AI 紫色调的根因

> AI 默认使用 Tailwind CSS，早期 Tailwind 默认背景色 `bg-indigo-500`（蓝紫），导致训练数据被大量紫色界面污染，AI 形成「现代界面 = 紫色」的固化模式。
>
> —— 多源报道：[AITNT](https://m.aitntnews.com/newDetail.html?newId=17685) / [火山引擎](https://developer.volcengine.com/articles/7537170135619600426) / [@dotey](https://x.com/dotey/status/1953714406220554279)

**实操对策**：在 `tailwind.config` 中显式移除/重映射 `colors.indigo` 和 `colors.violet`，否则 AI 会反复掉回默认值。

---

## 🤖 Codex 工作流（作者主力）

```
1. 在 Codex 里贴 Prompt 模板 → 拿到 8 个资产的批量 prompt 表
2. 中文 prompt 复制到即梦（艺术背景）/ 通义万相（含文字）/ 可灵（视频）
3. 英文 prompt 复制到 MJ（艺术感更强时）
4. 出图后让 Codex 写后处理脚本：裁切 / 调色 / 压缩为 WebP / 生成 srcset
```

详见 [`references/ai-image-cn.md`](./references/ai-image-cn.md) 第 5 节。

---

## 📚 参考资料

本 Skill 整合自以下社区资源（全部真实可点击）：

**反 AI 味设计**
- [AI 界面设计的「紫色魔咒」（AITNT）](https://m.aitntnews.com/newDetail.html?newId=17685)
- [AI 的「紫色问题」解密（火山引擎）](https://developer.volcengine.com/articles/7537170135619600426)
- [还在 vibecoding 蓝紫色网页吗？DESIGN.md 解决方案（知乎）](https://zhuanlan.zhihu.com/p/2027384262219835165)
- [7 个神级技巧彻底去除网站的 AI 味儿（程序员鱼皮）](https://www.cnblogs.com/yupi/p/19554255)
- [AI 生成的 UI 太丑？3 步秒变高级感（Skill Hub 中国）](https://www.skill-cn.com/practice/67)

**AI 建站工具**
- [V0 vs Bolt vs Lovable 2026 对比（NxCode）](https://www.nxcode.io/zh/resources/news/v0-vs-bolt-vs-lovable-ai-app-builder-comparison-2025)
- [AI-Driven Prototyping（Addy Osmani）](https://addyo.substack.com/p/ai-driven-prototyping-v0-bolt-and)

**Skill 写作规范**
- [Claude Code Skills 官方文档](https://code.claude.com/docs/en/skills)
- [anthropics/skills 仓库](https://github.com/anthropics/skills)

---

## 🛠️ 可选：自动化反陷阱检查（hookify）

借助 Claude Code 的 hooks 系统，可以在 `~/.claude/settings.json` 的 `PostToolUse` 加一个反陷阱 grep hook，每次编辑设计文档时自动检测紫色词：

```json
{
  "matcher": "Edit|Write|MultiEdit",
  "hooks": [{
    "type": "command",
    "command": "/bin/sh -c 'INPUT=$(cat); FILE=$(echo \"$INPUT\" | python3 -c \"import json,sys;d=json.load(sys.stdin);print(d.get(\\\"tool_input\\\",{}).get(\\\"file_path\\\",\\\"\\\"))\" 2>/dev/null); case \"$FILE\" in *design*|*research*|*image_prompt*) if [ -f \"$FILE\" ] && grep -Eiq \"purple|violet|indigo|magenta\" \"$FILE\" 2>/dev/null; then echo \"⚠️ 反 AI 味警告：$FILE 检测到紫色词汇\" >&2; fi;; esac; exit 0'"
  }]
}
```

---

## ❓ FAQ

**Q: 这个 Skill 会替我做审美决策吗？**
A: 不会。**铁律是「教方法不教审美」** —— 所有具体配色/字体/风格决策都由你提供反例 + 真实对标驱动，AI 不替你填空。

**Q: 国际项目能用吗？**
A: 能。Skill 内含中英文工具对照，海外项目走 Midjourney + v0.dev + DALL-E 3 路径。

**Q: 不用 Claude Code 能用吗？**
A: SKILL.md 本质是结构化方法论，可以复制到 Cursor / Codex / ChatGPT 的 system prompt 或 custom instructions 里用。

**Q: 跟 ecc:design-system / anthropics frontend-design 冲突吗？**
A: 不冲突，互补。本 Skill 是**方法论层**（教怎么决策），那两个是**执行层**（写代码）。推荐组合：本 Skill 做 Phase 0-3 调研决策 → frontend-design 做 Phase 4+ 实施。

---

## 📈 版本历史

- **v2.0.0** (2026-06-18)：拆分 references 套件；新增 Codex 工作流；新增 v0/bolt/lovable 协作；补强紫色根因；加 hookify 自动检查
- **v1.0.0** (2026-05)：初版 17 章方法论

---

## 🤝 贡献

欢迎提 Issue / PR：
- 补充新的 AI 设计陷阱
- 分享你的反陷阱检查清单
- 添加其他语言版本（英文 / 日文）
- 提供新的中文 AI 生图工具评测

---

## 📄 License

[MIT](./LICENSE) — 自由使用、修改、分发。

---

## 🙏 致谢

- [anthropics/skills](https://github.com/anthropics/skills) — Skill 规范参考
- [obra/superpowers](https://github.com/obra/superpowers-marketplace) — Plugin marketplace 模式
- 中文社区所有分享 AI 设计反陷阱的博主和作者

---

**如果这个 Skill 帮到你**，欢迎 ⭐ Star / Fork / 推荐。
