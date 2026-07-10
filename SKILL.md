---
name: xiaohongshu-algorithm-visualizer
description: Use when creating Chinese Xiaohongshu algorithm explainers, data-structure tutorials, or interview-algorithm carousel cards, especially topics needing examples, correctness intuition, code, complexity, or probability reasoning.
---

# 小红书算法图解 Skill

将算法、数据结构或算法面试题转化为中文小红书图文轮播。默认 6-8 页，适合讲清楚问题、规则、例子、正确性、代码和面试总结。

## 先读共享规范

制作前读取：

- `references/visual-style.md`
- `references/xiaohongshu-layout.md`
- `references/attribution.md`

必须遵守：3:4 竖版、白底、黑色手绘线稿、少量红蓝橙强调、角色参与核心动作。

## 默认输出

除非用户另有要求，输出：

1. 3-5 个小红书标题
2. 6-8 页轮播结构表
3. 每页文案和视觉分镜
4. 每页生图提示词或生成图说明
5. 小红书正文
6. 标签
7. 技术准确性检查报告

## 默认结构

```text
1. 封面：问题钩子或反直觉点
2. 场景：输入、限制、为什么普通方法不够
3. 核心规则：一句话讲算法
4. 示例：小规模过程演示
5. 正确性：直觉证明、概率证明或不变量
6. 代码：核心实现
7. 扩展：变体、边界或 k 版本
8. 总结：复杂度和面试话术
```

需要更短时压缩为 6 页：封面、场景、规则、示例、代码、总结。

## 工作流程

1. 先判断算法解决什么问题，输入输出是什么，限制条件是什么。
2. 选择最小可讲清楚的示例，优先 4-6 个元素。
3. 提炼每页一个认知锚点。
4. 为每页设计角色动作，不做纯装饰图。
5. 把公式、代码和复杂文本列为“后期排版文字”。
6. 校验算法定义、边界条件、随机数范围、复杂度和证明。

## 必须读取的参考

- 通用算法轮播规则：`references/algorithm-template.md`
- 蓄水池抽样示例：`references/reservoir-sampling-example.md`
- 算法 QA：`references/qa-checklist.md`

## 技术检查

算法内容交付前必须检查：

- 定义是否准确
- 示例过程是否符合算法
- 代码索引和随机范围是否正确
- 数学公式是否正确
- 时间复杂度和空间复杂度是否正确
- 扩展版本是否没有偷换问题

## 禁止

- 为了凑够 8 页加入无教学价值内容。
- 把正确性证明画成看不懂的大公式墙。
- 让生图模型直接生成长代码。
- 把算法状态变化画错。
- 未经用户要求使用 16:9。
