# Knowledge Layer

`knowledge/` stores reusable **non-company-specific** knowledge that may support business reasoning.

Examples:
- industry/category knowledge;
- market/channel knowledge;
- general material/process knowledge;
- general standards/regulatory explanations where appropriate.

## Important boundary
RUNTONG / WAYEAH company facts do not live here anymore.

The canonical company workspace is:

`company/`

The formal RUNTONG Company Pack is:

`company/packs/runtong/`

## Scope rules
- Company-general capability does not automatically apply to every product, factory, customer, or project.
- Product/factory/certification facts should remain narrowly scoped.
- Real customer histories, confidential prices, PO details, project-specific commercial terms, and one-off approvals belong in customer/project context or memory.
- Abstract cases belong in `/cases/`, not in the knowledge layer.

## Runtime principle
Load only the generic knowledge materially relevant to the active task. Do not use generic knowledge to override explicit current-project facts or the scoped RUNTONG Company Pack.
