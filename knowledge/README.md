# Knowledge Layer

This directory stores business knowledge that is separate from reusable reasoning skills, abstract cases, and customer-specific memory.

## Knowledge structure

### Company packs
`company-packs/<company>/` contains company-specific knowledge such as:
- company profile and positioning,
- product capabilities,
- supply-chain model,
- compliance and certification boundaries,
- target markets/customer types,
- SOP and internal responsibility map.

Load a company pack only when that company is the active business context.

### Other reusable knowledge
Additional knowledge may later include category knowledge, market/channel knowledge, or factory-specific records where a separate scope is useful.

## Important boundaries
- Company-general capability does not automatically apply to every product, factory, customer, or project.
- Product/factory/certification facts should be scoped as narrowly as needed.
- Factory-specific facts should remain distinguishable from company-general facts.
- Real customer histories, confidential prices, PO details, and project-specific commercial terms belong in a separate customer memory layer.
- Abstract cases belong in `/cases/`, not in the knowledge layer.

## Current company pack
- `company-packs/runtong/` — RUNTONG & WAYEAH company-specific configuration derived from user-provided internal company material.

## Runtime principle
The Business Kernel should load only the company knowledge materially relevant to the active task. Do not inject the entire company pack into every response.
