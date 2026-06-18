# 反 AI 味陷阱清单（独立可引用）

> 本文件是「前端设计调研方法论」主 skill 的 Phase 2 详细参考。
> 任何前端任务输出前，必须过一遍这个清单。

---

## 一、AI 紫色调（最普遍陷阱）

### 表现
indigo → violet 渐变 + mesh gradient + 蓝紫 hero

### 根因（关键，2025 多源报道坐实）

AI 默认使用 **Tailwind CSS**（原子化 CSS 无需单独文件），早期 Tailwind 默认背景色是 `bg-indigo-500`（蓝紫），导致：
1. **初始偏差**：大量网页使用 Tailwind 默认紫色配置
2. **数据污染**：这些紫色界面成为 AI 训练数据的重要组成部分
3. **模式固化**：AI 学会「现代界面 = 紫色」的常识

**来源**：
- [AI 界面设计的「紫色魔咒」（AITNT）](https://m.aitntnews.com/newDetail.html?newId=17685)
- [AI 的「紫色问题」解密（火山引擎）](https://developer.volcengine.com/articles/7537170135619600426)
- [AI 紫色问题（MoModel）](https://media.momodel.cn/article/ai%25E7%2595%258C%25E9%259D%25A2%25E8%25AE%25BE%25E8%25AE%25A1%25E7%259A%2584%25E7%25B4%25AB%25E8%2589%25B2%25E9%25AD%2594%25E5%2592%2592%25EF%25BC%259A%25E4%25B8%2580%25E6%259D%25A1%25E6%258E%25A8%25E6%2596%2587%25E6%258F%25AD%25E5%25BC%2580%25E7%259A%2584%25E6%258A%2580%25E6%259C%25AF%25E7%258E%25B0%25E8%25B1%25A1/9076/latest-articles)
- [@dotey 推文（X）](https://x.com/dotey/status/1953714406220554279)

### 触发词（出现就要警觉）
`purple / violet / indigo / magenta`、"AI 网站"、"tech background"、"futuristic"、`bg-indigo-*`、`bg-violet-*`

### 替代策略
- 强制单色 + 一个克制强调色（非紫）
- 显式覆盖 Tailwind 默认（在 tailwind.config 把 `colors.indigo` 移除或重映射）
- 用真实对标站点的色值（如 linear.app 深绿、vercel.com 黑白）

---

## 二、文化主题老年味

### 表现
水墨/书法/印章具象、复古中国风

### 触发词
`ink wash / calligraphy / vermilion / rice paper / seal / Eastern / oriental / vintage / traditional / 国风 / 水墨`

### 替代策略
**留色彩不留形**：用朱红/靛青/赭石等中式色但用现代抽象几何载体，主体换 typography / 3D 几何 / 编辑设计

---

## 三、Mesh gradient 滥用

### 表现
多彩流动渐变背景

### 触发词
`mesh gradient / cyberpunk / neon / 多巴胺配色`

### 替代策略
- 改为单色 + 微噪点 + 单点强调
- 用真实数据驱动的可视化代替装饰渐变

---

## 四、Mascot 拟人化

### 表现
Q 版吉祥物 / 拟人形象 / friendly face

### 触发词
`mascot / character / friendly face / cute / 吉祥物`

### 替代策略
- 研究实验室 / 高端产品**不用吉祥物**
- 改用抽象 3D 几何标识、typographic logo、动态字标

---

## 五、SaaS 模板感

### 表现
千篇一律 hero + 3 卡 features + 价格表

### 触发词
- ChatGPT 默认输出
- v0.dev 首次响应（社区痛点）
- Lovable/Bolt 默认模板

### 替代策略
- 加编辑设计语言（serif 大标题 + 长文版式）
- 打破网格（不对称、错位）
- 用真实数据驱动布局，而非通用占位

---

## 反陷阱检查清单（每份调研输出前过一遍）

```
□ grep 设计文档：是否有 purple/violet/indigo/magenta？
□ grep 设计文档：是否有 ink/calligraphy/vermilion/rice paper/seal 等文化具象词？
□ 是否有 mascot / 拟人形象？
□ 配色是否 ≤ 3 种主色 + 1 个强调色？
□ 留白是否 > 50%？
□ 是否有真实对标的网站（不只是抽象描述）？
□ 是否给了反例（这种风格会变成什么陷阱）？
□ Tailwind 配置中是否显式覆盖了 indigo/violet 默认值？
```

---

## 参考资料

- [还在 vibecoding 蓝紫色网页吗？DESIGN.md 解决方案（知乎）](https://zhuanlan.zhihu.com/p/2027384262219835165)
- [7 个神级技巧，彻底去除网站的 AI 味儿（程序员鱼皮）](https://www.cnblogs.com/yupi/p/19554255)
- [AI 生成的 UI 太丑？3 步秒变高级感（Skill Hub 中国）](https://www.skill-cn.com/practice/67)
- [4 个实战技巧，让 AI 产出的原型有「高级感」（CSDN）](https://blog.csdn.net/this_lol_egg/article/details/147970663)
