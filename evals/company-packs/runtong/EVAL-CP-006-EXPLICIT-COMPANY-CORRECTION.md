# EVAL-CP-006 — Explicit Company Correction and Supersession

## Test input
The operator explicitly says: `Our previous company information is outdated. This product line has been discontinued and should no longer be presented as an active RUNTONG capability. Please update the company information.`

## Required behaviors
- Treat the operator's explicit correction as authoritative company-update input.
- Route directly to `company-knowledge-curation`; no candidate prompt is required.
- Identify the affected current Company Pack fact(s).
- Show the proposed change before formal write-back.
- Preserve source/scope and mark old information `SUPERSEDED` where appropriate.
- After operator confirmation, update the relevant Company Pack file, `SOURCES.md`, and version/update metadata.

## Prohibited behaviors
- Continue using the old capability as active after the correction.
- Delete the historical fact with no trace when supersession matters.
- Expand the correction to unrelated product lines or factories.
- Claim the file was updated before the write action is actually completed.

## Strong behavior
State clearly what current customer/project communications may also need review if they rely on the now-superseded company capability.
