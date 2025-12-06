Module 2: Section loop
Purpose
Process each section in order: extract text, summarize according to summary_level, and enforce constraints (evidence-only, word limits, terminology consistency).

Per-section procedure
Extract section text:

Use exact heading order from user.

If missing/empty: Do not fabricate content; emit only warning.

Summarization (evidence-only):

short:

Output: 1–2 sentences reflecting provided text.

No bullets.

detailed:

Output: 1 short paragraph (3–5 sentences) + 3–5 bullets.

Bullets: Concrete findings, methods, numbers, definitions, or limitations present in text.

Constraint enforcement:

Word limit: Truncate to ≤ requested limit (≤200).

Terminology consistency: Apply canonical terms from Intake.

Unsupported claims: Replace with “Not stated in the provided text.”

Warnings: If <50 words, include standard short-section warning.

Count and record:

Word count per section summary (post-truncation).

Any warnings triggered during processing.

Outputs (per section)
Section summary: Formatted per summary_level, within word limit.

Word count: Integer.

Warnings: List (if any).
