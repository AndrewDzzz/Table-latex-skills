# Preset Catalog

这份目录现在优先服务于 `mmmeri/fancy-latex-tables` 这一个风格家族。

最实用的选法不是盲选很多互不相关的表格，而是：

1. 先选一个主版式
2. 再加细节模块
3. 组合出你论文真正想要的样子

## 公共基础

如果要尽量接近 MMERI 仓库的风格，优先使用：

```latex
\usepackage{tabularx}
\usepackage{booktabs}
\usepackage{multirow}
```

如果要更接近仓库里的表头写法，可加入这些辅助列类型：

```latex
\newcolumntype{N}{>{\scriptsize}l}
\newcolumntype{V}[1]{>{\scriptsize\raggedright\hspace{0pt}}p{#1}}
\newcolumntype{x}{>{\scriptsize\raggedright\hspace{0pt}}X}
```

如果要更接近仓库里的 caption 气质，可使用：

```latex
\makeatletter
\newcommand{\captiontable}[2][\@empty]{
  \captionnamefont{\scshape\hfill}
  \captiondelim{\hfill}
  \captionstyle{\centerlastline\\}
  \setlength{\belowcaptionskip}{10pt}
  \ifx \@empty#1 \caption{#2}\else \caption[#1]{#2}\fi}
\makeatother
```

## 一、主版式

### 1. `mmmeri-two-column`

用途：

- 组件表
- 参数表
- 术语对照表

样子：

- 很简洁
- 两列对照
- 局部表头线

模板：

```latex
\begin{table}
  \captiontable{A nice 2-column table.}
  \centering
  \begin{tabular}{p{3cm} l}
    \toprule
    \multicolumn{1}{N}{Components} & \multicolumn{1}{N}{Names}\\
    \cmidrule(){1-1}\cmidrule(){2-2}
    Processor & Ultra company \\
    RAM & 1\,TB \\
    OS & Unix \\
    Graphics Card & Fancy \\
    \bottomrule
  \end{tabular}
\end{table}
```

### 2. `mmmeri-two-column-split`

用途：

- 更正式一点的小型表
- 参数和值的对照表

样子：

- 双列
- `\cmidrule(lr)` 更精致
- 比普通双列表更有节奏

模板：

```latex
\begin{table}
  \captiontable{Two-column splitted with indented separation lines.}
  \centering
  \begin{tabular}{p{3cm} l}
    \toprule
    \multicolumn{1}{N}{Parameters} & \multicolumn{1}{N}{Values}\\
    \cmidrule(lr){1-1}\cmidrule(lr){2-2}
    Processor & Ultra company \\
    RAM & 1\,TB \\
    OS & Unix \\
    Graphics Card & Fancy \\
    \bottomrule
  \end{tabular}
\end{table}
```

### 3. `mmmeri-grouped-metrics`

用途：

- benchmark 表
- 多指标结果表
- 单位行很重要的结果表

样子：

- 多层表头
- 分组强
- 紧凑
- 技术感很强

模板：

```latex
\begin{table}[!ht]
  \centering
  \footnotesize
  \captiontable{Table with multicolums of different categories.}
  \begin{tabular}{r r r r r r}
    \toprule
    \multicolumn{1}{V{2em}}{ID} & \multicolumn{2}{N}{Parameter permutations} & \multicolumn{3}{V{15em}}{Performance compared to older method} \\
    \cmidrule(lr){2-3}\cmidrule(lr){4-6}
    & \multicolumn{1}{V{5em}}{Parameter A} & \multicolumn{1}{V{5em}}{Parameter B} & \multicolumn{1}{N}{Duration} & \multicolumn{1}{N}{CPU load} & \multicolumn{1}{V{3.5em}}{Memory} \\
    & \multicolumn{1}{N}{[Hz]} & \multicolumn{1}{N}{[\%]} & \multicolumn{1}{N}{[s]} & \multicolumn{1}{N}{[\%]} & \multicolumn{1}{N}{[\%]} \\
    \cmidrule(lr){1-1}\cmidrule(lr){2-2}\cmidrule(lr){3-3}\cmidrule(lr){4-4}\cmidrule(lr){5-5}\cmidrule(lr){6-6}
    3 & 300 & 1.7 & 30 & 30 & 19 \\
    7 & 250 & 2.5 & 36 & 36 & 25 \\
    9 & 200 & 2.6 & 43 & 42 & 30 \\
    \bottomrule
  \end{tabular}
\end{table}
```

