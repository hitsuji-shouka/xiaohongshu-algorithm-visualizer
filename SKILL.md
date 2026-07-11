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
- `references/xiaohei-3x4-adapter.md`

保持白底、黑色手绘线稿、少量红蓝橙强调；原创“小煤球”主角必须参与核心动作。

## 强制 Xiaohei 视觉依赖

生成任何算法卡前，必须读取已安装的 Ian 原始 Skill：

```text
${CODEX_HOME:-$HOME/.codex}/skills/ian-xiaohei-illustrations/SKILL.md
```

并读取该 Skill 的 `references/style-dna.md`、`references/xiaohei-ip.md`、`references/prompt-template.md`、`references/qa-checklist.md`，再读取本 Skill 的 `references/xiaohei-3x4-adapter.md`。

Ian 原始 Skill 的默认画布是 16:9 正文配图；本 Skill 只能按适配层将它转换为 3:4 小红书完整知识卡。No generic fallback：找不到 Ian Skill 或未完成上述阅读时，不得改用通用手绘人物生成并假装符合风格。

No stick figure：默认主角是原创“小煤球”--黑色蓬松不规则圆体、短而自然的炭笔绒刺、两只偏白的大圆眼睛、细短腿和可选细手臂，表情好奇但不卖萌。它借鉴 Ian 的“角色参与技术动作”方法，不复制任何现有影视角色的具体造型、道具或镜头。禁止圆头火柴人、白脸线稿人、头发或普通涂鸦人。

## 默认交付

除非用户只要脚本、分镜或提示词，交付：

1. 最终标题和 2 个备选标题
2. 6–8 页独立 3:4 PNG
3. 可直接发布的正文和 5–10 个标签
4. 技术准确性检查报告
5. 与 PNG 同目录的 `xiaohongshu-copy.md`

所有最终 PNG 必须是精确的 1080 × 1440。

## 直接成品交付

除非用户明确只要脚本、分镜或提示词，必须调用 `image_gen` 直接生成每页含中文文字、公式、代码和手绘场景的完整知识卡，并交付最终 PNG、简洁正文和 5-10 个精准标签。

不得只输出分镜或提示词；不得只交付无文字底图。只有 `image_gen` 不可用时，才说明原因并输出完整降级提示词。

## 完整知识卡成品约束

最终交付必须是完整知识卡，信息密度保持中到高：每页包含一个主结论、小煤球主动作和 3–5 个辅助教学模块。内容要紧凑地填满约 60%–75% 的画面，但必须保持清晰的标题—过程—结论阅读层级；不要把多页的不同算法语义硬塞进一页。

不得只生成纯插画底图。默认由 `gpt-image-2` 直接完成标题、中文解说、公式、代码和结论的手绘知识卡排版，并导出单张最终成品图；只提供 overlay 文案建议不算完成。

## 严格 3:4 成品检查

3:4 是硬性发布规格，不是提示词里的软性建议：

1. 每页最终成图提示词必须明确写 `3:4 vertical portrait` 和 `1080 × 1440`。
2. `image_gen` 返回后必须检查实际像素尺寸，不得只相信提示词或文件名。
3. 最终图必须精确为 `1080 × 1440`；不得交付 `2:3`、16:9、正方形或多页拼图作为单张轮播。
4. 在 macOS 上使用 `scripts/normalize_3x4.sh` 补白或裁切后再复检。

## 不可省略的成图流程

### 1. 先写页面语义合同

在生成任何图片前，为每页写：页面目的、唯一结论、精确技术文字、公式/代码、角色动作、样本语义和允许变量。

对容易混淆的变体必须显式锁定语义。例如蓄水池抽样：

- 单样本页标记 `sample_count = 1`，只能出现一个候选位、`1/i` 和最终 `1/n`。
- `k` 样本只能在专门扩展页出现，必须明确 `sample_count = k`、`k/i` 和随机替换一个池内位置。
- 不得把单样本的标题/公式叠在 k 样本的池、箭头、代码或证明上。

### 2. 直接生成完整知识卡

