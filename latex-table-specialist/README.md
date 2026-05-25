# LaTeX Table Specialist

这个 README 是给你挑“表格长相”用的。

现在只参考这个项目：

- [mmmeri/fancy-latex-tables](https://github.com/mmmeri/fancy-latex-tables)

所以现在最适合的理解方式不是“几十种互不相关的风格”，而是：

- 先选一个主版式
- 再加几个细节模块
- 最后得到你论文里想要的那种样子

这样会比乱选风格更统一，也更像真的论文系统。除非你后面明确改口，否则这套 skill 不再参考其他仓库。

---

## 1. 这套风格的共同气质

参考 `mmmeri/fancy-latex-tables` 后，这个 skill 现在默认会追求这些观感：

- 三线表为主
- caption 在上方
- 局部 `\cmidrule` 很讲究
- 表头通常比较紧凑，甚至会做成窄列换行
- 复杂表会用两层或三层表头
- 数值表常会切到 `\footnotesize`，让密度更高
- 整体是“精致、技术感、排版感强”，不是传统大网格表

---

## 2. 先选一个主版式

现在先从 4 个主版式里挑。它们都直接来自或紧贴 `mmmeri/fancy-latex-tables` 里的例子。

| 主版式 | 长相感觉 | 适合放在哪 | 你可以怎么说 |
| --- | --- | --- | --- |
| `mmmeri-two-column` | 干净的双列表，很简洁 | 术语表、配置表、变量名对照表 | “用 MMERI 双列表” |
| `mmmeri-two-column-split` | 双列表，但标题下分隔线更讲究 | 更正式一点的参数表 | “用带缩进分隔线的 MMERI 双列表” |
| `mmmeri-grouped-metrics` | 多层表头、分组很强 | 实验结果表、指标比较表 | “用 MMERI 分组指标表” |
| `mmmeri-multirow-blocks` | 多行块状结构、信息密度高 | 状态表、配置块、复杂实验设计表 | “用 MMERI 多行块状表” |

---

## 3. 这 4 种主版式分别长啥样

### `mmmeri-two-column`

感觉：

- 最简洁
- 两列信息对照很清楚
- 有点像高质量术语表或组件表

大概长这样：

```text
---------------------------------
Components              Names
---------------------------------
Processor               Ultra company
RAM                     1 TB
OS                      Unix
Graphics Card           Fancy
---------------------------------
```

适合：

- 组件列表
- 参数说明
- 名称对照
- 小型正文表

---

### `mmmeri-two-column-split`

感觉：

- 跟上面差不多
- 但表头下方的 `\cmidrule(lr)` 更有“设计感”
- 比普通双列表更像精修过的论文表

大概长这样：

```text
---------------------------------
Parameters              Values
  ---------              ------
Processor               Ultra company
RAM                     1 TB
OS                      Unix
Graphics Card           Fancy
---------------------------------
```

适合：

- 想要简洁但不想太素
- 参数表
- 论文里比较正式的小表

---

### `mmmeri-grouped-metrics`

感觉：

- 这就是“论文感”最强的一类
- 多层表头
- 指标分组明确
- 常见于实验结果和性能比较

大概长这样：

```text
-------------------------------------------------------------
ID   Parameter permutations    Performance compared to older method
     ----------------------    -----------------------------------
     Parameter A  Parameter B  Duration   CPU load   Memory
     [Hz]         [%]          [s]        [%]        [%]
-------------------------------------------------------------
3    300          1.7          30         30         19
7    250          2.5          36         36         25
9    200          2.6          43         42         30
-------------------------------------------------------------
```

适合：

- benchmark 表
- 多指标比较表
- 有单位行的结果表
- 论文主结果表

---

### `mmmeri-multirow-blocks`

感觉：

- 最复杂
- 表里有块状结构
- 同一个 ID 或状态会跨多行
- 信息量大，但层次也最强

大概长这样：

```text
-----------------------------------------------------------------
#   State      Parameters                               Measure
               ------------------------------------
               Value   Wow   Awesome percentage   Factor
               [Hz]    [s]         [%]            x10^-3
-----------------------------------------------------------------
1   State A    5000     8          166             2.96   1.66
    State B   10000    10          260
-----------------------------------------------------------------
2   State A    5000     8          166             2.83   0.60
    State B   15000    10          365
-----------------------------------------------------------------
```

适合：

- 复杂实验设计
- 分状态、分阶段、分配置的表
- 需要 `multirow` 的表

---

## 4. 再加“细节模块”改变长相

你可以把这些理解成“同一主版式上的装饰开关”。

| 模块名 | 作用 | 视觉效果 | 常见搭配 |
| --- | --- | --- | --- |
| `small-caps-caption` | 标题更像 repo 里的样子 | caption 更精致、更像论文模板 | 全部都可加 |
| `tight-cmidrules` | 用局部短横线而不是通栏横线 | 更克制、更高级 | `mmmeri-two-column-split`、`mmmeri-grouped-metrics` |
| `thin-header` | 表头变窄、允许换行 | 更像 repo 的紧凑表头 | `mmmeri-grouped-metrics` |
| `unit-row` | 单独放一行单位 | 指标更规整 | `mmmeri-grouped-metrics` |
| `footnotesize-dense` | 整张表更紧凑 | 技术感更强、密度更高 | `mmmeri-grouped-metrics`、`mmmeri-multirow-blocks` |
| `block-multirow` | 同一组记录跨多行 | 块状结构更明显 | `mmmeri-multirow-blocks` |

---

## 5. 真正能选出来的“样子”示例

所以你不是只能说一种风格，而是可以这样组合：

1. `mmmeri-two-column`
2. `mmmeri-two-column-split + small-caps-caption`
3. `mmmeri-grouped-metrics + unit-row`
4. `mmmeri-grouped-metrics + unit-row + footnotesize-dense`
5. `mmmeri-multirow-blocks + block-multirow + thin-header`

这几种放到论文里，看起来就已经是明显不同的“表格样貌”了。

---

## 6. 你后面可以直接这样对我说

### 只指定主版式

- “这张表用 `mmmeri-two-column`”
- “这个结果表用 `mmmeri-grouped-metrics`”
- “这个复杂设计表用 `mmmeri-multirow-blocks`”

### 指定主版式加细节

- “这张表用 `mmmeri-two-column-split`，caption 做精致一点”
- “这个结果表用 `mmmeri-grouped-metrics`，带单位行，紧凑一点”
- “这张表用 `mmmeri-multirow-blocks`，要块状结构明显一点”

### 用自然语言说

- “做成 fancy-latex-tables 那个双列表” 
- “做成 fancy-latex-tables 那种多层指标表”
- “做成 fancy-latex-tables 那种复杂 multirow 表”

---

## 7. 如果你写的是毕业论文，我推荐这样配

1. 名词、参数、组件说明：`mmmeri-two-column`
2. 稍正式的小表：`mmmeri-two-column-split`
3. 主要实验结果：`mmmeri-grouped-metrics + unit-row`
4. 很复杂的结构表：`mmmeri-multirow-blocks + footnotesize-dense`

这样整篇论文会统一，而且会明显有“这是一个系统设计过的表格语言”的感觉。

---

## 8. 现在最实用的一句话

如果你懒得选，你以后可以直接说：

- “按 `mmmeri/fancy-latex-tables` 的风格给我做这张表。”

我就会默认从这 4 个主版式里挑最合适的一个，再补必要的细节模块。
