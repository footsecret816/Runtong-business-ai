# Business AI Evals

Purpose: verify that a new model or agent harness preserves the intended RUNTONG business behavior, fact discipline, and company-information boundaries.

## Evaluate behavior, not wording
A model does not need to produce the same sentence. It should preserve the same business reasoning, factual discipline, risk boundaries, response depth, company scope, and communication quality.

## Core dimensions
- task understanding;
- fact vs inference control;
- gap diagnosis;
- negotiation logic;
- business-writing quality;
- risk control;
- appropriate response depth;
- project-advancement usefulness.

## Existing core benchmark set
The 12 reusable business benchmarks remain the main business-quality suite, covering MOQ, pricing basis, follow-up, sample deviation, IP, prospect qualification, mixed-SKU MOQ, existing-customer tone, false precision, price floor, deposit exception, and credibility/NDA boundaries.

## RUNTONG company-pack evals
Existing RUNTONG tests cover certification scope, core-vs-extended category boundaries, and supply-chain/factory-ownership claims.

The company-maintenance upgrade adds:
- `EVAL-CP-004-COMPANY-UPDATE-CANDIDATE.md` — durable new company fact found in normal business dialogue;
- `EVAL-CP-005-PROJECT-EXCEPTION-NOT-COMPANY-KNOWLEDGE.md` — prevent one-project exceptions from polluting Company Knowledge;
- `EVAL-CP-006-EXPLICIT-COMPANY-CORRECTION.md` — explicit correction/supersession of an old company fact.

## Company-maintenance critical failures
Treat as critical failure when the model:
- silently writes a conversation-derived candidate into the formal Company Pack without operator review;
- treats a customer/project exception as a durable RUNTONG capability;
- generalizes a factory/product-specific certificate/capability to the whole company without evidence;
- ignores a newer explicit company correction and continues using the superseded fact;
- invents a company update source or claims a file was updated when it was not.

## Scoring
Use `SCORING.md` for the 0–2 rubric and critical-fail rules. Use `RUN-TEMPLATE.md` to record comparable model/harness runs.

## End-to-end acceptance
- `E2E-ACCEPTANCE-V1.md` — original five-workflow architecture simulation.
- `E2E-COMPANY-MAINTENANCE-V2.md` — company-update lifecycle acceptance scenarios.

A platform is not production-validated merely because the repository can be imported. Run the required business, company-pack, and E2E suites on the target model/harness.
