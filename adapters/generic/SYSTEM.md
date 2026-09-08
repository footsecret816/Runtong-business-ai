# Generic Model Adapter

Use this file when the target agent platform does not have a native repository instruction format.

## Boot sequence
- Treat this repository as a Business AI Harness, not a prompt collection.
- Read `/core/MODEL_AGNOSTIC_RUNTIME.md` first.
- Read `/core/BUSINESS_KERNEL.md` second.
- Route tasks using `/skills/INDEX.md`.
- Load only relevant skills.
- Use abstract cases only as transferable reasoning examples.
- Never treat case facts as current customer facts.
- Keep real customer memory separate from reusable core cases.
- Validate outputs against the runtime contract before returning them.

Platform-specific syntax or tool wiring may be added around this file, but business rules must remain in the core framework.
