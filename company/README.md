# RUNTONG Company Workspace

`company/` is the canonical workspace for RUNTONG / WAYEAH company-specific information.

Unlike the generic `B2B-Trade-Business-AI` repository, this repository already ships with the formal RUNTONG Company Pack. Zero-start onboarding is therefore not required.

## Structure
- `ACTIVE_COMPANY.yaml` — runtime pointer to the preloaded RUNTONG pack
- `packs/runtong/` — confirmed formal RUNTONG / WAYEAH Company Pack
- `inbox/` — new raw company materials waiting for review
- `pending/` — operator-approved company-update candidates waiting for formal curation
- `COMPANY_PACK_SPEC.md` — pack structure and scope rules
- `MAINTENANCE.md` — company update workflow

## Normal runtime
Load only the Company Pack files materially relevant to the current task. Do not inject the entire company pack into every conversation.

## Update paths
### A. New source materials
New company PDF/PPT/Word/Excel/certificate/catalogue/etc. → `inbox/` → `company-knowledge-curation` → review → update formal pack.

### B. Business conversation patch
Normal business dialogue reveals a likely durable company fact → Core marks `COMPANY_UPDATE_CANDIDATE` → operator decides whether to review → `pending/` → curation → formal update.

### C. Explicit correction
Operator explicitly says an existing company fact has changed and asks to update it → curation compares against current pack → review → formal update / supersession.

## Safety
Do not write customer-specific/project-specific commercial facts into the Company Pack merely because they appear in business conversation.

`inbox/` and `pending/` are runtime working areas and are ignored by Git by default. The formal RUNTONG Company Pack remains version-controlled in this repository.
