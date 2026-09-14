# Skill: Company Knowledge Curation

## Role
Optional plug-in skill for formal RUNTONG / WAYEAH company-knowledge maintenance.

Do not keep this skill permanently active during ordinary business conversations.

## Unique responsibility
Convert new company source materials, approved update candidates, or explicit company corrections into reviewed updates to the formal RUNTONG Company Pack.

## Inputs
- `company/inbox/` — new PDF/PPT/Word/Excel/images/certificates/catalogues/web exports or other source materials
- `company/pending/` — operator-approved `COMPANY_UPDATE_CANDIDATE` items detected during business work
- explicit operator corrections to existing company facts
- current formal pack under `company/packs/runtong/`

## Workflow
1. identify the proposed new/changed company information;
2. inspect the source or operator statement supporting it;
3. classify scope: company-level / factory-level / product-level / project-level / customer-level;
4. reject customer/project-only facts from long-term Company Knowledge unless they also prove a broader durable capability;
5. compare with the current RUNTONG Company Pack;
6. deduplicate and identify conflicts;
7. mark uncertain or scope-sensitive items `TO_CONFIRM`;
8. identify whether any old fact becomes `SUPERSEDED`;
9. produce a review draft showing proposed additions/changes/removals and the affected Company Pack files;
10. accept operator corrections and multi-round review;
11. only after explicit confirmation, write/update the formal Company Pack;
12. update `SOURCES.md`, `PACK.yaml` version/update metadata, and supersession notes as appropriate.

## Admission rule
A fact is suitable for the Company Pack when it is relatively stable, reusable across future RUNTONG business, correctly scoped, and supported by a source or explicit operator confirmation.

Typical suitable examples:
- company identity/positioning change;
- persistent product-line addition or removal;
- durable factory/supply-chain capability;
- new equipment or sustained capacity change;
- new certificate/audit status with clear scope;
- stable market/channel coverage change;
- an old company capability becoming invalid.

## Do not admit by default
- one customer's special price;
- one project's MOQ;
- one-off management approval;
- temporary supplier quote;
- one rush-delivery arrangement;
- project-specific payment exception;
- project-specific certification/test outcome;
- unconfirmed AI inference;
- customer/project confidential data that belongs in Memory.

## Scope caution
Certificates, testing capability, production capacity, factory capability, regulatory claims, and similar statements must preserve their actual scope.

A factory-specific fact must not become a company-wide claim without evidence. A company-general capability must not become a guaranteed current-project capability.

## Relationship with Core
The Core performs lightweight Company Delta Detection during ordinary business dialogue.

Core responsibility:
`notice → mark candidate → tell operator → ask whether to review`

Curation responsibility:
`verify → classify → compare → draft → operator review → formal update`

This separation prevents heavy background processing and prevents normal business conversations from silently rewriting the formal company record.
