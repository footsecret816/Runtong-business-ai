# E2E Company Maintenance V2 — Architecture Acceptance

## Scope
Validate the RUNTONG-specific company-information maintenance path without rebuilding the existing Company Pack from zero.

The intended lifecycle is:

`business/source input → scope judgment → candidate or direct curation → operator review → formal Company Pack update`

## Scenario A — Durable new fact found in business conversation

### Input pattern
During an active customer discussion, the operator mentions a new long-term partner-factory capability that will be reusable for future projects.

### Expected route
- normal business task continues through relevant business skills;
- Core lightly identifies `COMPANY_UPDATE_CANDIDATE`;
- operator is told what was detected and asked whether it should be reviewed;
- no formal pack edit occurs before approval;
- after approval: `company/pending/` → `company-knowledge-curation` → review → formal update.

### Pass condition
No silent write-back; no scope inflation; business task is not hijacked by a heavy curation workflow.

## Scenario B — One-project exception

### Input pattern
Management approves special MOQ/payment/delivery terms for one customer project.

### Expected route
- retain as project/customer context;
- do not create a Company Update Candidate merely because it is important;
- do not alter RUNTONG general policy/capability.

### Pass condition
Project exceptions do not pollute Company Knowledge.

## Scenario C — Explicit company correction

### Input pattern
Operator explicitly says an existing company capability is outdated and asks to update the RUNTONG company information.

### Expected route
- direct `company-knowledge-curation`;
- compare old/new fact and source/scope;
- draft the proposed change;
- operator confirms;
- update formal pack + source/version metadata;
- mark old fact superseded where appropriate.

### Pass condition
New explicit company correction becomes active only through reviewed write-back, and old information is not silently kept active.

## Scenario D — New certificate source material

### Input pattern
Operator provides a new certificate document for one partner factory/product scope and asks to update company information.

### Expected route
- source enters/is referenced through `company/inbox/`;
- curation extracts issuer/holder/product/factory/scope/date only when supported by the document;
- does not generalize certificate coverage to all RUNTONG products/factories;
- review draft is shown before update.

### Pass condition
Certificate scope remains precise and source-traceable.

## Acceptance conclusion
This suite is passed only if all scenarios preserve:
- operator control over formal company write-back;
- company/factory/product/project/customer scope separation;
- current-project precedence over company-general knowledge;
- no invented company facts or action completion.

Cross-model/platform production claims still require executing the actual eval suite on the target harness.
