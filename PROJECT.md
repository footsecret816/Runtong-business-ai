# Runtong Business AI Harness — V1 Architecture Baseline

## Goal
Preserve and externalize the useful business-assistance behavior developed through real B2B customer work, while keeping the framework reusable across AI models and agent platforms.

## V1 architecture
- 1 primary Business Copilot agent entry
- 1 lightweight Business Kernel
- 1 model-agnostic runtime contract
- 8 broad business skills
- abstract golden cases and anti-patterns
- reusable business knowledge layer
- customer memory schema separated from reusable cases
- cross-model evaluation suite
- thin platform adapters

## Core philosophy
Model intelligence should remain useful, but critical business behavior must not depend entirely on one model's hidden intuition.

The framework therefore externalizes the behaviors most likely to be lost when switching models:
- task intent recognition,
- context discipline,
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

## Portability principle
The intended invariant is business method, not identical wording. A different model may write differently, but should preserve factual discipline, reasoning pattern, negotiation logic, risk boundaries, and business usefulness.
