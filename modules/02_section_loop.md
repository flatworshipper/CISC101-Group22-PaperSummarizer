[Change Log – Dec 2025]
- Added summary_level variable and conditional behavior for short vs detailed summaries.
- Clarified enforcement of word limits and evidence-only rule for each section.

## Module 2: Section loop

### Purpose
Process each section in order: extract text, summarize according to `summary_level`, and enforce constraints (word limits, no hallucinations, consistent terminology).

---

### Inputs (from Module 1)
- Ordered list of section headings.
- Mapping from section heading → section text.
- Global constraints:
  - `word_limit` (≤ 200 words per section; default 200).
  - `summary_level` (“short” or “detailed”).
  - `evidence_mode` (must be "strict").
  - Terminology map for canonical terms.

---

### Per-section procedure

1. **Select section in order**
   - Take the next section heading from the ordered list.
   - Retrieve its corresponding text (if missing/empty, record a warning and do not fabricate content).

2. **Apply strict evidence rule**
   - Summaries must only use information explicitly present in the section text.
   - If a requested detail is not in the text, state:  
     `Not stated in the provided text.`

3. **Choose behavior based on `summary_level`**

   - If `summary_level = "short"`:
     - Produce a **1–2 sentence** summary that captures the main idea of the section.
     - No bullet list.
     - Keep within the `word_limit` (≤ 200 words).

   - If `summary_level = "detailed"`:
     - Produce:
       - One short paragraph (about 3–5 sentences), **and**
       - A bullet list of **3–5 key points** drawn directly from the text.
     - Bullet points should highlight:
       - Important results,
       - Methods or design choices,
       - Definitions or key concepts,
       - Limitations or future work.
     - Keep the total words for this section (paragraph + bullets) within `word_limit` (≤ 200 words).

4. **Enforce constraints**
   - If the draft summary exceeds the `word_limit`, truncate gracefully while preserving meaning.
   - Replace any invented or speculative content with  
     `Not stated in the provided text.`
   - Apply canonical terminology from the terminology map (e.g., always use “Transformer” or “model” consistently).

5. **Record diagnostics**
   - Compute the final word count of the section summary after truncation.
   - Collect any warnings for:
     - Missing section text,
     - Empty section text,
     - Section text with < 50 words,
     - Truncated due to word limit.

---

### Outputs (per section)
- Formatted section summary (short or detailed, based on `summary_level`).
- Final word count (integer).
- List of warnings (possibly empty) for that section.
