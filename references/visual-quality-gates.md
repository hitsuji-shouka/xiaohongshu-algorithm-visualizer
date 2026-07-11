# 配图质量门槛

这份规范用于避免“看起来像排版草稿”的成图。信息丰富不等于堆满空框，手绘风也不等于允许文字重叠。

## 构图硬规则

- 每页只保留一个主视觉动作，配 2-3 个有内容的辅助模块。
- 页面最多 4 个边框模块；每个模块都必须有真实文字、图解或数据，禁止空卡片、占位横线、虚假表格和无意义虚线框。
- 标题区独立占顶部 12%-16%，标题、副标题和页码不能压到插图区或互相重叠。
- 主视觉、辅助模块和结论之间必须有明确层级；不要把页面做成九宫格或密集仪表盘。
- 留白只用于分隔内容，不得出现大块“准备放内容但没有内容”的空白。

## 生图提示词必须包含

```text
finished Xiaohongshu knowledge card, not a wireframe,
no empty boxes, no placeholder lines, no blank cards,
no overlapping text, no clipped title, no garbled labels,
one dominant scene plus 2-3 compact teaching callouts,
clear reading order, generous but purposeful whitespace
```

中文长句、公式、代码和命令优先用可控的后期排版；如果当前环境不能做后期排版，就减少图中文字并重新生成，不能交付有错字、重叠或占位线的图片。

## 生成后拒绝条件

出现以下任一情况，必须重新生成或重新排版：

- 标题压线、越界、重叠或被装饰遮挡。
- 出现空白卡片、灰色占位线、无意义的表格格子。
- 中文、公式、代码或命令乱码、重复或截断。
- 箭头没有明确起点和终点，或模块之间的关系不成立。
- 角色被挤到角落，或者主视觉无法解释算法状态变化。
- 页面一眼看不出阅读顺序。
