# Platform Adapters

The repository follows **Generic Core First** while remaining RUNTONG-specific at the Company layer. No agent platform is the architectural center.

Adapters connect a target model/platform to the reusable Business AI Core. They must remain thin and must not duplicate business logic or RUNTONG company facts.

## Canonical documents
- `PLATFORM_ADAPTER_CONTRACT.md` — mandatory rules for every adapter
- `COMPATIBILITY_MATRIX.md` — platform capability / packaging comparison
- `generic/SYSTEM.md` — fallback entry for platforms without a native repository instruction format
- `codex/AGENTS.md` — current Codex-specific boot adapter

## Repository portability
All adapters resolve logical `REPO_ROOT` dynamically. Normal setup should be:

`Clone / Import / Install / Open → platform provides/discovers workspace root → REPO_ROOT resolves → agent runs`

Do not hard-code or persist local paths such as `D:\...`, `C:\Users\...`, `/Users/...`, or `/home/...` into reusable configuration.

## Canonical company context
The active company pointer is:

`<REPO_ROOT>/company/ACTIVE_COMPANY.yaml`

The formal RUNTONG Company Pack is:

`<REPO_ROOT>/company/packs/runtong/`

Adapters must load only the company files needed for the current task.

## Typical capability requirements
| Skill | Minimum capability | Helpful additional capability |
|---|---|---|
| customer-analysis | text input | image/file reading for screenshots, PDFs, PO documents |
| prospecting | external research/web when current research is requested | browser, structured business search |
| gap-strategy | text/context reasoning | knowledge retrieval |
| negotiation | text/context reasoning | calculator/data tools for detailed models |
| business-writing | text generation | customer-memory retrieval |
| factory-bridge | text/context reasoning | file/image reading for drawings/specs |
| risk-guard | text/context reasoning | authoritative web/knowledge access when verification is required |
| project-next-action | text/context reasoning | calendar/task/project tools if actions are to be executed |
| company-knowledge-curation | file/text reasoning + write capability for formal updates | PDF/Office/image reading and repository/file tools |

## Company maintenance rule
Normal business dialogue may generate a `COMPANY_UPDATE_CANDIDATE`, but the adapter must not bypass the canonical review lifecycle:

`candidate → operator decision → pending → curation → review → formal pack update`

## Degradation rule
If a required capability is unavailable:
- state the limitation when material;
- complete the reliable portion;
- do not fabricate external research, document contents, memory, tool results, or completed actions.

## Production rule
Technical compatibility is not production validation. A target harness should reach A4 only after running the canonical business, company-pack, and E2E evals.
