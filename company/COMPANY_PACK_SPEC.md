# Company Pack Specification

A Company Pack stores confirmed, reusable company-specific knowledge. In this repository the active formal pack is `company/packs/runtong/`.

## Required structure
- `PACK.yaml` — pack identity, version, status, source/update metadata
- `INDEX.md` — loading rules and scope boundaries
- `COMPANY_PROFILE.md` — company identity, positioning, business model, durable strengths
- `PRODUCT_CAPABILITIES.md` — product portfolio and customization capabilities
- `SUPPLY_CHAIN_MODEL.md` — supplier/factory collaboration model and manufacturing boundaries
- `COMPLIANCE_BOUNDARIES.md` — certificates, testing, regulatory, claim, audit, and IP boundaries
- `MARKETS_AND_CUSTOMERS.md` — target markets, channels, customer types
- `BUSINESS_SOP.md` — stable internal business workflow
- `SOURCES.md` — provenance, confirmation, and supersession records
- `products/` — more detailed product/category knowledge loaded only when relevant

## Fact-scope states
Use the narrowest appropriate scope:
- company-level
- factory-level
- product-level
- project-level
- customer-level

Project/customer facts normally belong outside the Company Pack unless they establish a durable broader capability.

## Evidence states
Important facts should be treated as one of:
- `CONFIRMED`
- `INFERRED`
- `UNKNOWN`
- `TO_CONFIRM`
- `SUPERSEDED`

Only reviewed, supported information should be written as active Company Knowledge.

## Update rule
Formal Company Pack changes must preserve:
- source/provenance;
- scope;
- conflict notes;
- supersession history when relevant;
- operator confirmation;
- version/update metadata.

## Boundary
Never use the Company Pack as a place to accumulate customer-specific prices, POs, one-off approvals, project MOQ, temporary quotes, or rush-delivery exceptions.
