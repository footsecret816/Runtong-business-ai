# Runtong Business AI Harness — V1 Architecture Baseline

## Goal
Preserve and externalize the useful business-assistance behavior developed through real B2B customer work, while keeping the framework reusable across AI models and agent platforms.

## V1 architecture
- 1 primary Business Copilot entry
- 1 lightweight Business Kernel
- 1 model-agnostic runtime contract
- 8 broad business skills
- abstract Golden Cases and Anti-patterns
- reusable business knowledge layer with swappable Company Packs
- customer-memory schema separated from reusable cases
- cross-model evaluation suite
- thin, peer-level platform adapters

## Generic Core First

No platform is the architectural center.

The canonical Business AI consists of:
- Runtime Contract,
- Business Kernel,
- Skills,
- Cases,
- Company Packs,
- Customer Memory rules/schema,
- Evals.

Codex, Claude Code, DeepSeek Harness, WorkBuddy / CodeBuddy, Accio Work, and future platforms should connect through peer adapters. Platform-specific boot files, skill packaging, tool wiring, permissions, and memory bridges must not fork the canonical business methodology.

See:
- `adapters/PLATFORM_ADAPTER_CONTRACT.md`
- `adapters/COMPATIBILITY_MATRIX.md`

## Core philosophy
Model intelligence should remain useful, but critical business behavior must not depend entirely on one model's hidden intuition.

The framework therefore externalizes the behaviors most likely to be lost when switching models:
- task intent recognition,
- context discipline,
- source precedence and superseded-fact handling,
- fact vs inference separation,
- strategy-before-writing for complex issues,
- selective skill routing,
- business-risk boundaries,
- output-depth control,
- final self-check.

## Non-goals for V1
- Do not create many autonomous sub-agents.
- Do not encode every possible business situation as rigid if/else logic.
- Do not store raw identifiable customer histories in the reusable case library.
- Do not attempt to replace model intelligence with a large deterministic workflow.
- Do not prebuild native adapters for every possible platform before they are needed.

## Portability principle
The intended invariant is business method, not identical wording. A different model may write differently, but should preserve factual discipline, reasoning pattern, negotiation logic, risk boundaries, and business usefulness.

A platform is not considered production-validated merely because the repository can be imported. Native adapter implementation must be followed by the canonical benchmark and E2E suite.

## V1 acceptance status
Architecture-level end-to-end simulation completed on the current model using five realistic workflows:
- new prospect development,
- hard MOQ conflict,
- material/sample deviation,
- simple interpretation,
- conflicting project memory + company-general compliance scope.

Result: **PASS WITH ONE FIX APPLIED**.

The fix formalized active-project source precedence so newer explicit project facts cannot be overridden by older memory, company-general knowledge, or abstract cases.

See `evals/E2E-ACCEPTANCE-V1.md`.

This result does not prove equivalent behavior on DeepSeek, Claude, Gemini, or another model. Target models must run the same benchmark and E2E suite before production replacement.
