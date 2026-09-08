# Platform Adapter & Capability Boundary

Adapters connect the model/platform to the reusable Business AI core. They must remain thin and must not duplicate business logic.

## Two separate questions
When evaluating a target platform, distinguish:
1. **Model capability** — reasoning, language, long-context understanding, instruction following.
2. **Harness capability** — web access, file reading, image/PDF handling, repository access, memory/database access, tool calling.

A strong model cannot execute a skill that depends on tools the harness does not provide.

## Typical capability requirements
| Skill | Minimum capability | Helpful additional capability |
|---|---|---|
| customer-analysis | text input | image/file reading for screenshots, PDFs, PO documents |
| prospecting | external research/web access when current account research is requested | browser, structured business search |
| gap-strategy | text/context reasoning | knowledge retrieval |
| negotiation | text/context reasoning | calculator/data tools when detailed commercial models are required |
| business-writing | text generation | customer-memory retrieval |
| factory-bridge | text/context reasoning | file/image reading for drawings/specs |
| risk-guard | text/context reasoning | authoritative web/knowledge access for current rules when verification is required |
| project-next-action | text/context reasoning | calendar/task/project tools if actions are to be executed |

## Degradation rule
If a required capability is unavailable:
- state the limitation,
- complete the portion that can be done reliably,
- do not fabricate external research, document contents, memory, or tool results.

## Adapter rule
A platform-specific adapter may define boot syntax, tool wiring, context-loading instructions, and file conventions. It must point back to the canonical core/skills/cases rather than copying them.

## Portability target
Switching model/platform should require adapter/tool changes, not rewriting the business methodology.