每页必须调用 `image_gen` 生成完整的、可直接发布的知识卡。`gpt-image-2` 负责所有页面内的中文标题、短解说、公式、代码、页码和手绘图解；不要默认把文字拆给后期排版。

先按“强制 Xiaohei 视觉依赖”读取 Ian 原始 Skill 和 3:4 适配层。只吸收其风格 DNA、角色动作和原创隐喻方法；不要复制 Ian 的样例图片、物件组合或已有构图。

提示词必须明确提供本页的全部精确文本，并要求模型逐字呈现。每页文本控制在可读范围：标题 8–18 字、正文 80–150 个汉字、公式最多 1 条、代码最多 6 行、短标签每条不超过 8 字。

提示词必须包含：

```text
3:4 vertical portrait, 1080 × 1440, white background,
an original Ian Xiaohei visual language adapted for a Xiaohongshu knowledge card:
black hand-drawn line art, slight natural wobble, limited red blue orange accents,
one dominant algorithm action with 原创小煤球 as the active subject:
a small black fuzzy irregular soot-ball creature with short hand-drawn charcoal bristles,
two large off-white circular eyes, tiny thin legs, optional thin arms, curious focused expression,
No stick figure, no outline-only human, no round white face, no hair, no mascot styling,
render every supplied Chinese string, formula, code line and page number accurately,
make a medium-high density, immediately scannable complete hand-drawn knowledge card,
show title, illustration, explanation and conclusion in one coherent composition,
no empty boxes, no placeholder lines, no overlapping text, no cropped text.
```

不要让模型自行改写技术文字、补充变量、发明命令或混用算法变体。不要使用一张含文字的成图再图生图修改下一页。

生成后先用 `view_image` 检查每张完整卡。只要出现错字、乱码、漏字、错误变量/样本数、错误公式/代码、无法解释状态变化的箭头、空框、火柴人、白脸线稿人、文字重叠、文字裁切或非 3:4 构图，就重生成整页；不要用半透明白框覆盖错误。

### 3. 只在模型文字失败时进行受控修正

默认不再进行“底图 + 后期排版”。只有用户明确要求修正某一张已生成卡的个别错字，或连续重生仍无法得到正确文字时，才允许以受控排版作局部修正。

局部修正时：保留原有构图、只替换错误文字、不得把整张卡改成排版海报、不得覆盖主视觉或用大面积白色遮罩抹去模型错误。

### 4. 双重验收后才交付

按 `references/render-pipeline.md` 和 `references/visual-quality-gates.md` 检查：

1. 逐字比对最终图的模型文字与语义合同：变量、随机范围、索引、公式、复杂度和变体一致。
2. 检查文字/公式/代码无重叠、无截断、无错字，且箭头不穿过文字。
3. 在 100% 尺寸检查细节，并在手机缩略图检查阅读顺序。
4. 检查实际像素为 1080 × 1440；macOS 可用 `scripts/normalize_3x4.sh` 归一化后复检。
5. 检查原创小煤球是否承担算法动作、是否保持黑色蓬松圆体与偏白大圆眼睛、是否没有退化为 PPT 图或火柴人。

任一失败，优先重生成整页；不得带着残留错误交付。

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

## 发布文案

读取 `references/xiaohongshu-copywriting.md`，并交付：

```text
标题：1 个最终标题，另附 2 个备选标题
简介：3-6 个短段，使用 4-8 个有语义的 emoji，至少 3 个分点
标签：5-10 个精准标签
```

`xiaohongshu-copy.md` 与 PNG 同目录保存，不能只在聊天中展示。

## 禁止

- 因为担心中文而默认把所有文字从生图模型中剥离，交付空洞的底图或排版海报。
- 让生图模型自作主张改写用户提供的精确文字、公式、代码或状态表。
- 在同一页混用不同样本数、索引体系或算法变体。
- 用 k 样本视觉解释单样本规则，或反过来。
- 用半透明遮罩掩盖错误文字、错误符号或错误状态。
- 交付 16:9、非 1080 × 1440、文字重叠、截断、空框或错误箭头的图片。
