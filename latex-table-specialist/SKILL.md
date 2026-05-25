---
name: latex-table-specialist
description: Create beautiful, publication-ready LaTeX tables, and also rewrite, clean up, fit, or debug them. Use when the user asks to make, convert, fix, beautify, polish, optimize, resize, align, or debug a LaTeX table, including requests like LaTeX table, tabular, tabularx, longtable, threeparttable, siunitx, multirow, booktabs, tabularray, decimal alignment, merged headers, page-width fitting, multipage tables, or Chinese thesis three-line tables. Also use when the user asks in Chinese to zhizuo, xiugai, meihua, youhua, paiban, yasuo, duiqi, huo xiufu LaTeX biaoge, especially when they want tables that look professional, thesis-ready, or conference-paper ready.
---

# LaTeX Table Specialist

这个 skill 的默认目标不是“能编译就行”，而是“做出干净、克制、层次清楚、像论文里那样的漂亮表格”。

当前默认视觉来源只参考 `mmmeri/fancy-latex-tables`。除非用户之后明确改变要求，否则不要混入其他项目的表格语言。

## 先读哪里

按任务类型加载最少的参考内容：

- 想沿用 `mmmeri/fancy-latex-tables` 的样子：读 `references/mmmeri-fancy-latex-tables.md`
- 想直接挑一个可用样式：读 `references/preset-catalog.md`
- 只想知道整体排版原则：读 `references/overview.md`
- 表格太宽、太挤、层次不清：读 `references/layout-tuning.md`

## 默认行为

- 默认采用 `booktabs` 风格
- 默认优先使用 MMERI 这套家族的主版式和标题样式
- 默认不用竖线，除非用户明确要求或原文档已经统一使用竖线
- 默认让 caption 在表格上方，并可采用 MMERI 风格的小型大写标题气质
- 默认通过对齐、留白、分组表头和少量加粗来体现重点
- 默认优先美观与可读性，再考虑极限压缩

## 任务流程

1. 判断任务类型
   - 新建表格
   - 美化已有表格
   - 修复报错
   - 控宽或跨页
   - 增加表注、合并表头、数字对齐
2. 优先从 `references/preset-catalog.md` 里选一个主版式
   - `mmmeri-two-column`
   - `mmmeri-two-column-split`
   - `mmmeri-grouped-metrics`
   - `mmmeri-multirow-blocks`
3. 再按需要加细节模块
   - `small-caps-caption`
   - `tight-cmidrules`
   - `thin-header`
   - `unit-row`
   - `footnotesize-dense`
   - `block-multirow`
4. 选择环境
   - `tabular`: 简单短表
   - `tabularx`: 需要适配 `\linewidth`
   - `longtable`: 需要跨页
   - `threeparttable`: 需要表注
   - `tblr` / `longtblr`: 用户明确要现代语法，或项目本身已使用 `tabularray`
   - `table`: 需要浮动体、caption、label 时再包一层
5. 只引入真正需要的宏包
   - `booktabs`
   - `tabularx`
   - `multirow`
   - `siunitx`
   - `longtable`
   - `threeparttable`
   - `makecell` / `array`
   - `tabularray`
6. 保证输出可直接编译
   - 列数匹配
   - 特殊字符转义
   - 数值精度统一
   - 表头层次清楚

## 美化硬规则

- 不要默认使用 `|` 和 `\hline`
- 优先使用 `\toprule`、`\midrule`、`\bottomrule`
- 分组表头优先用 `\multicolumn` + `\cmidrule(lr){...}`
- 数字列优先右对齐；有小数时优先 `S` 列
- 最优值默认仅加粗，不默认上色
- 单位优先写在表头，不在单元格里重复
- 如果表格左右空隙过大，可在列格式两端用 `@{}` 收紧
- 只有在结构优化仍不够时才考虑缩字号
- 如果想接近 MMERI 的样子，优先用窄表头、多层表头、局部 `\cmidrule` 节奏，而不是堆更多线

## 输出要求

除非用户要求解释过程，否则默认输出：

- 必要宏包
- 完整 LaTeX 表格代码
- 如需改文件，则直接编辑文件
- 如有假设，只在结尾补一句

## 歧义处理

如果信息不完整，先做最小合理假设并继续完成。默认假设：

- 使用 `booktabs`
- 不使用竖线
- caption 在上方
- 最优值只做加粗
- 以 `\linewidth` 为宽度边界
- 若用户说“参考 fancy-latex-tables”，默认按 MMERI 家族主版式处理
