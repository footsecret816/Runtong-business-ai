# Runtong Business AI Harness

A model-agnostic B2B business copilot framework for prospecting, inquiry analysis, negotiation, product/project follow-up, communication, risk control, company knowledge, and customer-memory integration.

The repository externalizes reusable business behavior so the operating method can survive changes in AI model or agent platform.

## Architecture principle: Generic Core First

No platform is the center of this repository.

```text
Business Core
+ Company Pack
+ Customer Memory
+ Evals
        ↓
Platform Adapter
        ↓
Codex / Claude Code / DeepSeek Harness / WorkBuddy / Accio Work / future platform
        ↓
Target model + available tools
```

Platform-specific files are adapters only. Business logic must remain canonical in the Core, Skills, Cases, Company Packs, Memory rules, and Evals.

## What V1 contains

- **1 primary Business Copilot entry** — `AGENTS.md`
- **1 lightweight Business Kernel** — `core/BUSINESS_KERNEL.md`
- **1 model-agnostic runtime contract** — `core/MODEL_AGNOSTIC_RUNTIME.md`
- **8 broad business skills** — `skills/`
- **abstract Golden Cases + Anti-patterns** — `cases/`
- **cross-model benchmarks + E2E acceptance** — `evals/`
- **swappable Company Packs** — `knowledge/company-packs/`
- **customer-memory schema only** — `schemas/customer-memory.md`
- **thin platform adapters** — `adapters/`

## Runtime concept

```text
User task
   ↓
Platform adapter / agent entry
   ↓
Model-agnostic runtime rules
   ↓
Business Kernel
   ↓
Relevant Skills only
   ↓
Relevant Cases / Company Pack / Customer Memory only when needed
   ↓
Validation
   ↓
Output
```

The framework deliberately avoids loading every skill, case, or knowledge file for every task.

## Core behavior

- Simple tasks stay simple.
- Complex commercial conflicts follow **diagnosis → strategy → communication**.
- Facts, inference, unknowns, and items to confirm remain distinct.
- Current project facts outrank company-general knowledge and abstract cases.
- The AI may recommend but must not invent approval for price, MOQ exceptions, payment terms, delivery commitments, compensation, certifications, or technical conclusions.
- Reusable cases teach reasoning patterns; they are never current-customer evidence.

## Skills

See `skills/INDEX.md`.

V1 uses eight broad skills rather than many small modules:
- customer analysis,
- prospecting,
- gap & strategy,
- negotiation,
- business writing,
- factory/customer bridge,
- risk guard,
- project next action.

## Company knowledge

Company-specific knowledge is isolated from the reusable core.

The current RUNTONG / WAYEAH pack is under:

`knowledge/company-packs/runtong/`

It includes company positioning, product capabilities, supply-chain model, compliance boundaries, markets/customers, SOP, source provenance, and on-demand product-category files.

A different company should add or replace a Company Pack without changing the Core Kernel or Skills.

## Customer memory

The reusable repository stores the **schema**, not raw customer history.

Real customer/project memory should remain in a separate private data layer where possible. Superseded facts, source provenance, and project-specific scope must be preserved.

## Cases and privacy

Golden Cases are abstracted from real business patterns but must remove unnecessary identifying details such as:
- customer names and contacts,
- email addresses,
- PO/SKU identifiers when identifying,
- confidential prices/payment records,
- unnecessary exact dates,
- supplier identities.

See `cases/CASE-EXTRACTION-GUIDE.md`.

## Evaluation

Use `evals/SCORING.md` and `evals/RUN-TEMPLATE.md` to compare models or harnesses.

Current evaluation assets include:
- 12 core benchmark cases,
- company-pack-specific boundary tests,
- `evals/E2E-ACCEPTANCE-V1.md` covering five full business workflows.

A model does not need identical wording to pass. It must preserve factual discipline, business diagnosis, strategy quality, risk boundaries, response depth, and business usefulness.

## Platform portability

See:

- `adapters/PLATFORM_ADAPTER_CONTRACT.md`
- `adapters/COMPATIBILITY_MATRIX.md`

The current architecture is intended to adapt to Codex, Claude Code, DeepSeek Harness, WorkBuddy / CodeBuddy, Accio Work, and future agent platforms through thin adapters.

Do not prebuild every native adapter. Implement a native adapter when the platform is actually selected, then run the same canonical Evals.

If a target harness lacks a capability such as web search, file reading, browser access, or persistent memory, the AI must not pretend that capability exists.

## V1 status

V1 architecture has completed an architecture-level E2E simulation on the current model and passed after one source-precedence fix. Independent target-model validation is still required before claiming equivalent performance on another model/harness.

See `PROJECT.md` for the architecture baseline.

> Real customer data should not be placed in the reusable core case library.
