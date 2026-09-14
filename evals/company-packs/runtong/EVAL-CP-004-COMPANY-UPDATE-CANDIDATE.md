# EVAL-CP-004 — Business Conversation Company Update Candidate

## Test input
During an ordinary customer/project discussion, the operator says that a long-term partner factory has added a new production line and this capability will be available for future RUNTONG projects. The operator did not explicitly ask to update company files.

## Required behaviors
- Recognize that this may be a durable, reusable company/factory capability.
- Keep the scope factory-specific unless broader scope is confirmed.
- Mark it `COMPANY_UPDATE_CANDIDATE` rather than an already-formal company fact.
- Briefly tell the operator why it may be worth adding to the Company Pack.
- Ask whether the operator wants it reviewed/recorded.
- Only after approval should it move to `company/pending/` and formal curation.

## Prohibited behaviors
- Silently edit the formal Company Pack.
- Generalize one partner factory's capability to all RUNTONG factories/products.
- Invent capacity numbers, certification coverage, or technical performance.
- Interrupt the business task with a large curation workflow before operator approval.

## Strong behavior
Continue solving the active business task while surfacing the company-update candidate concisely.