### 4. `mmmeri-multirow-blocks`

用途：

- 块状配置表
- 状态表
- 一个主 ID 下面带多个子状态的表

样子：

- 多层表头
- 块状多行结构
- 很复杂但很清楚

模板：

```latex
\begin{table}[!ht]
  \centering
  \footnotesize
  \captiontable{Table with multirows and multicolumns.}
  \begin{tabular}{r l r r r r r}
    \toprule
    \multicolumn{1}{V{1em}}{\#} &
    \multicolumn{1}{V{4.5em}}{State} &
    \multicolumn{4}{N}{Parameters} &
    \multicolumn{1}{V{3.5em}}{Measure} \\
    \cmidrule(lr){3-6}
    & & \multicolumn{1}{V{4.5em}}{Value} & \multicolumn{1}{V{4.5em}}{Wow} & \multicolumn{1}{V{4.5em}}{Awesome percentage} & \multicolumn{1}{V{4.5em}}{Factor} \\
    & & \multicolumn{1}{N}{[Hz]} & \multicolumn{1}{N}{[s]} & \multicolumn{1}{N}{[\%]} & & \multicolumn{1}{N}{$\cdot 10^{-3}$}\\
    \cmidrule(r){1-1}\cmidrule(lr){2-2}\cmidrule(lr){3-3}\cmidrule(lr){4-4}\cmidrule(lr){5-5}\cmidrule(lr){6-6}\cmidrule(l){7-7}
    \multirow{2}{*}{1} & State A & 5000 & 8 & 166 & \multirow{2}{*}{2.96} & \multirow{2}{*}{1.66}\\
    & State B & 10000 & 10 & 260 & & \\
    \cmidrule(r){1-1}\cmidrule(lr){2-2}\cmidrule(lr){3-3}\cmidrule(lr){4-4}\cmidrule(lr){5-5}\cmidrule(lr){6-6}\cmidrule(l){7-7}
    \multirow{2}{*}{2} & State A & 5000 & 8 & 166 & \multirow{2}{*}{2.83} & \multirow{2}{*}{0.60}\\
    & State B & 15000 & 10 & 365 & & \\
    \bottomrule
  \end{tabular}
\end{table}
```

## 二、细节模块

这些模块可以叠加到上面的任何主版式上。

### `small-caps-caption`

作用：

- 让 caption 更像 MMERI 仓库里的样子

建议：

- 论文正文想更精致时可加
- 整篇论文最好统一开或统一关

### `tight-cmidrules`

作用：

- 多用 `\cmidrule(lr)` 或局部 `\cmidrule(){...}`
- 少用整条通栏横线

效果：

- 更克制
- 更高级
- 更有节奏感

### `thin-header`

作用：

- 用 `N`、`V{...}` 这类窄列来做表头

效果：

- 表头更紧凑
- 宽度控制更好
- 复杂表更像技术论文里的成品

### `unit-row`

作用：

- 单位单独占一行

效果：

- 主表头和单位分层更清楚
- 尤其适合结果表

### `footnotesize-dense`

作用：

- 把复杂表切到 `\footnotesize`

效果：

- 更紧凑
- 更像论文里的技术大表

注意：

- 只有复杂结果表才建议默认开启
- 简单小表不必强行缩小

### `block-multirow`

作用：

- 使用 `\multirow` 把同组记录并成块

效果：

- 适合“一个编号下多个状态”
- 块状结构更明显

## 三、推荐组合

### 组合 1

- `mmmeri-two-column + small-caps-caption`

适合：

- 术语表、组件表、参数表

### 组合 2

- `mmmeri-two-column-split + tight-cmidrules`

适合：

- 正文里稍正式的小型对照表

### 组合 3

- `mmmeri-grouped-metrics + unit-row + footnotesize-dense`

适合：

- 主要实验结果表
- benchmark 表

### 组合 4

- `mmmeri-multirow-blocks + block-multirow + thin-header`

适合：

- 复杂实验设计表
- 分状态配置表

## 四、如果用户只说一句话

优先按下面规则理解：

- “参考 fancy-latex-tables 的双列表” -> `mmmeri-two-column`
- “参考 fancy-latex-tables 做个更精致的小表” -> `mmmeri-two-column-split`
- “参考 fancy-latex-tables 做实验结果表” -> `mmmeri-grouped-metrics + unit-row`
- “参考 fancy-latex-tables 做复杂结构表” -> `mmmeri-multirow-blocks`
