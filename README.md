# paper-format-template

A format-only ChatGPT Skill for academic-paper DOCX files.

It was distilled from a supplied manuscript and submission-material set, but intentionally contains **no research topic, scientific argument, experiment design, model description, or reusable paper prose**.

## What it does

- Keeps the original language: Chinese stays Chinese; English stays English.
- Preserves scientific wording, data, claims, citations, equations, and section meaning.
- Applies a fixed manuscript layout: page geometry, fonts, sizes, heading spacing, body indentation, line spacing, continuous line numbering, figure/table captions, scientific tables, equations, and references.
- Supports Chinese/English mixed typography.
- Includes separate format specifications for Highlights, Cover Letter, Conflict of Interest, and Supplementary Caption.

## Typical prompt

> Format this Chinese manuscript with `paper-format-template`. Change formatting only; do not rewrite, translate, add, delete, or reorder scientific content. Return the formatted DOCX.

English input works the same way.

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
└── scripts/
    ├── format_paper.py
    └── check_format.py
```

## Main manuscript format distilled

- A4 portrait.
- Margins approximately: top 2.30 cm, bottom 1.70 cm, left 2.50 cm, right 1.50 cm.
- Title: 18 pt bold.
- Authors/affiliations: 11 pt.
- Body: 10.5 pt, justified, double-spaced, 0.741 cm left/right + first-line indent.
- Numbered headings: 12 pt bold, double-spaced, 15.6 pt before/after.
- Abstract/Keywords: 10.5 pt, 1.7 line spacing.
- Latin font: Times New Roman.
- Chinese body font: SimSun / 宋体.
- Chinese title/headings: SimHei / 黑体.
- Equations: Cambria Math when using native Word equations.
- Ordinary data tables: three-line style with no vertical rules.
- Continuous line numbering.

The full specification is in `references/`.

## Script usage

```bash
pip install -r requirements.txt
python scripts/format_paper.py input.docx output.docx
python scripts/check_format.py output.docx
```

The formatter uses conservative heuristics. When a source document has ambiguous semantic roles or complex custom layout, the Skill should inspect the DOCX and preserve content rather than guessing.
