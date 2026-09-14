# Codex Adapter

This adapter is intentionally thin. Do not duplicate business logic here.

When operating this repository in Codex:
1. Resolve `REPO_ROOT` from the active Codex repository/workspace root when available.
2. If execution starts inside a subdirectory, walk upward until `AGENTS.md`, `core/`, and `skills/` are found together.
3. If Codex exposes an imported/remote repository context, use it as logical `REPO_ROOT`.
4. Only if automatic resolution fails, ask the user/runtime to open, clone, mount, select, or identify the repository.
5. Follow `<REPO_ROOT>/AGENTS.md`.
6. Read `<REPO_ROOT>/core/MODEL_AGNOSTIC_RUNTIME.md` and `<REPO_ROOT>/core/BUSINESS_KERNEL.md`.
7. Read `<REPO_ROOT>/company/ACTIVE_COMPANY.yaml`; the default active pack is `<REPO_ROOT>/company/packs/runtong/`.
8. Load only relevant files from the RUNTONG Company Pack, relevant skills, and relevant cases.
9. Treat `company/inbox/` and `company/pending/` as runtime maintenance work areas.
10. Preserve the rule that normal business conversation can create a `COMPANY_UPDATE_CANDIDATE` but cannot silently rewrite the formal Company Pack.
11. Use `skills/company-knowledge-curation/` only for explicit company maintenance/review.
12. Use `<REPO_ROOT>/evals/` to regression-test changes or target models.

Machine-local paths may exist in temporary runtime state, but they must not become Business Memory, Company Knowledge, Golden Case content, or reusable adapter configuration.

Codex-specific behavior should remain limited to platform integration. Business behavior belongs in the core framework.
