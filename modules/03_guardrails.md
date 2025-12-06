[Change Log – Dec 2025]
- Added explicit evidence_mode flag with strict behavior.
- Defined standardized warning messages for missing, empty, and very short sections.
- Clarified final checks for hallucinations and constraint violations.

## Module 3: Guardrails

### Purpose
Enforce strict evidence-based behavior, standardized warnings, and final safety checks so the summarizer never hallucinates and always respects constraints.

---

### Inputs (from other modules)
- `evidence_mode` (string; must be `"strict"`).
- Section diagnostics from Module 1 (missing, empty, <50 words).
- Draft section summaries from Module 2.
- Global constraints (word_limit, canonical terminology, section order).

---

### Evidence mode

1. **Check evidence_mode**
   - If `evidence_mode` is not `"strict"`:
     - Do not proceed with summarization.
     - Instruct the system to respond with:  
       `The summarizer only runs with evidence_mode = "strict". Please enable strict evidence mode and try again.`

2. **Strict evidence behavior**
   - Every claim in summaries must be directly supported by the provided text.
   - If a claim cannot be supported, replace it or annotate with:  
     `Not stated in the provided text.`

---

### Standard warning messages

For each section, use these standardized messages:

- **Missing section text**  
  `Warning: Section "{name}" is missing.`

- **Empty section text**  
  `Warning: Section "{name}" contains no text.`

- **Very short section (< 50 words)**  
  `Warning: Section "{name}" is under 50 words; summary quality may be limited.`

- **Exceeded word limit**  
  `Warning: Requested word limit exceeded; summary truncated to comply.`

- **Evidence gap**  
  `Note: Some claims were not stated in the provided text.`

These warnings should be attached both:
- to the per-section diagnostics, and  
- to the final Warnings section rendered by Module 4.

---

### Final safety checks

Before rendering the final output:

1. **Word limit check**
   - Confirm each section summary is within its `word_limit` (≤ 200 words).
   - If not, truncate and attach the “Exceeded word limit” warning.

2. **Section diagnostics check**
   - Ensure every section with missing/empty/<50-word text has the appropriate warning attached.

3. **Evidence-only scan**
   - Review summaries for:
     - External facts,
     - Unjustified examples,
     - Extra context not in the paper.
   - Convert unsupported content to  
     `Not stated in the provided text.`  
     or remove it.

4. **Order and terminology**
   - Confirm section summaries follow the original section order.
   - Confirm canonical terminology is used consistently across the entire output.

---

### Outputs
- Cleaned, constraint-respecting summaries ready for rendering.
- A consolidated list of all warnings for use in the final Warnings section.
- Guaranteed strict evidence behavior (no hallucinations) when evidence_mode = "strict".
