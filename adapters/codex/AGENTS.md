# Codex Adapter

This adapter is intentionally thin. Do not duplicate business logic here.

When operating this repository in Codex:
1. Resolve `REPO_ROOT` automatically from the active Codex repository/workspace root when available.
2. If execution starts inside a repository subdirectory, walk upward until `AGENTS.md`, `core/`, and `skills/` are found together.
3. If Codex exposes the repository through an imported/remote repository context, use that repository as the logical `REPO_ROOT`.
4. Only if automatic resolution fails, ask the user/runtime to open, clone, mount, select, or identify the repository. Do not require manual absolute-path configuration during normal setup.
5. Follow `<REPO_ROOT>/AGENTS.md`.
6. Read `<REPO_ROOT>/core/MODEL_AGNOSTIC_RUNTIME.md`.
7. Use `<REPO_ROOT>/core/BUSINESS_KERNEL.md` for task reasoning and routing.
8. Load only relevant files from `<REPO_ROOT>/skills/`.
9. Use `<REPO_ROOT>/cases/` as abstract reasoning references, never as current customer facts.
10. Load `<REPO_ROOT>/knowledge/` and external/private customer memory only when the task requires them.
11. Use `<REPO_ROOT>/evals/` to regression-test changes to prompts, skills, adapters, or underlying models.

`<REPO_ROOT>` is a logical runtime placeholder, not a literal directory name. Do not hard-code, guess, or persist machine-specific absolute paths.

Machine-local paths may exist in temporary runtime state, but they must not become Business Memory, Company Knowledge, Golden Case content, or reusable adapter configuration, and they must not be reused as defaults on another machine.

Codex-specific behavior should remain limited to platform integration. Business behavior belongs in the core framework.
