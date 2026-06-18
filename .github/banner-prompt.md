# Banner 设计 Brief（Codex / GPT-Image-1 高级版）

> 完全为 AI 生图优化，可以复杂、可以精致、可以真实材质感。
> **硬性约束**：不出现任何 purple/violet/indigo/magenta/mesh gradient/cyberpunk/neon/mascot/cute 等元素。

---

## 设计方向

**主题**：Method over aesthetics（方法论 > 审美）

**风格定位**（多源参考）：
- Vercel / Linear / Stripe docs hero 的精致静态海报感
- 编辑设计（editorial design）的 typography-driven 美学
- 2026 年度配色：deep charcoal + warm terracotta（[2026 trend](https://www.pinterest.com/ideas/terracotta-and-deep-forest-green/) — 反紫色方向）
- Swiss / Brutalist 极简网格
- 完全静态平面，无 3D / glow / blur

**配色（严格）**：
- 主背景：`#0d1117` deep charcoal（或反相用 `#faf8f3` warm off-white）
- 主文字：`#ffffff` 纯白（深色背景）或 `#0a0a0a` 纯黑（浅色背景）
- **唯一强调色**：`#c2410c` warm terracotta（2026 年度色）
- 辅助灰阶：`#8b949e` / `#6e7681` / `#30363d`
- **绝对禁止**：任何 purple / violet / indigo / magenta / pink / mesh / cyber / neon 色

---

## 完整 Prompt（喂给 Codex / GPT-Image-1）

```
A high-end editorial-design hero banner for a GitHub repository, 1280 × 480 px, horizontal.

The banner is for "Frontend Design Research" — a methodology skill that teaches AI coding agents (Claude Code, Codex, Cursor) to avoid the five common "AI design tells" in generated frontends. The banner itself must embody anti-AI-tell editorial aesthetic.

=== COMPOSITION ===

Layout: editorial grid, 12-column. Left column (60%) = typography. Right column (40%) = abstract editorial composition. Thin vertical hairline between them.

=== LEFT COLUMN: TYPOGRAPHY ===

Top micro-label (14px monospace, terracotta #c2410c, uppercase, letter-spacing 2px):
  METHODOLOGY SKILL · ANTI-AI-TELL

Display heading (3 lines, 72px sans-serif Inter/Söhne/SF Pro Display, weight 700, letter-spacing -1.8px, pure white #ffffff):
  Frontend
  Design
  Research

Caption below (15px sans-serif, color #8b949e):
  前端设计调研方法论 — method, not aesthetic decisions.

Bottom of left column: a single 1px terracotta hairline, 80px wide, with a small terracotta dot (4px diameter) at its right end. Like an editorial pull-quote marker.

=== RIGHT COLUMN: ABSTRACT EDITORIAL COMPOSITION ===

A vertical editorial collage, NOT a list of color swatches, NOT a flowchart. Think of a single magazine spread page. Elements from top to bottom:

1. Top: a large terracotta #c2410c geometric form — a quarter circle (radius 80px) in the top-right corner, like a Japanese-engraved seal mark but rendered as pure abstract geometry. NO cultural references, NO actual seal/calligraphy, just the geometric form.

2. Middle: a stack of 5 thin horizontal rules (1px each, color #30363d), evenly spaced 8px apart, getting progressively shorter from top (200px) to bottom (80px) — like a descending data bar. To the right of each rule, a small monospace number in grey #6e7681: 01, 02, 03, 04, 05.

3. Below the stack: a large terracotta arrow (→) rendered as a thick geometric chevron (8px stroke, no feathered tip), pointing right. Color #c2410c.

4. After the arrow: a single solid terracotta square (40×40px), labeled below in 12px monospace: METHOD.

5. Bottom-right corner: 4 pill-shaped badges (no fill, 1px border #30363d, 12px sans-serif, color #c9d1d9), spaced 8px apart:
   "Claude Code"  "Codex"  "Cursor"  "more"

=== GLOBAL TREATMENT ===

- Subtle 2% opacity paper-grain noise texture overlay across entire canvas (for warmth, like Risograph print)
- One single 0.5px hairline horizontal rule below the typography column (color #30363d)
- Generous negative space — at least 55% of the canvas is empty
- Pure flat 2D, no shadows, no gradients, no 3D, no glow, no blur, no glassmorphism

=== AESTHETIC REQUIREMENTS (CRITICAL) ===

- Feels like a Vercel.com or Linear.app hero illustration, NOT a generic AI landing page
- Editorial magazine cover quality (think Apartamento, Cereal, Kinfolk magazine covers)
- Typography is the hero, decoration is restrained
- Single accent color (terracotta) used sparingly — only 3-4 instances in entire banner
- Brutalist/Swiss design discipline: every element earns its place

=== NEGATIVE PROMPT (CRITICAL) ===

--no purple, violet, indigo, magenta, pink, lavender, lilac, plum,
    mesh gradient, duotone gradient, cyberpunk, neon, glow, lens flare,
    ink wash, calligraphy, brush stroke, vermilion, cherry blossom,
    mascot, cartoon, character, cute face, friendly face, kawaii,
    3D render, isometric, glassmorphism, depth of field, bokeh, blur,
    SaaS template, hero with people, stock photo, dribbble aesthetic,
    watermark, signature, jpg artifacts, blurry, low quality,
    multicolor, rainbow, pastel
```

---

## 3 个色调变体（让 Codex 同时出，你选最对的）

### 变体 1（默认推荐）：Dark + Terracotta
```
Background #0d1117, text #ffffff, accent terracotta #c2410c.
```

### 变体 2：Warm Light + Terracotta
```
Background #faf8f3 (warm off-white), text #0a0a0a (pure black),
accent terracotta #c2410c. Paper-grain texture more visible.
Feels like a Risograph print magazine cover.
```

### 变体 3：Deep Forest + Cream
```
Background #0d2818 (deep forest green), text #faf8f3 (cream),
accent terracotta #c2410c. The 2026 transformative-teal-meets-terracotta palette.
```

---

## Codex 指挥 Prompt（推荐用法）

```
我在做一个开源项目 frontend-design-research-zh 的 GitHub README banner。
项目核心：教 AI 反「AI 设计味」的方法论 skill。

请按上面的 brief，一次生成 3 张 banner 候选（变体 1/2/3 各一张），每张 1280×480px。

输出要求：
- 严格遵守 negative prompt，任何一张出现 purple/violet/mesh/mascot 直接重做
- 每张配一段说明，写明色调变体 + 是否严格遵守了反陷阱清单
- 推荐其中一张作为最终 banner，并说明理由

硬性反陷阱要求（违反就重做，不要妥协）：
- 严禁任何紫色系（purple/violet/indigo/magenta/pink/lavender/lilac/plum）
- 严禁 mesh gradient / 多彩流动渐变
- 严禁 ink wash / calligraphy / 文化具象
- 严禁 mascot / 拟人卡通 / friendly face
- 严禁 SaaS template 感（hero+3 卡 pricing）
- 严禁 3D / glow / blur / glassmorphism
- 唯一允许的彩色是 terracotta #c2410c
```

---

## 关键设计决策（为什么这样）

| 决策 | 理由 |
|---|---|
| 不画 5 个色块 | 用户洞察：画紫色 = 把 AI 味再现，连灰度都不行 |
| 用 5 根递减 hairline + 编号 | 表达"5 tells"概念，但不出现具体色块 |
| 用 quarter circle 替代 logo 图形 | 抽象几何，无文化指向，编辑设计语言 |
| Terracotta 作为唯一彩色 | 2026 年度色，温暖 earth，绝对反紫 |
| Paper-grain noise 2% | 像杂志印刷品，增加质感不抢戏 |
| 大字 typography 当 hero | 编辑设计铁律：typography-driven |
| 4 个 pill 标签 | 突出多平台支持，Claude Code / Codex / Cursor / more |
| 55%+ 留白 | 反 mesh gradient 滥用陷阱 |

---

## 落地（图生成后）

```bash
cd '/Users/yb/Desktop/Name/工具/frontend-design-research-zh'

# 1. 把 Codex 生成的图存为 .github/banner.png（替换现有 .svg）
# 2. 改 README.md 和 README.en.md 第 3 行 .svg → .png
# 3. 提交 + push
git add .github/banner.png README.md README.en.md .github/banner-prompt.md
git rm .github/banner.svg
git commit -m "docs: banner 升级为 Codex 生成的编辑设计海报"
git push
```

---

## 参考视觉来源

- [2026 Terracotta trend](https://icolorpalette.com/terracotta-and-deep-forest-green/)
- [Vercel Blueprint Grid design](https://www.setproduct.com/blog/complete-guide-to-blueprint-grid-design)
- [Swiss design poster](https://elements.envato.com/learn/swiss-style-graphic-design)
- [Brutalist minimal color](https://www.kittl.com/blogs/brutalist-design-art-stl/)
- [Editorial design 哲学](https://taiarts.com/en/blog/what-is-editorial-design/)
