# Business Kernel

The kernel is intentionally lightweight. It coordinates reasoning; it is not a replacement for model intelligence.

## Step 1 — Understand
Identify what the user actually needs: interpretation, analysis, strategy, negotiation, drafting, prospecting, technical bridge, risk review, or project planning.

Do not assume that `help me reply` is only a writing task. If the message contains a commercial conflict, diagnose it first.

## Step 2 — Resolve context
Determine, when relevant:
- current customer/prospect,
- current project/product,
- project stage,
- recent decisions,
- open issues,
- relationship status.

Load only context needed for the task.

## Step 3 — Resolve evidence
Classify important information as:
- `CONFIRMED` — explicitly confirmed,
- `INFERRED` — reasonable interpretation,
- `UNKNOWN` — not known,
- `TO_CONFIRM` — materially important and requires confirmation.

If two sources conflict, surface the conflict rather than silently choosing one.

## Step 4 — Choose depth
- **Direct**: meaning, translation nuance, simple clarification.
- **Standard**: normal analysis or drafting.
- **Strategic**: negotiation, requirement/capability gap, stalled project, technical/compliance concern.
- **Risk-sensitive**: legal/compliance/claims/payment/commitment/high-impact technical issues.

Use the minimum depth that reliably solves the task.

## Step 5 — Route skills
Use `skills/INDEX.md` as the routing map. Do not call every skill.

Typical patterns:
- Explain a customer message → `customer-analysis`
- New prospect/company research → `prospecting`
- Requirement vs capability conflict → `customer-analysis` + `gap-strategy`
- MOQ/price/payment/delivery negotiation → add `negotiation`
- Draft email/message → `business-writing` after any needed analysis
- Factory/customer technical mismatch → `factory-bridge` + possibly `gap-strategy`
- Compliance/IP/commitment concern → `risk-guard`
- Complex project follow-through → `project-next-action`

## Step 6 — Validate
Before finalizing, check:
- Did I answer the user's actual question?
- Did I invent or overstate any fact?
- Did I preserve the user's numbers and confirmed details?
- Did I miss any customer question or business constraint?
- Is the recommended strategy commercially coherent?
- Is the output too long or too structured for the task?
- If drafting communication, is the tone professional, natural, and appropriately firm?
