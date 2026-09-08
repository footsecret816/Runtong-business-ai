# Platform Adapter Contract

## Purpose

A Platform Adapter connects the canonical Business AI Core to a specific agent platform without changing the business methodology.

The repository follows **Generic Core First**:

`Business Core != Company Pack != Customer Memory != Platform Adapter != Model != Tools`

No platform is the architectural center. Codex, Claude Code, DeepSeek Harness, WorkBuddy, Accio Work, and future platforms are peers at the adapter layer.

## Canonical sources

An adapter must point to, not duplicate, the canonical sources:

- `/core/MODEL_AGNOSTIC_RUNTIME.md`
- `/core/BUSINESS_KERNEL.md`
- `/skills/`
- `/cases/`
- `/knowledge/company-packs/`
- `/schemas/customer-memory.md`
- `/evals/`

If an adapter conflicts with a canonical business rule, the canonical rule wins.

## Adapter responsibilities

A platform adapter may define only the platform-specific mechanics needed to run the canonical framework:

1. **Boot entry** — which platform file or instruction surface starts the agent.
2. **Context map** — how the platform finds the Runtime Contract, Kernel, Company Pack, Cases, and Memory.
3. **Skill packaging** — how canonical skills are exposed through the platform's skill/plugin format.
4. **Tool map** — which required capabilities actually exist: web, browser, file/image/PDF reading, shell, MCP, calendar, email, database, etc.
5. **Memory bridge** — how customer/project memory is retrieved and updated without copying raw memory into the reusable core.
6. **Permission boundary** — how the platform enforces or surfaces sensitive actions, approvals, and unavailable tools.
7. **Degradation behavior** — what the agent must do when a required platform capability is unavailable.
8. **Evaluation entry** — how the target model/harness runs the canonical benchmark and E2E suite.

## Adapter prohibitions

A platform adapter must not:

- rewrite or fork the Business Kernel;
- maintain a second copy of negotiation, prospecting, writing, or risk logic;
- embed real customer histories into the reusable adapter;
- promote Company Pack facts into project-specific facts;
- weaken the source-precedence and fact-discipline rules;
- claim a tool or integration exists when the target harness does not provide it;
- treat successful installation as proof that the target model passes business-quality evaluation.

## Context-loading rule

Prefer selective loading:

- always-on content should be short and high-signal;
- full skills should load only when relevant;
- product knowledge should load only for the active category;
- Golden Cases should load by business conflict/objective rather than product name;
- Customer Memory should load only for the active customer/project.

If a platform only supports a single large system prompt, the adapter should still use pointers/sections and preserve the same logical boundaries rather than flattening every repository file into one permanent prompt.

## Capability degradation rule

When the platform lacks a required capability:

- state the limitation when it materially affects the result;
- complete the reliable part of the task;
- mark missing external evidence or execution as `TO_CONFIRM`;
- never fabricate web research, file contents, memory retrieval, tool execution, or action completion.

## Adapter readiness levels

- **A0 — Generic**: platform can receive the generic system/runtime instructions manually.
- **A1 — Booted**: native platform entry file/config correctly points to the canonical core.
- **A2 — Skills mapped**: relevant skills can be discovered or invoked on demand.
- **A3 — Tools & memory mapped**: required external capabilities and customer-memory bridge are configured.
- **A4 — Evaluated**: target model/harness passes the required benchmark, Company Pack, and E2E acceptance thresholds.

Only A4 should be described as production-validated for this Business AI Harness.

## Versioning principle

Platform adapters may change frequently as platforms evolve. The Business Core should change only when the business methodology itself changes.

When a platform changes its native file layout or plugin API, update that adapter and rerun Evals; do not redesign the Business Core unless the business behavior actually needs to change.
