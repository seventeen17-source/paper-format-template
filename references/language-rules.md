# Chinese, English, and bilingual font rules

## Core rule

Preserve the document's language. Formatting is not translation.

## English

- Main Latin font: Times New Roman.
- Submission-file exceptions: Arial where specified in `submission-materials.md`.
- Equations: Cambria Math.

## Chinese

Use East Asian font assignments while keeping Latin characters and numbers in Times New Roman unless a submission-file rule explicitly uses Arial.

### Manuscript

- Chinese title: SimHei / 黑体, 18 pt, bold.
- Chinese numbered headings: SimHei / 黑体, 12 pt, bold.
- Chinese body: SimSun / 宋体, 10.5 pt.
- Chinese abstract/keywords/captions/references: SimSun / 宋体 at the sizes defined by the manuscript specification.
- Latin letters and Arabic numerals inside Chinese text: Times New Roman at the surrounding size.

### Submission materials

When the source layout specifies Arial, use Arial for Latin text. For Chinese characters, use a compatible Chinese sans-serif font while preserving the same point size; prefer Microsoft YaHei when available. Do not substitute a visually unrelated decorative font.

## Bilingual text

Set run-level OOXML font mappings so that:

- `w:ascii` and `w:hAnsi` use the Latin font.
- `w:eastAsia` uses the Chinese font.

This allows a sentence such as `本研究采用 ConvNeXt V2 进行分析` to render Chinese characters with the Chinese font and Latin letters/numbers with Times New Roman without splitting or rewriting the sentence.

## Labels

When formatting Chinese papers, support localized labels already present in the document, such as:

- `摘要：`
- `关键词：`
- `图 1.`
- `表 1`
- `参考文献`

Do not automatically translate `Abstract`, `Keywords`, `Fig.`, or `Table` into Chinese unless the user requests localization or the source document already uses Chinese labels.
