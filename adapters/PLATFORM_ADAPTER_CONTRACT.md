# Platform Adapter Contract

## Purpose
A Platform Adapter connects the canonical RUNTONG Business AI Core to a specific agent platform without changing the business methodology.

`Business Core != Company Pack != Customer/Project Memory != Platform Adapter != Model != Tools`

## Repository root portability
Every adapter must resolve logical `REPO_ROOT` / `AGENT_ROOT` automatically.

Use this order:
1. platform-provided repository/workspace/project root;
2. upward discovery until `AGENTS.md`, `core/`, and `skills/` are found together;
3. package/plugin/import root;
4. remote repository root exposed by the platform;
5. manual open/mount/clone/select only as a last resort.

Never hard-code developer-specific absolute paths or persist them into reusable knowledge.

## Canonical sources
Adapters must point to, not duplicate:
- `<REPO_ROOT>/AGENTS.md`
- `<REPO_ROOT>/core/MODEL_AGNOSTIC_RUNTIME.md`
- `<REPO_ROOT>/core/BUSINESS_KERNEL.md`
- `<REPO_ROOT>/skills/`
- `<REPO_ROOT>/cases/`
- `<REPO_ROOT>/company/ACTIVE_COMPANY.yaml`
- `<REPO_ROOT>/company/packs/runtong/`
- `<REPO_ROOT>/schemas/`
- `<REPO_ROOT>/evals/`

`knowledge/` is for generic non-company knowledge.

## Adapter responsibilities
An adapter may define only platform-specific mechanics:
1. boot entry;
2. repository-root resolution;
3. context map;
4. skill packaging/discovery;
5. tool map;
6. customer/project memory bridge when available;
7. permission boundary;
8. degradation behavior;
9. evaluation entry.

## Adapter prohibitions
An adapter must not:
- rewrite/fork the Business Kernel;
- maintain a second copy of negotiation/writing/risk logic;
- change the RUNTONG Company Pack silently;
- weaken source-precedence or fact-discipline rules;
- persist machine-local paths into reusable knowledge;
- claim unavailable tools/integrations exist;
- treat successful installation as proof of business-quality equivalence.

## Context loading
Prefer selective loading:
- always-on content should be short/high-signal;
- skills load only when relevant;
- RUNTONG Company Pack files load by active task/category;
- Golden Cases load by conflict/objective, not product keyword alone;
- customer/project memory loads only for the active context.

## Company maintenance compatibility
Adapters must preserve the same company-update lifecycle:

`normal conversation → Core candidate detection → operator decision → pending → curation → review → formal pack update`

A platform must not bypass operator review simply because it supports file writes automatically.

## Capability degradation
When a platform lacks a required capability:
- state the limitation when material;
- complete the reliable part;
- mark missing evidence/execution `TO_CONFIRM`;
- never fabricate file access, web research, memory retrieval, or action completion.

## Readiness levels
- **A0 — Generic**: can receive generic instructions manually.
- **A1 — Booted**: native entry resolves repo root and canonical core.
- **A2 — Skills mapped**: skills can be discovered/invoked on demand.
- **A3 — Tools & memory mapped**: external capabilities and memory bridge are configured.
- **A4 — Evaluated**: required business, company-scope, and E2E tests pass.

Only A4 should be described as production-validated for the target harness.
