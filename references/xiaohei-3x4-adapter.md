# Ian Xiaohei 3:4 完整知识卡适配层

本文件把已安装的 `ian-xiaohei-illustrations/SKILL.md` 适配为小红书算法完整知识卡。它不是 Ian 原始 Skill 的替代品；每次生图前仍必须读取原始 `SKILL.md` 及其角色和 QA 参考。

## 原创小煤球角色硬约束

- 默认主角“小煤球”必须是 solid-black、蓬松不规则圆体，有短而自然的炭笔绒刺，不是人类身体比例。
- 小煤球必须有稳定的 white dot eyes（渲染为 two large off-white circular eyes）、细短腿，可按动作加入细手臂；表情好奇、专注或轻微困惑，不卖萌。
- No stick figure：禁止圆头火柴人、白色圆脸、头发、衣服、普通线稿小人、可爱吉祥物，也不要复刻现有影视角色的独特道具、镜头或情节。
- 小煤球必须执行核心算法动作，例如托住当前候选、把新元素送入候选位、记录概率或拉动状态转换；去掉小煤球后隐喻不应仍完整成立。

## 3:4 卡片适配

- Ian 原始规则中的 16:9 只改为 3:4 竖版；不要继承横版构图。
- 顶部 12%-16% 放模型直接渲染的标题，底部 25%-32% 放模型直接渲染的短公式、代码或结论；中部由一个小煤球主动作占据。
- 每张卡用一个怪诞但成立的算法隐喻，配 2-3 个真实物件和 2-4 个手绘文字教学模块；不要画课程课件、PPT 网格、UI 线框或无意义空卡片。
- 黑色用于小煤球和主要线稿；橙色仅用于主路径，红色仅用于警告/当前状态，蓝色仅用于补充状态。
- Do not copy Ian's example compositions、物件组合或标注；从当前算法的状态变化重新发明隐喻。

## 强制生图片段

把以下内容原样合并进每页最终成图提示词：

```text
Use the installed Ian Xiaohei visual language, adapted to a 3:4 Xiaohongshu card.
原创小煤球 is required: a small black fuzzy irregular soot-ball creature with short charcoal bristles,
two large off-white circular eyes, tiny thin legs, optional thin arms, and a curious focused expression.
小煤球 performs the core algorithm action. Render the supplied Chinese title, labels,
formula and short code exactly as provided in a hand-drawn but legible layout.
No stick figure, no outline-only human, no white round face, no hair, no cute mascot,
no PPT infographic, no placeholder cards, no overlapping or cropped text.
```

## 交付前拒绝

下列任一情况必须重生成底图：

- 角色不是 black fuzzy body 或没有 two off-white circular eyes。
- 角色退化为火柴人、白脸线稿人或普通涂鸦人物。
- 小煤球只是站在角落，没有承担算法状态变化。
- 画面像课程课件、正式流程图或复刻了 Ian 样例构图。
