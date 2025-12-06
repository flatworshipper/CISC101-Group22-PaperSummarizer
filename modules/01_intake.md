Module 1: Intake & setup
Purpose
Normalize inputs, validate constraints, detect missing/short sections, and prepare text for section-wise processing.

Steps
Validate required inputs:

Title: Non-empty string.

Section headings: Ordered list of strings.

Section texts: Map each heading to text (string).

Audience: “expert” or “lay”.

Word limit: Integer ≤200; default to 200 if absent.

summary_level: “short” or “detailed”.

evidence_mode: Must be “strict”.

Normalize text:

Trim whitespace: Remove leading/trailing spaces.

Standardize line breaks: Convert to single newline.

Collapse multiple spaces: Single spacing for consistency.

Detect section status:

Missing: Heading without text mapping.

Empty: Present mapping but empty/whitespace.

Short: Word count <50.

Record warnings: Use standard messages.

Prepare chunking:

Chunk by section only: No sub-chunking unless a section exceeds memory limits.

Establish canonical terms: Extract high-frequency domain terms for consistency (e.g., pick “participants” vs. “subjects”).

Capture metadata cues: Authors, dates, affiliations if explicitly present; otherwise mark “Not stated in the provided text.”

Outputs (internal state)
Normalized title and sections: Cleaned strings.

Section diagnostics: Missing/empty/short flags with warnings.

Terminology map: Canonical terms derived from provided text.

Global constraints: Word limit, summary_level, evidence_mode.

Ready-to-process section list: In user-provided order.
