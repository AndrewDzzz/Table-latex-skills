# MMERI Fancy LaTeX Tables Reference

这份参考专门提炼 `mmmeri/fancy-latex-tables` 的视觉语言和可复用模式。

仓库链接：<https://github.com/mmmeri/fancy-latex-tables>

## 1. 仓库本身在做什么

仓库 README 直接说它是 “some fancy table examples in latex”，并且说明这些例子是 “in the style of tabsatz”。这说明它不是一个通用论文模板，而是一组“有明确排版审美”的表格示例集合。

## 2. 这套风格的基础技术组件

`main.tex` 里最重要的基础件有这些：

- `tabularx`
- `booktabs`
- `multirow`

还定义了几类自定义列：

- `N`: `\scriptsize` 的普通表头列
- `V{...}`: 窄宽度、可换行、`\scriptsize` 的表头列
- `x`: `\scriptsize` 的 `X` 列
- `R{...}`: 旋转表头列

以及一个自定义 caption 命令：

- `\captiontable{...}`

这个 caption 命令会把表题做成更有设计感的样子：小型大写倾向、上方标题、居中收尾、标题下方留出一定空间。

## 3. 从仓库里能直接提炼出的 4 个主版式

### A. `mmmeri-two-column`

来自 `templates.tex` 的第一个例子。

特征：

- 双列
- 极简
- `\toprule` / `\bottomrule`
- 表头用 `N` 样式
- 每个表头下各有一段局部 `\cmidrule`

适合：

- 参数表
- 组件表
- 名词对照表

### B. `mmmeri-two-column-split`

来自 `templates.tex` 的第二个例子。

特征：

- 仍然是双列
- 但 `\cmidrule(lr)` 使用得更明显
- 比普通双列表更有“切分感”和节奏感

适合：

- 正式一点的小型参数表
- 想要简洁但不想太平的正文表

### C. `mmmeri-grouped-metrics`

来自 `templates.tex` 的第三个例子。

特征：

- `\footnotesize`
- 多层表头
- 多组 `\multicolumn`
- 多段 `\cmidrule(lr)`
- 单位单独成一行
- 窄宽度表头列 `V{...}`

适合：

- 实验结果表
- benchmark 比较表
- 多指标性能表

### D. `mmmeri-multirow-blocks`

来自 `templates.tex` 的第四个例子。

特征：

- `multirow`
- `multicolumn`
- 多层表头
- 块状信息组织
- 适合复杂结构

适合：

- 状态表
- 复杂实验配置表
- 每个 ID 下有多行子记录的表

## 4. 能从这个仓库稳定抽象出的“细节模块”

这些不是仓库里单独命名的 preset，而是从它的写法中可以稳定抽象出的模块。这里带有明确推断成分。

### `small-caps-caption`

依据：`main.tex` 中的 `\captiontable` 定义。

效果：

- caption 更像精修过的模板
- 比普通 `\caption{}` 更有版式气质

### `tight-cmidrules`

依据：仓库的多个例子都偏好局部 `\cmidrule`，而不是通栏 `\midrule` 解决所有问题。

效果：

- 层次更细
- 线更克制
- 更有“精致技术文档”的观感

### `thin-header`

依据：`N` 和 `V{...}` 这类窄表头列。

效果：

- 表头可以更窄
- 复杂表在有限宽度里更容易排进去
- 看起来更像工程/研究表而不是普通说明表

### `unit-row`

依据：第三、第四个例子都有明显的单位行。

效果：

- 单位表达更整齐
- 表头和数据职责更清楚

### `footnotesize-dense`

依据：第三、第四个例子都把复杂表切到 `\footnotesize`。

效果：

- 适合高密度技术表
- 看起来更像论文里的“严肃结果表”

### `block-multirow`

依据：第四个例子的 `multirow` 块状写法。

效果：

- 强化组块感
- 一个主键下面有多个状态或配置时更清晰

## 5. 这套风格最适合的论文场景

- 术语/参数说明表
- 实验指标表
- 复杂实验设计表
- 系统配置表
- 需要两层以上表头的技术表

## 6. 不要误用的场景

- 很花哨的彩色报告表
- 需要大量底色或品牌色的商务报告
- 主要靠图形化视觉而不是结构化表头取胜的表

## 7. 推荐用法

如果用户说“参考 fancy-latex-tables”，优先按这个顺序决策：

1. 先选 4 个主版式之一
2. 再补 1 到 3 个细节模块
3. 尽量保留 `booktabs` + 局部 `\cmidrule` + 紧凑表头的核心气质
4. 除非用户强烈要求，不要突然切回传统竖线网格表
