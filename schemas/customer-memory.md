# Customer Memory Schema

This file defines structure only. Reusable framework repositories should not contain real customer memory by default.

## Recommended structure

### Customer profile
- customer_id
- account_name
- country/market
- customer_type
- channel
- relationship_status

### Projects
For each project:
- project_id
- product/category
- stage
- confirmed_facts
- commercial_terms
- technical_requirements
- customer_preferences
- open_issues
- decisions
- next_actions
- superseded_facts

### Fact labels
- `CONFIRMED`
- `PROJECT_CONFIRMED`
- `COMPANY_GENERAL`
- `FACTORY_SPECIFIC`
- `USER_ASSUMPTION`
- `AI_INFERENCE`
- `TO_CONFIRM`
- `SUPERSEDED`

## Durable memory record
Important stored facts should carry enough provenance to prevent old or inferred information from silently becoming current truth:
- `value`
- `label`
- `source` — e.g. customer message, user statement, factory reply, document, or AI inference
- `recorded_at` — when the memory was captured
- `effective_at` — when the fact became applicable, if known
- `status` — active, to-confirm, or superseded
- `supersedes` / `superseded_by` — when a later fact replaces an earlier one

## Memory update rule
Store deltas, not entire conversations. Capture only durable facts, decisions, preferences, unresolved issues, and next actions.

Do not overwrite conflicting information silently. Preserve the conflict until a reliable source resolves it. Newer information does not automatically override older information unless the newer source actually changes or supersedes the prior fact.

## Privacy rule
Real customer memory should live in a separate private data layer or repository when possible. Never copy raw customer memory into the reusable golden case library.
