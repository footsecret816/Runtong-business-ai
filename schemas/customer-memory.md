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

## Memory update rule
Store deltas, not entire conversations. A memory update should capture only durable facts, decisions, preferences, unresolved issues, and next actions.

## Privacy rule
Real customer memory should live in a separate private data layer or repository when possible. Never copy raw customer memory into the reusable golden case library.
