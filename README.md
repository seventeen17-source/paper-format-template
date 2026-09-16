# paper-format-template

一个**只负责论文排版、不改科研内容**的 ChatGPT Skill。它从一套实际 manuscript + submission materials 中蒸馏出 Word/DOCX 格式规则，但不会学习或复用论文主题、论证方法、实验设计、模型内容或具体措辞。

A **format-only ChatGPT Skill** for academic-paper DOCX files. It preserves research content and applies a fixed manuscript/submission layout.

## 能做什么 / What it does

- 中文输入仍输出中文；英文输入仍输出英文。
- 不翻译、不重写、不补实验、不改结论、不调整科研论证。
- 保留原有数据、引用、公式、图表编号、作者信息和章节含义。
- 自动规范标题、作者/单位、摘要、关键词、编号标题、正文、图题、表题、三线表、公式、参考文献、页边距、行距和连续行号。
- 支持中文/英文混排：中文使用中文字体映射，Latin letters / Arabic numerals 使用 Times New Roman。
- 另含 Highlights、Cover Letter、Conflict of Interest、Supplementary Caption 的独立格式规范。

## 最常用的调用方式 / Typical prompt

中文：

> 使用 `paper-format-template` 排版这篇中文论文。只修改格式，不要重写、翻译、增加、删除或重排任何科研内容。最后返回排好版的 DOCX。

English:

> Format this manuscript with `paper-format-template`. Change formatting only; do not rewrite, translate, add, delete, or reorder scientific content. Return the formatted DOCX.

## Repository layout

```text
./
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── manuscript-format.md
│   ├── submission-materials.md
│   └── language-rules.md
├── scripts/
│   ├── format_paper.py
│   └── check_format.py
└── requirements.txt
```

## 蒸馏出的主文稿格式 / Main manuscript format

- A4 portrait.
- Margins: top ≈ 2.30 cm, bottom ≈ 1.70 cm, left ≈ 2.50 cm, right ≈ 1.50 cm.
- Title: 18 pt, bold.
- Authors/affiliations: 11 pt.
- Body: 10.5 pt, justified, double-spaced, 0.741 cm left/right indent + 0.741 cm first-line indent.
- Numbered headings: 12 pt, bold, double-spaced, 15.6 pt before/after.
- Abstract/Keywords: 10.5 pt, 1.7 line spacing.
- Latin font: Times New Roman.
- Chinese body: SimSun / 宋体.
- Chinese title/headings: SimHei / 黑体.
- Equations: Cambria Math when using native Word equations.
- Ordinary data tables: three-line scientific-table style, no vertical rules.
- Continuous line numbering.

完整细则见 `references/`。

## Scripts

安装依赖：

```bash
pip install -r requirements.txt
```

格式化：

```bash
python scripts/format_paper.py input.docx output.docx
```

检查基础版式：

```bash
python scripts/check_format.py output.docx
```

## 设计边界 / Design boundary

这个仓库的核心原则是 **format only**。

当输入结构存在歧义时，应优先保留原文和原结构，而不是猜测、改写或重新组织内容。自动脚本使用保守的语义识别；复杂 DOCX 应结合 Skill 规则进行检查后再交付。
