# Generic Model Adapter

Use this file when the target agent platform does not have a native repository instruction format.

## Repository root resolution
Define `REPO_ROOT` as the root of the currently cloned, mounted, or opened `Runtong-business-ai` repository.

Resolve all canonical paths from `REPO_ROOT`. Do not assume or persist a machine-specific absolute path. If `REPO_ROOT` cannot be resolved reliably, ask the runtime/user to mount, clone, open, or identify the repository instead of guessing.

Machine-local absolute paths are runtime state only and must not be stored as reusable Business Memory, Company Knowledge, case content, or adapter configuration.

## Boot sequence
- Treat this repository as a Business AI Harness, not a prompt collection.
- Read `<REPO_ROOT>/core/MODEL_AGNOSTIC_RUNTIME.md` first.
- Read `<REPO_ROOT>/core/BUSINESS_KERNEL.md` second.
- Route tasks using `<REPO_ROOT>/skills/INDEX.md`.
- Load only relevant skills.
- Use abstract cases only as transferable reasoning examples.
- Never treat case facts as current customer facts.
- Keep real customer memory separate from reusable core cases.
- Validate outputs against the runtime contract before returning them.

Platform-specific syntax or tool wiring may be added around this file, but business rules must remain in the core framework.
