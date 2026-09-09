# Generic Model Adapter

Use this file when the target agent platform does not have a native repository instruction format.

## Repository root resolution
Define `REPO_ROOT` as the active repository/workspace root for this Business AI Harness.

Resolve it automatically in this order:
1. use the platform-provided repository / workspace / project root when valid;
2. if running inside a subdirectory, walk upward until `AGENTS.md`, `core/`, and `skills/` are found together;
3. if installed/imported as a plugin or package, use its platform-provided package/install root when the canonical structure is present;
4. if the platform provides remote repository context without a local clone, use that remote repository as the logical root;
5. only when all automatic methods fail, ask the runtime/user to open, mount, clone, select, or identify the repository.

Normal setup must not require users to type an absolute local path. Manual absolute-path entry is a last-resort fallback only.

Resolve all canonical paths from `REPO_ROOT`. Do not assume or persist a machine-specific absolute path. Machine-local paths are runtime state only and must not be stored as reusable Business Memory, Company Knowledge, case content, or adapter configuration.

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
