# Case Library

The case library teaches transferable business patterns. It must not contain identifiable customer information.

## Structure
- `golden/` — approved abstract examples of strong business reasoning and communication.
- `anti-patterns/` — common failure modes to avoid.
- `CASE-EXTRACTION-GUIDE.md` — rules for turning real projects into reusable, non-identifying cases.

## Retrieval rule
Retrieve cases by **business pattern**, not by product name or exact wording. Prefer similarity in:
1. conflict/tension type,
2. business objective,
3. project stage,
4. customer relationship type,
5. constraint type.

Product category is secondary unless technically material.

## Golden case index
| ID | Business pattern | Typical stage | Main skills | Tags |
|---|---|---|---|---|
| GC-NEG-001 | Hard production MOQ vs small trial order | quotation / negotiation | gap-strategy, negotiation, business-writing | MOQ, trial, structural constraint |
| GC-TECH-002 | Internal technical data vs formal third-party report | development / compliance | gap-strategy, risk-guard, business-writing | report gap, evidence form, compliance |
| GC-NEG-003 | Annual volume vs per-order pricing basis | quotation / negotiation | negotiation, gap-strategy | annual volume, price basis, order quantity |
| GC-FUP-004 | Mature project stalled near decision | negotiation / decision | gap-strategy, business-writing | follow-up, silence, decision reopening |
| GC-DEV-005 | Close sample deviation vs extra tooling | development / sampling | factory-bridge, gap-strategy, business-writing | material difference, tooling, acceptance |
| GC-RISK-006 | IP-sensitive reference design | inquiry / development | risk-guard, prospecting, business-writing | IP, reference design, safer alternative |
| GC-PRO-007 | Broad catalogue + low target price + unclear fit | prospecting / inquiry | prospecting, customer-analysis, business-writing | qualification, catalogue, target price |
| GC-ORD-008 | Mixed SKU/pack order vs production MOQ | order confirmation | customer-analysis, gap-strategy, negotiation | pack conversion, colors, batch MOQ |
| GC-REL-009 | Natural tone for existing-customer update | any ongoing project stage | business-writing | existing customer, concise update, tone |
| GC-TECH-010 | Irregular shape cannot be defined by simple 2D dimensions | technical development | factory-bridge, gap-strategy | geometry, false precision, physical reference |
| GC-NEG-011 | Price negotiation near the commercial floor | late negotiation | negotiation, gap-strategy, business-writing | price floor, final review, relationship |
| GC-RISK-012 | Production before deposit as controlled exception | order / production | negotiation, risk-guard, project-next-action | deposit, exception, approval, delivery |

## Anti-pattern index
| ID | Failure mode | Why it matters |
|---|---|---|
| AP-001 | Common Business AI failures | General factual/business-quality failures |
| AP-002 | Over-official customer-service tone | Makes real B2B communication robotic and indirect |
| AP-003 | Over-structured simple tasks | Makes the framework rigid and triggers unnecessary skills |

## Case format
Each reusable case should contain:
1. Scenario
2. Business tension / gap
3. Confirmed facts when needed
4. Recommended reasoning pattern
5. Strategy
6. Communication pattern
7. Anti-patterns
8. Transferable principle

## Abstraction rules
Remove or generalize:
- customer names and contacts,
- email addresses,
- PO/SKU identifiers when identifying,
- confidential exact prices or payment records,
- unnecessary exact dates,
- supplier identities,
- any detail that is not needed to preserve the business lesson.

Cases are references, never evidence for a current project.