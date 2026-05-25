# Overview

这份参考是 LaTeX 漂亮表格的总览。目标是给出稳定、可复用、偏论文风格的默认规则。

## 视觉原则

- 用层次代替线条
- 用对齐代替装饰
- 用留白代替拥挤
- 用分组表头代替重复文字
- 用克制的强调代替大面积上色

## 默认技术路线

1. 从 `booktabs` 三线表开始
2. 如果是数值表，加 `siunitx`
3. 如果有长文本或宽度问题，加 `tabularx`
4. 如果需要表注，加 `threeparttable`
5. 如果跨页，用 `longtable`
6. 只有用户明确需要现代语法时，再考虑 `tabularray`

## 对齐规则

- 文本列：左对齐
- 编号、短标签：居中
- 普通数值列：右对齐
- 小数数值列：优先 `S` 列按小数点对齐
- 单位：尽量写在表头

## 结构规则

- caption 简短，不堆备注
- label 清晰，例如 `tab:main-results`
- 重点信息放左，比较指标放右
- 同类指标放在相邻列
- 有一级分组时用 `\multicolumn`
- 有局部分组线时用 `\cmidrule(lr){i-j}`

## 宽度处理顺序

1. 缩短表头文案
2. 让长文本列换行
3. 切到 `tabularx`
4. 把单位移入表头
5. 微调 `\tabcolsep`
6. 微调 `\arraystretch`
7. 必要时用 `\small`
8. 仍然过宽时，拆表、横向或跨页

## 默认微调范围

- `\setlength{\tabcolsep}{4.5pt}` 到 `6pt`
- `\renewcommand{\arraystretch}{1.05}` 到 `1.12`

## 不推荐的默认做法

- 默认全表加竖线
- 默认用 `\hline` 堆很多横线
- 默认缩到 `\scriptsize`
- 默认用底色和边框同时强调
- 把长备注硬塞进 caption
