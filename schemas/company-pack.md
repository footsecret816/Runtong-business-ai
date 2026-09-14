# Company Pack Data Contract

A Company Pack is the reviewed source of reusable company knowledge.

## Identity
- `company_id`
- `company_name`
- `version`
- `status`
- `canonical_path`

## Fact record expectations
Material facts should preserve, when relevant:
- statement
- scope: company / factory / product / project / customer
- evidence state: CONFIRMED / INFERRED / UNKNOWN / TO_CONFIRM / SUPERSEDED
- source/provenance
- confirmation date or update record when available
- superseded-by / supersedes relationship when a fact changes

## Admission rule
A fact belongs in Company Knowledge only when it is sufficiently stable and reusable across future business and its scope is clear.

Customer/project-specific prices, POs, special MOQ, temporary supplier quotes, one-off approvals, rush delivery arrangements, and project-specific payment exceptions belong in customer/project context or memory instead.

## Write-back rule
Formal Company Pack write-back requires operator confirmation after curation. Lightweight conversation detection may create candidates, but candidates are not formal company facts.
