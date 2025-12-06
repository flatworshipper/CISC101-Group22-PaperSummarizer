Module 4: Rendering
Purpose
Assemble final output in consistent markdown: Paper summary header, Section table, Section summaries, Unified final summary, Expert/Lay summaries, Mini-glossary, and Warnings.

Formatting rules
Markdown structure:

H1: Paper summary (title).

H2: Section table.

H2: Section summaries.

H2: Unified final summary.

H2: Expert summary.

H2: Lay summary.

H2: Mini-glossary.

H2: Warnings.

Lists and labels:

Use bold lead-ins for bullets and numbered items (e.g., “Objective: …”).

Avoid redundant phrasing and maintain clarity.

Section table:

Columns: Section name | Summary word count | Warnings.

Place sources line only if needed: Not applicable here.

No citations in cells.

Word limits:

Per-section summaries ≤200 words.

Unified/Expert/Lay summaries ≤200 words each.

Terminology:

Apply canonical terms consistently across all rendered sections.

Rendering pipeline
Paper summary header:

Title: From inputs.

Optional metadata: Authors/affiliations/dates only if explicitly present; otherwise “Not stated in the provided text.”

Section table:

Row per section: Name, word count, warnings (comma-separated).

Section summaries:

In order: Use summary_level formatting.

Include per-section headings matching user input.

Unified final summary:

Integrate across sections without introducing unsupported claims.

Respect canonical terms.

Expert summary:

Concise, technical tone, leverage domain terms present in the text.

No external jargon beyond supplied definitions.

Lay summary:

Plain language: Explain terms only if definitions appear in the text; else mark “Not stated in the provided text.”

No added analogies beyond text evidence.

Mini-glossary:

5–12 terms: Only if definitions or clear meanings appear in the text.

If absent: Populate with “Not stated in the provided text” per term.

Warnings:

Aggregate list from all modules and steps.
