---
name: paper-format-template
description: Apply a fixed academic-paper DOCX layout distilled from a supplied manuscript template, without rewriting scientific content. Use when ChatGPT needs to format an existing Chinese, English, or bilingual research-paper draft; normalize title, authors, affiliations, abstract, keywords, numbered headings, body text, figures, captions, tables, equations, references, page geometry, line numbering, and related submission documents such as Highlights, Cover Letter, Conflict of Interest, and Supplementary Caption. Preserve the user's language, wording, claims, section meaning, data, references, and argumentation unless the user separately asks for content editing.
---

# Paper Format Template

Apply formatting only. Treat the source document as authoritative for content.

## Non-negotiable boundary

- Preserve all scientific content, wording, claims, data, citations, section meaning, and argumentation.
- Do not translate unless the user explicitly requests translation.
- Do not invent, delete, merge, reorder, or rewrite sections for rhetorical reasons.
- Do not add experiments, references, conclusions, or journal-specific claims.
- Do not copy topic-specific wording from the template manuscript into a new paper.
- When structure is ambiguous, format conservatively and report the ambiguity instead of changing content.

## Language behavior

Detect the document language from the text.

- Chinese input -> return Chinese content with Chinese font mappings and the same template geometry.
- English input -> return English content with English font mappings.
- Bilingual input -> use Chinese fonts for East Asian text and Times New Roman for Latin letters and numbers.
- Mathematical expressions -> use Cambria Math when represented as Word equations.

Read [references/language-rules.md](references/language-rules.md) when applying Chinese or bilingual font rules.

## Manuscript workflow

1. Inspect the input DOCX and identify semantic roles without changing text:
   - article type label, if present
   - title
   - author line(s)
   - affiliations and corresponding-author line(s)
   - abstract and keywords
   - numbered headings
   - body paragraphs
   - figures and figure captions
   - tables and table captions
   - equation blocks
   - references heading and entries
2. Apply the exact layout rules in [references/manuscript-format.md](references/manuscript-format.md).
3. For deterministic formatting, prefer `scripts/format_paper.py`.
4. If automatic role detection is uncertain, preserve the text and formatting relationship rather than guessing a new structure.
5. Render the output DOCX and inspect every page before delivery when the environment supports DOCX rendering.

## Submission-material workflow

When the user supplies or requests formatting of Highlights, Cover Letter, Conflict of Interest, or Supplementary Caption, read [references/submission-materials.md](references/submission-materials.md).

These files have their own page margins and typography. Do not apply manuscript body settings to them.

## Tables

For ordinary data tables, apply the template's three-line scientific-table treatment:

- no vertical rules
- no internal vertical gridlines
- top rule and bottom rule only at table level
- stronger header top/bottom rules
- centered short headers and numerical cells
- Times New Roman / SimSun mapping at 10.5 pt

Do not convert equation-layout tables or special-purpose abbreviation tables into data tables.

## Figures and captions

- Center image-bearing paragraphs.
- Place figure captions below figures.
- Place table captions above tables.
- Use 10.5 pt caption text.
- Bold only the label prefix such as `Fig. 1.` / `图 1.` / `Table 1` / `表 1`; keep caption text regular.
- Center short single-line captions; allow long multi-line captions to use the manuscript text width.

## Equations

Preserve native Word equations whenever possible.

For numbered display equations, preserve the visual pattern:

- equation centered
- number right-aligned as `(1)`, `(2)`, ...
- no visible surrounding borders

Do not alter equation content.

## Output contract

Return a formatted DOCX, not a prose description of what the user should change manually, unless the user explicitly asks only for a style audit.

Before delivery, verify:

- language unchanged unless requested
- no scientific text changed
- A4 page geometry and margins correct
- fonts and sizes correct
- heading spacing correct
- body indentation and line spacing correct
- captions in correct positions
- ordinary data tables have no vertical rules
- equations retain numbering layout
- references remain intact
- line numbering is continuous for manuscript files
