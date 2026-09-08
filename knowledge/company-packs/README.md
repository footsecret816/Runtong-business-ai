# Company Packs

Company packs are swappable company-specific configurations for the model-agnostic Business AI Harness.

The reusable core (`core/`, `skills/`, `cases/`) should not need to change when a new company pack is introduced.

## Recommended pack structure

`company-packs/<company>/`

Recommended files:
- `INDEX.md` — load rule, source, fact-scope notes
- `COMPANY_PROFILE.md` — identity, positioning, business model, core strengths
- `PRODUCT_CAPABILITIES.md` — core categories, extended categories, customization scope
- `SUPPLY_CHAIN_MODEL.md` — manufacturing/sourcing model and project confirmation rules
- `COMPLIANCE_BOUNDARIES.md` — document, certification, claim, audit and IP boundaries
- `MARKETS_AND_CUSTOMERS.md` — target markets, channels, account types and acquisition logic
- `BUSINESS_SOP.md` — general workflow and internal responsibility map

## Scope hierarchy
Use the following hierarchy when reasoning:
1. current project/customer confirmed fact,
2. factory/product-specific confirmed fact,
3. active company-pack general fact,
4. reusable abstract case / general business knowledge.

A lower layer must not override a more specific confirmed fact.

## Loading principle
Do not load the entire company pack by default. Load only the files materially relevant to the task.

Examples:
- new prospect development → COMPANY_PROFILE + PRODUCT_CAPABILITIES + MARKETS_AND_CUSTOMERS
- certification question → COMPLIANCE_BOUNDARIES + project-specific evidence
- supplier/manufacturing question → SUPPLY_CHAIN_MODEL + factory-specific facts
- internal next-action planning → BUSINESS_SOP

## Portability boundary
A company pack may contain internal business information, but it should still avoid unnecessary customer-level confidential data. Real customer/project memory belongs in the separate memory layer.

## Evaluation
Company-specific behavior may be tested under `evals/company-packs/<company>/` without changing the core cross-model benchmark set.
