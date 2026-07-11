---
name: xiaohongshu-algorithm-visualizer
description: Use when creating Chinese Xiaohongshu algorithm explainers, data-structure tutorials, or interview-algorithm carousel cards, especially topics needing examples, correctness intuition, code, complexity, or probability reasoning.
---

# 小红书算法图解

将算法、数据结构或面试题做成 6–8 页中文小红书轮播。目标是可直接发布的 3:4 成品，而不是生图草稿。

## 必读规范

先读取：

- `references/visual-style.md`
- `references/xiaohongshu-layout.md`
- `references/attribution.md`
- `references/complete-knowledge-card.md`
- `references/xiaohongshu-copywriting.md`
- `references/visual-quality-gates.md`
- `references/render-pipeline.md`

保持白底、黑色手绘线稿、少量红蓝橙强调；角色必须参与核心动作。

## 默认交付

除非用户只要脚本、分镜或提示词，交付：

1. 最终标题和 2 个备选标题
2. 6–8 页独立 3:4 PNG
3. 可直接发布的正文和 5–10 个标签
4. 技术准确性检查报告
5. 与 PNG 同目录的 `xiaohongshu-copy.md`

所有最终 PNG 必须是精确的 1080 × 1440。

## 不可省略的成图流程

### 1. 先写页面语义合同

在生成任何图片前，为每页写：页面目的、唯一结论、精确技术文字、公式/代码、角色动作、样本语义和允许变量。

对容易混淆的变体必须显式锁定语义。例如蓄水池抽样：

- 单样本页标记 `sample_count = 1`，只能出现一个候选位、`1/i` 和最终 `1/n`。
- `k` 样本只能在专门扩展页出现，必须明确 `sample_count = k`、`k/i` 和随机替换一个池内位置。
- 不得把单样本的标题/公式叠在 k 样本的池、箭头、代码或证明上。

### 2. 生成“无文字视觉底图”，不要生成最终文字卡

每页仍必须调用 `image_gen`，但它的职责是生成独立的手绘视觉底图，不是渲染长中文、公式或代码。

提示词必须明确：

```text
3:4 vertical portrait, 1080 × 1440, white background,
black hand-drawn line art, limited red blue orange accents,
one dominant algorithm action with an active stick-figure character,
reserve a clean header zone and a clean lower teaching zone for later typesetting,
NO text, NO Chinese characters, NO letters, NO digits, NO equations,
NO code, NO UI labels, NO tables, NO placeholder cards, NO arrows through reserved zones.
```

底图可有留白，但留白必须是后续真实内容的安全区；不得要求模型生成空卡片或伪表格。不要使用一张含文字的成图再图生图修改下一页。

生成后先用 `view_image` 检查每张底图。只要出现残留文字、错误变量/样本数、无法解释状态变化的箭头、空框或构图侵入安全区，就重新生成该页底图；不要用半透明白框掩盖错误。

### 3. 确定性排版所有技术文字

在底图上用可控排版工具写入最终标题、中文、公式、表格和代码。成图必须扁平化为单张 PNG。

- 中文：使用可用的 CJK 字体和固定文本框；标题、正文、标签分层。
- 公式：使用原始公式字符串渲染为矢量或受控文本；不得让模型生成公式。
- 代码：只放 4–8 行核心实现，使用等宽字体、固定行高和独立代码区；不得依赖模型生成代码。
- 每个文字框、公式框、代码框只能落在预留安全区，四周至少留 80 px 安全边距。
- 不得覆盖主视觉的必要状态；不得把新的文字层压在错误旧文字上。

### 4. 双重验收后才交付

按 `references/render-pipeline.md` 和 `references/visual-quality-gates.md` 检查：

1. 逐字比对最终图的文字源与语义合同：变量、随机范围、索引、公式、复杂度和变体一致。
2. 检查文字/公式/代码的边界框无重叠、无截断，且箭头不穿过文字。
3. 在 100% 尺寸检查细节，并在手机缩略图检查阅读顺序。
4. 检查实际像素为 1080 × 1440；macOS 可用 `scripts/normalize_3x4.sh` 归一化后复检。

任一失败，修正排版或重新生成底图；不得带着残留错误交付。

## 默认分页

1. 封面：问题钩子
2. 场景：输入、限制、为什么普通方法不够
3. 核心规则
4. 小例子过程
5. 正确性：直觉证明、概率证明或不变量
6. 代码：核心实现
7. 扩展：变体、边界或 k 版本
8. 总结：复杂度和面试话术

压缩为 6 页时：封面、场景、规则、示例、代码、总结。不要为凑页添加无教学价值内容。

## 技术与发布检查

读取：

- `references/algorithm-template.md`
- `references/reservoir-sampling-example.md`（主题相关时）
- `references/qa-checklist.md`

验证定义、示例、索引、随机范围、公式、复杂度和变体边界。发布文案按 `references/xiaohongshu-copywriting.md` 写入 `xiaohongshu-copy.md`，其中记录标题、备选、正文、标签、页数、比例、生成信息和检查结果。

## 禁止

- 让生图模型直接生成长中文、长代码、公式或状态表，再把错误内容叠加遮住。
- 在同一页混用不同样本数、索引体系或算法变体。
- 用 k 样本视觉解释单样本规则，或反过来。
- 用半透明遮罩掩盖错误文字、错误符号或错误状态。
- 交付 16:9、非 1080 × 1440、文字重叠、截断、空框或错误箭头的图片。
