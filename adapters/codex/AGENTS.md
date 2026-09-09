# Codex Adapter

This adapter is intentionally thin. Do not duplicate business logic here.

When operating this repository in Codex:
1. Resolve `REPO_ROOT` as the root of the currently opened/cloned repository. Do not hard-code or persist any machine-specific absolute path.
2. Follow `<REPO_ROOT>/AGENTS.md`.
3. Read `<REPO_ROOT>/core/MODEL_AGNOSTIC_RUNTIME.md`.
4. Use `<REPO_ROOT>/core/BUSINESS_KERNEL.md` for task reasoning and routing.
5. Load only relevant files from `<REPO_ROOT>/skills/`.
6. Use `<REPO_ROOT>/cases/` as abstract reasoning references, never as current customer facts.
7. Load `<REPO_ROOT>/knowledge/` and external/private customer memory only when the task requires them.
8. Use `<REPO_ROOT>/evals/` to regression-test changes to prompts, skills, adapters, or underlying models.

`<REPO_ROOT>` is a logical runtime placeholder, not a literal directory name. If the active repository root cannot be resolved reliably, ask the runtime/user to open or identify the repository rather than guessing a local path.

Machine-local paths may exist in temporary runtime state, but they must not become Business Memory, Company Knowledge, Golden Case content, or reusable adapter configuration.

Codex-specific behavior should remain limited to platform integration. Business behavior belongs in the core framework.
