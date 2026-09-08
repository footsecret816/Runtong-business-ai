# Company Pack: RUNTONG & WAYEAH

This company pack contains company-specific knowledge for the active RUNTONG / WAYEAH business context. It must not be treated as universal framework knowledge.

## Load rule
Load this pack only when the active company is RUNTONG / WAYEAH or when the user explicitly asks about this company.

## Fact-scope rule
- Company-general facts are `COMPANY_GENERAL`.
- Product, factory, certification, MOQ, lead-time, or test capability for a specific project must be confirmed separately.
- Do not convert a company-general capability into a project promise.
- Do not treat extended/outsource project categories as equal to core product categories.

## Core files
- `COMPANY_PROFILE.md` — identity, positioning, core strengths, business model
- `PRODUCT_CAPABILITIES.md` — portfolio overview and customization scope
- `SUPPLY_CHAIN_MODEL.md` — supplier/factory operating model and operational capabilities
- `COMPLIANCE_BOUNDARIES.md` — certification, testing, claim, audit and IP boundaries
- `MARKETS_AND_CUSTOMERS.md` — target markets, customer types, acquisition channels
- `BUSINESS_SOP.md` — internal workflow from inquiry to after-sales

## Product-detail files
Load only when the active product/category requires them:
- `products/INSOLES.md`
- `products/SHOE_CARE.md`
- `products/FOOT_CARE_AND_SPORTS.md`

## Typical loading examples
- new insole prospect → COMPANY_PROFILE + MARKETS_AND_CUSTOMERS + PRODUCT_CAPABILITIES + products/INSOLES
- shoe-care inquiry → PRODUCT_CAPABILITIES + products/SHOE_CARE
- certification question → COMPLIANCE_BOUNDARIES + project-specific evidence
- supplier/factory question → SUPPLY_CHAIN_MODEL + relevant factory-specific facts
- internal project planning → BUSINESS_SOP + project context

## Source
Derived from the user-provided internal document: `RUNTONG & WAYEAH 公司背景与内部信息汇总 V2.1`.
