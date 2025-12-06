Student module B: Citation extractor
Purpose
Extract in-text citations and reference entries from the provided sections without external augmentation.

Inputs
Sections likely to contain citations: Background, Related Work, Methods, Results, Discussion, References/Bibliography.

Procedure
Detect in-text citations:

Patterns: (Author, Year), [Number], superscripts, or author-year mentions.

Extract as-is with surrounding context snippet (≤20 words).

Extract reference entries:

From References section only.

Capture fields present: Authors, year, title, venue, pages.

Do not normalize styles beyond the provided text.

De-duplicate:

Match by author-year or bracket number; consolidate duplicates.

Evidence-only:

No completion or guessing of missing fields.

Output
“Citation extractor” section:

In-text citations list: Author/Year or Number + short context.

Reference entries list: Full entries exactly as provided.

Warnings: If References section missing/empty or few citations found.
