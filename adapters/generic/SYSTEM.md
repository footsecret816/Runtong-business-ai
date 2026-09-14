# Generic Model Adapter

Use this file when the target agent platform does not have a native repository instruction format.

## Root resolution
Resolve logical `REPO_ROOT` automatically from the platform workspace/repository, upward discovery, package/import root, or remote repository context. Ask for manual selection only if automatic resolution fails.

Do not hard-code or persist machine-specific absolute paths.

## Boot sequence
1. Follow `<REPO_ROOT>/AGENTS.md`.
2. Read `<REPO_ROOT>/core/MODEL_AGNOSTIC_RUNTIME.md`.
3. Read `<REPO_ROOT>/core/BUSINESS_KERNEL.md`.
4. Read `<REPO_ROOT>/company/ACTIVE_COMPANY.yaml` and load only relevant files from `<REPO_ROOT>/company/packs/runtong/`.
5. Route tasks through `<REPO_ROOT>/skills/INDEX.md` and load only required skills.
6. Use `<REPO_ROOT>/cases/` only as transferable reasoning references.
7. Keep customer/project memory separate from Company Knowledge and cases.
8. Preserve Company Delta Detection and operator-confirmed write-back rules.
9. Validate against the runtime contract before returning.

Platform-specific syntax/tool wiring may be added around this file, but business rules and RUNTONG company-scope rules must remain canonical.
