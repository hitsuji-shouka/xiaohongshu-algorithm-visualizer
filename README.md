# xiaohongshu-algorithm-visualizer

把算法、数据结构和算法面试题做成中文小红书图解轮播的 Codex Skill。

## 适合什么

适合把一个算法主题整理成 6-8 页小红书知识卡片，例如：

- 蓄水池抽样
- LRU
- 二分查找
- 滑动窗口
- 布隆过滤器
- 一致性哈希
- 动态规划

这个 Skill 的重点是：先讲问题，再讲核心规则、小例子、正确性、代码和面试总结。

## 默认输出

- 小红书标题选项
- 6-8 页轮播结构
- 每页文案与视觉分镜
- 每页生图提示词
- 小红书正文与标签
- 算法准确性检查清单

## 视觉风格

默认采用小红书技术教学风：

- 3:4 竖版
- 白底黑色手绘线稿
- 少量红蓝橙强调
- 角色参与核心算法动作
- 一页只讲一个认知点
- 长中文、公式、代码优先后期排版

视觉方法参考并署名 `helloianneo/ian-xiaohei-illustrations`，见 `NOTICE.md`。

## 安装

复制整个目录到 Codex 可发现的 skills 目录：

```bash
mkdir -p ~/.agents/skills
cp -R xiaohongshu-algorithm-visualizer ~/.agents/skills/
```

也可以放到项目级：

```text
.agents/skills/xiaohongshu-algorithm-visualizer/
```

## 示例

```text
$xiaohongshu-algorithm-visualizer
把“蓄水池抽样”做成 8 页小红书算法图解，面向校招面试。
```

## 目录结构

```text
xiaohongshu-algorithm-visualizer/
├── SKILL.md
├── README.md
├── LICENSE
├── NOTICE.md
└── references/
    ├── algorithm-template.md
    ├── reservoir-sampling-example.md
    ├── qa-checklist.md
    ├── visual-style.md
    ├── xiaohongshu-layout.md
    └── attribution.md
```
