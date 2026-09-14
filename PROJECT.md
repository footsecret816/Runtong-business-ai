# Runtong Business AI — Company-Maintenance Architecture Baseline

## Purpose
A dedicated RUNTONG / WAYEAH Business AI Harness for B2B foreign-trade work.

The business methodology remains model-agnostic and platform-agnostic, but this repository is intentionally **company-specific**: the RUNTONG / WAYEAH Company Pack is already installed and is the default company context.

## Core runtime
`Context → Understand → Diagnose → Decide → Communicate → Advance`

For complex commercial conflict: Strategy before Writing.
For simple tasks: stay simple.

## Architecture
- `core/` — model-agnostic runtime and lightweight business kernel
- `skills/` — 9 reusable business capabilities, including company-knowledge curation
- `cases/` — anonymized Golden Cases and anti-patterns
- `company/` — RUNTONG company workspace, maintenance queue, and formal Company Pack
- `memory/` / external memory — customer/project history layer when available
- `knowledge/` — generic non-company knowledge only
- `schemas/` — data contracts
- `evals/` — business and company-maintenance benchmarks
- `adapters/` — thin platform integration layer

## RUNTONG Company model
The formal company source is:

`company/packs/runtong/`

The repository does not need zero-start onboarding. Instead, the company layer supports continuous maintenance through three update paths:

1. **Source-material update** — new PDF/PPT/Word/Excel/certificate/catalogue or other company material → `company/inbox/` → `company-knowledge-curation` → review → formal pack update.
2. **Business-conversation patch** — normal business dialogue reveals a likely durable company fact → Core marks `COMPANY_UPDATE_CANDIDATE` → operator decides whether to review → `company/pending/` → curation → pack update.
3. **Explicit company correction** — operator directly states that an existing RUNTONG company fact has changed and asks to update it → curation checks scope/source/supersession → review → formal update.

## Company Delta Detection
The Core performs only lightweight detection during normal business work. It must not continuously run the heavy curation skill and must not silently rewrite formal company facts.

A candidate should normally be:
- relatively stable,
- reusable across future RUNTONG business,
- company/factory/product scoped rather than customer/project-only,
- supported by operator statement or source evidence.

Examples that normally **do not** enter the Company Pack:
- one customer's price,
- one project's MOQ,
- one-off boss approval,
- temporary supplier quote,
- rush delivery exception,
- project-specific payment exception,
- unconfirmed inference.

## Fact and scope discipline
Current-project confirmed facts override company-general knowledge.

Company-level, factory-level, product-level, project-level, and customer-level facts must remain distinguishable. Certifications, testing capability, capacity, production claims, and factory capability must not be generalized beyond their confirmed scope.

## Portability
All repository paths are resolved relative to logical `AGENT_ROOT` / `REPO_ROOT`. Machine-specific absolute paths are runtime-only state and must not be persisted into reusable business knowledge.

## Validation
Existing business benchmarks remain authoritative. Additional company-maintenance evals verify that:
- durable new RUNTONG facts are detected as candidates rather than silently committed;
- customer/project exceptions do not pollute Company Knowledge;
- explicit company corrections can supersede older company facts only through the review/update workflow.
