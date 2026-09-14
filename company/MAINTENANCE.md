# RUNTONG Company Information Maintenance

The RUNTONG / WAYEAH Company Pack already exists. This workflow is for **maintenance and correction**, not zero-start onboarding.

## Route A — New source materials
Use when the operator provides new company materials such as PDF/PPT/Word/Excel, certificates, audits, catalogues, capacity/equipment updates, or other company documents.

1. Place/make the material available under `company/inbox/`.
2. Load `skills/company-knowledge-curation/`.
3. Extract candidate facts from the source.
4. Classify scope: company / factory / product / project / customer.
5. Compare against the current RUNTONG Company Pack.
6. Detect duplicates, conflicts, and possible superseded facts.
7. Mark uncertain items `TO_CONFIRM`.
8. Produce a review draft showing exactly what would change.
9. Operator may correct/add/reject items over multiple rounds.
10. Only after explicit confirmation, update `company/packs/runtong/`, `SOURCES.md`, and version metadata.

## Route B — Business Conversation Patch
Use when normal business dialogue naturally reveals a possible durable company fact.

1. Core performs only lightweight detection.
2. If the information appears long-term + reusable + correctly scoped, mark `COMPANY_UPDATE_CANDIDATE`.
3. Tell the operator what was detected and why it may be worth storing.
4. Ask whether it should be reviewed for the RUNTONG Company Pack.
5. If the operator says no, continue normal business work and do not update the pack.
6. If the operator says yes, record/place the candidate under `company/pending/`.
7. Invoke `company-knowledge-curation`.
8. Verify source, scope, conflict, and supersession.
9. Show the proposed patch for review.
10. After confirmation, update the formal Company Pack.

### Examples that may become candidates
- a newly obtained certificate with clear scope;
- a new long-term product line;
- new equipment or sustained production capacity;
- a new persistent partner-factory capability;
- a stable new sourcing/manufacturing route;
- a market/channel coverage change;
- an old capability no longer available.

### Examples that should normally stay out of Company Knowledge
- one customer gets a special price;
- one project has a special MOQ;
- one order receives a rush-delivery exception;
- boss approves production before deposit for one order;
- a temporary supplier quote;
- a project-specific test result;
- a customer-specific packaging exception.

These belong to customer/project memory or current-project context.

## Route C — Explicit company correction
Use when the operator directly says an existing RUNTONG company fact is wrong/outdated and asks to correct the company information.

1. Route directly to `company-knowledge-curation`; no candidate prompt is needed.
2. Identify the old fact and its current source/scope.
3. Identify the new confirmed statement/source.
4. Mark the old fact `SUPERSEDED` where appropriate rather than silently losing history.
5. Show the proposed change.
6. After operator confirmation, update the formal pack and source/version records.

## Admission test
Before a fact enters the Company Pack, ask:
- Is it relatively stable?
- Is it reusable in future RUNTONG business?
- Is its scope clear?
- Is it supported by operator confirmation or source evidence?
- Is it truly company/factory/product knowledge rather than a one-project exception?

If any answer is unclear, keep it `TO_CONFIRM` or in `pending/` rather than formalizing it.

## Key principle
**Normal conversation may discover company knowledge; only reviewed curation may formalize it.**
