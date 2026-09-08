# Business AI Evals

Purpose: verify that a new model or agent harness preserves the intended business behavior.

## Evaluate behavior, not wording
A model does not need to produce the same sentence. It should preserve the same business reasoning, factual discipline, risk boundaries, response depth, and communication quality.

## Core dimensions
- task understanding,
- fact vs inference control,
- gap diagnosis,
- negotiation logic,
- business-writing quality,
- risk control,
- appropriate response depth,
- project-advancement usefulness.

## Pass criteria
Each benchmark case defines:
- required behaviors,
- prohibited behaviors,
- optional strong behaviors.

Use `SCORING.md` for the 0–2 scoring rubric and critical-fail rules. Use `RUN-TEMPLATE.md` to record comparable model/harness runs.

## Current benchmark set
- EVAL-001 — Hard MOQ vs trial order
- EVAL-002 — Annual volume vs per-order pricing
- EVAL-003 — Mature project follow-up
- EVAL-004 — Sample deviation vs extra tooling
- EVAL-005 — IP-sensitive reference design
- EVAL-006 — Broad prospect qualification
- EVAL-007 — Mixed SKU order vs production MOQ
- EVAL-008 — Existing-customer operational tone
- EVAL-009 — Irregular shape and false precision
- EVAL-010 — Price negotiation near floor
- EVAL-011 — Production before deposit exception
- EVAL-012 — Credibility proof with NDA boundary

## Suggested use
Run the same benchmark set on GPT/Codex, DeepSeek, Claude, Gemini, or another model/harness before switching production usage.

The benchmark is not intended to prove that models are identical. It tests whether the reusable business method remains intact when the underlying model changes.