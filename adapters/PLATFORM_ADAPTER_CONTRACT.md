# Platform Adapter Contract

## Purpose

A Platform Adapter connects the canonical Business AI Core to a specific agent platform without changing the business methodology.

The repository follows **Generic Core First**:

`Business Core != Company Pack != Customer Memory != Platform Adapter != Model != Tools`

No platform is the architectural center. Codex, Claude Code, DeepSeek Harness, WorkBuddy, Accio Work, and future platforms are peers at the adapter layer.

## Repository root portability

Every adapter must resolve a logical `REPO_ROOT` automatically at runtime.

`REPO_ROOT` means the active repository/workspace root of this Business AI Harness. It is not a fixed operating-system path and normal users should not need to type or configure it manually.

Use this resolution order:

1. **Platform root first** — use the repository / workspace / project root supplied by the active agent platform, if it contains the expected canonical structure.
2. **Upward discovery** — if execution starts inside a repository subdirectory, walk upward until a directory containing `AGENTS.md`, `core/`, and `skills/` is found.
3. **Package / plugin root** — when the Harness is installed or imported as a plugin, package, extension, or managed project, use the platform-provided install/package root if the canonical structure is present.
4. **Remote repository root** — when the platform exposes repository contents through a connector or remote-repository context without a local clone, use that repository as the logical `REPO_ROOT`.
5. **Manual fallback only** — only if all automatic resolution methods fail, ask the runtime/user to open, mount, clone, select, or identify the repository. Manual absolute-path entry is a last-resort fallback, not part of normal installation.

A valid `REPO_ROOT` should contain the expected canonical structure, including at minimum:

- `AGENTS.md`
- `core/`
- `skills/`

All canonical repository references must resolve relative to `REPO_ROOT`.

Adapters must not:

- hard-code a developer's local absolute path;
- assume a drive letter, username, home directory, or installation folder;
- require normal users to manually configure an absolute repository path when the platform already supplies workspace/project/repository context;
- persist a discovered machine-local path into Business Memory, Company Knowledge, Golden Cases, or reusable adapter configuration;
- silently reuse a path learned on another machine;
- guess a local repository path when the root cannot be resolved.

Examples of machine-specific paths that must never become canonical configuration include `D:\...`, `C:\Users\...`, `/Users/...`, and `/home/<user>/...`.

A platform may maintain a resolved machine-local path in ephemeral runtime/session state, but that value is environment-specific and must remain outside reusable business memory.

## Canonical sources

An adapter must point to, not duplicate, the canonical sources:

- `<REPO_ROOT>/core/MODEL_AGNOSTIC_RUNTIME.md`
- `<REPO_ROOT>/core/BUSINESS_KERNEL.md`
- `<REPO_ROOT>/skills/`
- `<REPO_ROOT>/cases/`
- `<REPO_ROOT>/knowledge/company-packs/`
- `<REPO_ROOT>/schemas/customer-memory.md`
- `<REPO_ROOT>/evals/`

`<REPO_ROOT>` is a logical runtime placeholder, not a literal folder name.

If an adapter conflicts with a canonical business rule, the canonical rule wins.

## Adapter responsibilities

A platform adapter may define only the platform-specific mechanics needed to run the canonical framework:

1. **Boot entry** — which platform file or instruction surface starts the agent.
2. **Repository-root resolution** — how the platform auto-resolves the active `REPO_ROOT` without hard-coding or normally asking for machine-specific paths.
3. **Context map** — how the platform finds the Runtime Contract, Kernel, Company Pack, Cases, and Memory relative to `REPO_ROOT`.
4. **Skill packaging** — how canonical skills are exposed through the platform's skill/plugin format.
5. **Tool map** — which required capabilities actually exist: web, browser, file/image/PDF reading, shell, MCP, calendar, email, database, etc.
6. **Memory bridge** — how customer/project memory is retrieved and updated without copying raw memory or machine-local runtime state into the reusable core.
7. **Permission boundary** — how the platform enforces or surfaces sensitive actions, approvals, and unavailable tools.
8. **Degradation behavior** — what the agent must do when a required platform capability is unavailable.
9. **Evaluation entry** — how the target model/harness runs the canonical benchmark and E2E suite.

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
- **A1 — Booted**: native platform entry file/config auto-resolves `REPO_ROOT` and points to the canonical core.
- **A2 — Skills mapped**: relevant skills can be discovered or invoked on demand.
- **A3 — Tools & memory mapped**: required external capabilities and customer-memory bridge are configured without leaking machine-local runtime state into reusable memory.
- **A4 — Evaluated**: target model/harness passes the required benchmark, Company Pack, and E2E acceptance thresholds.

Only A4 should be described as production-validated for this Business AI Harness.

## Versioning principle

Platform adapters may change frequently as platforms evolve. The Business Core should change only when the business methodology itself changes.

When a platform changes its native file layout or plugin API, update that adapter and rerun Evals; do not redesign the Business Core unless the business behavior actually needs to change.
