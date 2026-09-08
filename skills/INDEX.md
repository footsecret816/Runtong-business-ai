# Skill Routing Index

Load only the skills needed for the current task.

| Skill | Use when | Common companions |
|---|---|---|
| `customer-analysis` | Interpret customer messages, requirements, intent, stage, confirmed/open items | gap-strategy, business-writing |
| `prospecting` | Research and develop a new prospect/account | business-writing, risk-guard |
| `gap-strategy` | Customer requirement conflicts with capability, evidence, timing, or project reality | negotiation, factory-bridge, risk-guard |
| `negotiation` | MOQ, price, payment, delivery, mold/sample fees, exclusivity, compensation | gap-strategy, business-writing |
| `business-writing` | Email, WhatsApp, LinkedIn, outreach, follow-up, revision | any analysis skill that should precede writing |
| `factory-bridge` | Translate customer requirements into factory questions or factory replies into customer-safe language | gap-strategy, risk-guard |
| `risk-guard` | Compliance, certification, IP, claims, technical promises, payment/commitment risk | gap-strategy |
| `project-next-action` | Turn analysis into owners, confirmations, open issues, and next steps | customer-analysis, gap-strategy |

## Routing rule
Route by business situation, not by keyword alone. A message mentioning `MOQ`, `price`, `test`, or `email` does not automatically require every related skill. First determine whether the task is explanation, review, drafting, conflict resolution, negotiation, research, risk review, or project planning.

For compound tasks, use the smallest sequence that resolves the business problem. Analysis skills should precede writing only when analysis is materially needed.

## Routing examples
- `What does this customer mean?` → customer-analysis
- `Can this reply work?` → customer-analysis + business-writing; add gap-strategy only if a real commercial conflict is present
- `Customer wants 5k, hard MOQ is 40k` → customer-analysis + gap-strategy + negotiation + business-writing
- `Research this retailer and suggest how to approach` → prospecting + business-writing
- `Factory says material MOQ makes exact request impossible` → factory-bridge + gap-strategy + business-writing
