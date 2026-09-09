# Platform Adapters

The repository follows **Generic Core First**. No agent platform is the architectural center.

Adapters connect a target model/platform to the reusable Business AI Core. They must remain thin and must not duplicate business logic.

## Canonical documents

- `PLATFORM_ADAPTER_CONTRACT.md` — mandatory rules for every platform adapter
- `COMPATIBILITY_MATRIX.md` — current platform capability / packaging comparison
- `generic/SYSTEM.md` — fallback entry for platforms without a native repository instruction format
- `codex/AGENTS.md` — current Codex-specific boot adapter

Additional native adapters should be implemented only when that platform is actually going to be used.

## Repository portability

All adapters must resolve the active repository root dynamically as logical `REPO_ROOT`.

### Normal user experience

The expected setup is zero-config for local paths:

`Clone / Import / Install / Open → platform provides or discovers workspace root → REPO_ROOT resolves automatically → agent runs`

Users should not normally be asked to copy or type a local absolute repository path.

Use this priority:
1. platform-provided repository / workspace / project root;
2. upward discovery from the current working directory until `AGENTS.md`, `core/`, and `skills/` are found together;
3. platform-provided plugin/package/install root;
4. logical remote-repository root when using connector/remote repository context;
5. manual open/mount/clone/select/identify only as the final fallback.

The framework must work regardless of where a user clones, mounts, imports, or installs the repository. A local path such as `D:\AI\Runtong-business-ai`, `E:\Work\BusinessAI`, or `/Users/name/projects/Runtong-business-ai` is environment-specific runtime state, not canonical configuration.

Adapters must not hard-code, guess, or persist machine-specific absolute paths into reusable agent instructions, Business Memory, Company Knowledge, Golden Cases, or shared configuration.

All canonical repository references should resolve relative to `REPO_ROOT`.

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

- state the limitation when material;
- complete the portion that can be done reliably;
- do not fabricate external research, document contents, memory, tool results, or completed actions.

## Adapter rule

A platform-specific adapter may define boot syntax, tool wiring, context-loading instructions, memory bridges, permissions, and file conventions. It must point back to the canonical Core / Skills / Cases / Company Packs rather than copying them.

## Production rule

A platform being technically compatible does not mean it is production-validated. Use the readiness levels in `PLATFORM_ADAPTER_CONTRACT.md`; production validation requires the target model/harness to pass the canonical Evals and E2E acceptance.

## Portability target

Switching model/platform or moving the repository to another computer/path should require no business-logic rewrite and, under normal platform operation, no manual local-path configuration.
