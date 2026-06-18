# AI 建站工具协作模板（v0 / bolt / lovable）

> 主 skill Phase 4 输出的「三文档」（design_research + image_prompts + implementation_plan），
> 需要进一步压缩成 AI 建站工具能消费的 prompt。本文件提供模板。

---

## 一、工具选型决策树

```
什么场景？
├─ 纯 UI 组件 / 设计稿探索
│  └─ v0.dev（Vercel 出品，UI 组件专精）
├─ 全栈 App（前端 + 后端 + 数据库）
│  └─ bolt.new（StackBlitz 出品，全栈能力强）或 Lovable
├─ 快速 MVP / 结构化输出
│  └─ Lovable.dev
└─ 完全本地控制 / Cursor 配套
   └─ bolt.diy（bolt 开源版）
```

---

## 二、三文档 → v0.dev Prompt

### v0 痛点（社区反馈）
- **首次提示频繁错误**：需要多轮往返修正
- 组件库维护好但整体审美差（容易陷 AI 味）
- 适合：UI 组件、设计探索、原型

### v0 Prompt 压缩模板

```markdown
# 项目：{项目名}

## 设计方向（来自 design_research TL;DR）
- 风格：{极简沉稳 / 大胆锋芒 / 编辑学术 / 技术地下}
- 配色：主色 {hex} + 强调色 {hex} + 背景 {hex}（**禁止 indigo/violet/purple**）
- 字体：标题 {font} / 正文 {font} / 数字 {font}
- 对标网站：{真实 URL}

## 反陷阱（来自 anti-ai-patterns.md）
- 禁用：purple/violet/indigo/mesh gradient/mascot
- 风格关键词：editorial, monospace accents, asymmetric grid

## Tailwind 配置（关键）
请在 tailwind.config 中：
- 移除默认 indigo / violet
- 自定义 colors.{brand} = {hex}
- 字体加载 {font} via next/font

## 页面结构（来自 implementation_plan）
1. Hero：{一句话价值主张} + {CTA}
2. {section 名}：{数据源} × {组件}
3. {section 名}：...

## 我已有的产物
- API：{端点列表}
- 数据：{JSON 字段}
- 设计稿截图：{附件}

请按上述规范生成 React + Tailwind 代码。
```

### v0 多轮调教技巧（解决"首次频繁错误"痛点）
1. **首轮给压缩 prompt**（如上），不要一次性贴全部三文档
2. **第二轮贴设计稿截图**（v0 支持图片输入）
3. **第三轮针对错误**：明确说"不要紫色"、"打破 3 卡网格"
4. **每轮加 `--no` 风格关键词**："avoid SaaS template feel"

---

## 三、三文档 → bolt.new Prompt

### bolt 痛点
- 全栈能力强、UI 审美"性感但乱"
- 适合 Cursor 配套使用

### bolt Prompt 全栈模式（直接喂 implementation_plan 全文）

```markdown
# 项目：{项目名}

## 完整 implementation_plan（直接粘贴 Phase 9 输出）
{implementation_plan.md 全文}

## 设计约束（关键，避免 bolt 默认审美）
- 禁用 indigo/violet/purple（Tailwind 默认陷阱）
- 字体：{font}（不要默认 Inter）
- 对标：{真实 URL}

## 后端 API（如果 implementation_plan 中有定义）
- {端点列表}

请按 implementation_plan 生成完整 Next.js + TypeScript + Tailwind 项目。
```

### bolt + Cursor 配合模式
1. **bolt**：生成全栈骨架 + 基础功能
2. **Cursor**：精细调整审美 + 补充复杂逻辑

---

## 四、三文档 → Lovable Prompt

### Lovable 特点
- 结构化输出好
- 需要清晰、按 section 组织的 prompt

### Lovable Prompt 结构化模式（按 section 喂）

```markdown
# 项目：{项目名}

## 项目类型
{学术研究 / 产品功能 / 个人作品集 / 公司落地页}

## 设计系统（来自 design_research）
- 配色：主色 {hex} + 强调色 {hex}（仅 1 个强调色）
- 字体：{中英配对表}
- 反陷阱：禁用 purple/violet/indigo

## 页面 sections（按 implementation_plan）
### Section 1: Hero
- 用途：{价值主张}
- 数据源：{无 / 静态文案}
- 组件：{大标题 + CTA + 装饰图}

### Section 2: {名}
- 用途：...
- 数据源：{API 端点}
- 组件：...

## 技术栈
- {Next.js / Astro / Vite}
- {Tailwind / CSS Modules}

## 后端
- {API schema}

请生成完整可部署的项目。
```

---

## 五、协作工作流（推荐）

### 工作流 A：v0 探索 → 手写最终
1. 用 v0 探索 3-5 个设计方向（每方向喂压缩 prompt）
2. 选定一个方向，提取色值/字体/布局
3. 写到 design_research.md 和 implementation_plan.md
4. 手写最终代码（避免 v0 的 AI 味残留）

### 工作流 B：bolt 一把梭 → Cursor 精修
1. 用 bolt 喂完整 implementation_plan，生成全栈骨架
2. 用 Cursor 精修审美（重点修紫色、字体、网格）
3. 用 Cursor 补充复杂逻辑

### 工作流 C：Lovable 结构化 → 局部替换
1. 用 Lovable 按 section 生成结构化输出
2. 局部替换：把 AI 生成的色值/字体替换为 design_research 中的真实对标值
3. 验证反陷阱清单

---

## 六、参考资源

- [V0 vs Bolt.new vs Lovable：2026 AI 应用构建器对比（NxCode）](https://www.nxcode.io/zh/resources/news/v0-vs-bolt-vs-lovable-ai-app-builder-comparison-2025)
- [AI-Driven Prototyping: v0, Bolt, and Lovable Compared（Addy Osmani）](https://addyo.substack.com/p/ai-driven-prototyping-v0-bolt-and)
- [为什么 Vercel V0 的质量比 Lovable 和 Bolt 差（Reddit）](https://www.reddit.com/r/nextjs/comments/1huxty4/why_vercel_v0_quality_is_the_worst_compared_to/?tl=zh-hans)
- [AI 驱动的代码原型开发对比（知乎）](https://zhuanlan.zhihu.com/p/19533859140)
