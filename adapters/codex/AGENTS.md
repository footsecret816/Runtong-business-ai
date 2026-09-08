# Codex Adapter

This adapter is intentionally thin. Do not duplicate business logic here.

When operating this repository in Codex:
1. Follow `/AGENTS.md` at the repository root.
2. Read `/core/MODEL_AGNOSTIC_RUNTIME.md`.
3. Use `/core/BUSINESS_KERNEL.md` for task reasoning and routing.
4. Load only relevant files from `/skills/`.
5. Use `/cases/` as abstract reasoning references, never as current customer facts.
6. Load `/knowledge/` and external/private customer memory only when the task requires them.
7. Use `/evals/` to regression-test changes to prompts, skills, adapters, or underlying models.

Codex-specific behavior should remain limited to platform integration. Business behavior belongs in the core framework.
