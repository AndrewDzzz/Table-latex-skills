# Table LaTeX Skills

A focused Codex skill repository for creating better-looking LaTeX tables.

This repository currently contains one main skill:

- `latex-table-specialist/`

The goal is simple: help Codex produce LaTeX tables that look like deliberate paper tables rather than default `tabular` output.

## Reference style

This repository intentionally follows a single visual reference family:

- [`mmmeri/fancy-latex-tables`](https://github.com/mmmeri/fancy-latex-tables)

Instead of mixing many unrelated table aesthetics, this skill stays close to one coherent design language.

Reference image from the source project:

![Reference table examples](https://github.com/mmmeri/fancy-latex-tables/raw/master/fancy-latex-tables-ex.PNG)

## What the skill does

`latex-table-specialist` helps Codex:

- create LaTeX tables from plain text, structured notes, or data summaries
- restyle weak or ugly tables into cleaner paper-ready tables
- build grouped headers and multirow technical tables
- keep table choices visually consistent across a thesis or paper
- tune spacing, density, and structure without immediately shrinking everything

## Core design preferences

Because the repository is based on `mmmeri/fancy-latex-tables`, the skill prefers:

- `booktabs`-style rules
- compact and structured headers
- local `\cmidrule` rhythm instead of heavy full-grid borders
- grouped technical tables with strong hierarchy
- dense but readable layouts for result tables

## Repository layout

```text
Table-latex-skills/
├── README.md
└── latex-table-specialist/
    ├── README.md
    ├── SKILL.md
    └── references/
        ├── layout-tuning.md
        ├── mmmeri-fancy-latex-tables.md
        ├── overview.md
        └── preset-catalog.md
```

## Main table families

The current skill is organized around four MMERI-style table families:

1. `mmmeri-two-column`
2. `mmmeri-two-column-split`
3. `mmmeri-grouped-metrics`
4. `mmmeri-multirow-blocks`

These cover most practical paper-table needs:

- small parameter tables
- cleaned-up two-column explanation tables
- benchmark and result tables
- complex grouped multirow technical tables

## Detail modules

The skill also supports small visual modules that can be layered onto a main table family:

- `small-caps-caption`
- `tight-cmidrules`
- `thin-header`
- `unit-row`
- `footnotesize-dense`
- `block-multirow`

This makes it easy to request a table in natural language without inventing a brand-new style every time.

## Installation

Clone the repository and copy the skill into your Codex skills directory:

```bash
git clone https://github.com/AndrewDzzz/Table-latex-skills.git
cp -R Table-latex-skills/latex-table-specialist ~/.codex/skills/
```

## Example prompts

You can use direct style requests such as:

- `Use mmmeri-two-column for this parameter table.`
- `Turn this into an mmmeri-grouped-metrics results table.`
- `Use fancy-latex-tables style with a unit row and tighter cmidrules.`
- `Restyle this LaTeX table to match mmmeri/fancy-latex-tables.`
- `Make this benchmark table denser, but keep the MMERI look.`

## Emphasis conventions

For result tables, the repository recommends a simple and consistent emphasis policy:

- use bold for the best value within a directly comparable metric group
- use italics for the second-best directly comparable value
- use bold for main headers and grouped headers when stronger hierarchy is needed
- do not bold or italicize singleton values that are not part of a real comparison

Typical helper macros look like this:

```latex
\newcommand{\tblhead}[1]{\textbf{#1}}
\newcommand{\tblgroup}[1]{\textbf{#1}}
\newcommand{\best}[1]{\textbf{#1}}
\newcommand{\secondbest}[1]{\textit{#1}}
\newcommand{\na}{--}
```

This keeps the markup readable and makes it easy to change emphasis rules later.

## Typical use cases

- thesis result tables
- machine learning benchmark tables
- system configuration tables
- ablation and comparison tables
- structured appendix tables

## What is inside the skill

`latex-table-specialist/SKILL.md` contains the trigger logic and working rules.

The `references/` directory contains the reusable knowledge base:

- `overview.md`: high-level table philosophy
- `preset-catalog.md`: the main families and detail modules
- `layout-tuning.md`: spacing, width, and density guidance
- `mmmeri-fancy-latex-tables.md`: the extracted reference language from the MMERI project

The skill-level README is here:

- `latex-table-specialist/README.md`

That file is written for day-to-day style selection, while this repository README explains the project as a whole.

## Scope

This repository is intentionally narrow.

It is not a general LaTeX boilerplate collection.
It is not a multi-style table zoo.
It is a focused skill package for producing stronger LaTeX tables with one coherent visual language.

## Current status

- one skill
- one reference style family
- preset-based workflow
- in-repo references for consistent usage

## License

No license file has been added yet.
