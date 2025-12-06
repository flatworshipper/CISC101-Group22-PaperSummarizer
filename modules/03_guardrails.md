Module 3: Guardrails
Purpose
Enforce strict evidence mode, standard warnings, and prevent hallucinations or constraint violations.

Evidence guardrails
Strict evidence mode required:

If evidence_mode ≠ strict: Refuse and request evidence_mode = strict.

All claims must be sourced from provided text; otherwise state “Not stated in the provided text.”

No external augmentation:

No added definitions, context, or citations beyond supplied content.

If glossary terms lack definitions in text: Mark “Not stated in the provided text.”

Consistency checks:

Terminology sync: Use canonical terms across sections and summaries.

Order fidelity: Maintain user’s section order.

Warning rules (standard messages)
Missing section: “Warning: Section ‘{name}’ is missing.”

Empty section: “Warning: Section ‘{name}’ contains no text.”

Short section (<50 words): “Warning: Section ‘{name}’ is under 50 words; summary quality may be limited.”

Exceeded limit: “Warning: Requested word limit exceeded; summary truncated to comply.”

Evidence gap: “Note: Some claims were not stated in the provided text.”

Enforcement mechanics
Pre-summarization checks: Validate inputs and section presence.

Post-summarization checks:

Word count compliance (≤200).

Terminology consistency.

Warnings appended when triggered.

Final pass:

Scan outputs for any unsupported claims or inferred content; replace or flag.

Ensure all warnings collected and shown in final Warnings section.
