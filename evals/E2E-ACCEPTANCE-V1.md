# V1 End-to-End Acceptance — Architecture-Level Simulation

## Scope
This acceptance run validates the V1 architecture on the current model by simulating five realistic business workflows through:

`Kernel → relevant Skills → Cases / Company Pack / Memory rules → output validation`

This is **not** an independent DeepSeek / Claude / Gemini run. Cross-model acceptance still requires running the same cases through those target harnesses later.

## Result summary

| Test | Scenario | Expected route | Result |
|---|---|---|---|
| E2E-A | New prospect development | prospecting + relevant company/product knowledge + business-writing | PASS |
| E2E-B | Trial quantity below hard MOQ | customer-analysis + gap-strategy + negotiation + business-writing | PASS |
| E2E-C | Sample/material deviation with tooling implication | factory-bridge + gap-strategy + project-next-action + business-writing | PASS |
| E2E-D | Simple customer sentence interpretation | customer-analysis only | PASS |
| E2E-E | New project fact conflicts with old memory + company-general compliance claim | source precedence + risk-guard + relevant company knowledge | PASS after core fix |

No critical-fail behavior was observed in the architecture-level simulation.

---

## E2E-A — New Prospect Development

### Input pattern
A European pharmacy / foot-care retailer visibly sells heel cushions, gel pads and small foot-care accessories. No full-length functional insole is visible in the supplied evidence. User asks whether the account is worth developing and how to approach it.

### Expected routing
- `prospecting`
- company pack: profile + markets/customers
- on-demand insole / foot-care knowledge
- `business-writing` only if outreach copy is requested

### Required behavior
- classify the account by channel and visible product mix,
- describe the apparent assortment gap as an inference (`based on the visible range`), not a proven absence,
- recommend a small number of relevant entry angles,
- avoid sending the whole catalogue by default,
- avoid inventing purchase volume, supplier relationships or private-label activity,
- produce outreach centered on the prospect's product structure rather than a generic company introduction.

### Simulated result
PASS. The framework supports targeted development without converting incomplete website evidence into certainty.

### Score
Task understanding 2 / Fact discipline 2 / Business diagnosis 2 / Strategy 2 / Risk 2 / Communication 2 / Response depth 2 / Advancement value 2.

---

## E2E-B — Trial Order Below Hard MOQ

### Input pattern
Customer wants a small trial quantity. Supplier confirms a materially higher hard production MOQ caused by automated-line / material-batch economics. User asks how to reply.

### Expected routing
- `customer-analysis`
- `gap-strategy`
- `negotiation`
- `business-writing`

### Required behavior
- identify the real conflict as customer inventory-risk vs structural production minimum,
- distinguish a hard operational constraint from an arbitrary policy,
- acknowledge the customer's trial-order logic,
- explain the structural basis concisely,
- do not invent exact cost differences,
- do not promise an MOQ exception without approval,
- remain cooperative and leave a practical path forward.

### Simulated result
PASS. The architecture correctly prevents direct translation and routes the task through diagnosis before drafting.

### Score
2 / 2 / 2 / 2 / 2 / 2 / 2 / 2.

---

## E2E-C — Material / Sample Deviation and Tooling Implication

### Input pattern
A material close to the customer's sample is found. It is slightly heavier because the weave is denser; current stock color differs but bulk can be dyed to the target Pantone. The surface emboss pattern is smaller than the customer's sample; exact duplication would require additional tooling. Price is still being checked. User asks for a customer update.

### Expected routing
- `factory-bridge`
- `gap-strategy`
- `project-next-action`
- `business-writing`

### Required behavior
- translate factory information into customer-usable language,
- state measurable differences precisely,
- separate confirmed difference from subjective quality assessment,
- keep unconfirmed price as `TO_CONFIRM`,
- explain the exact-match tooling consequence without overstating necessity or cost,
- ask the customer to accept the current pattern or confirm whether exact matching is required,
- define the next sample / confirmation step.

### Simulated result
PASS. The framework preserves the technical difference without sounding defensive and turns the gap into a decision request.

### Score
2 / 2 / 2 / 2 / 2 / 2 / 2 / 2.

---

## E2E-D — Simple Interpretation

### Input pattern
Customer says: `Please update the date on the final artwork and send me the AI file.` User asks what it means.

### Expected routing
- `customer-analysis` only
- Direct depth

### Required behavior
Explain simply that the customer wants the date updated on the final artwork and the revised AI file sent back. No negotiation, gap analysis, risk review, case lookup or large structured template is needed.

### Simulated result
PASS. The Kernel's minimum-depth rule and anti-pattern guidance are sufficient to avoid over-structuring.

### Score
Task understanding 2 / Fact discipline 2 / Communication 2 / Response depth 2. Other dimensions not applicable.

---

## E2E-E — Current Fact vs Old Memory + Compliance Scope

### Input pattern
Old customer memory says the active packaging is 4-pack. The user now explicitly confirms the project has changed to 8-pack. Separately, the company pack says FDA-related documentation may be available depending on product/factory/project, but there is no project-specific evidence confirming FDA coverage for this product. User asks the AI to prepare a customer-facing response.

### Expected behavior
- treat the latest explicit user correction (8-pack) as active project state,
- mark the old 4-pack memory as superseded for current-state reasoning,
- do not allow company-general FDA capability to become a project-specific FDA claim,
- if customer-facing compliance wording is requested, state only what is confirmed or mark document availability as needing confirmation.

### Issue found during acceptance
The repository already had fact labels, superseded memory fields, and general fact-scope rules, but the Kernel did not state the **active-project source precedence** strongly enough for weaker models.

### Fix applied
Updated:
- `core/MODEL_AGNOSTIC_RUNTIME.md`
- `core/BUSINESS_KERNEL.md`

to define project-state precedence and prevent old memory / company knowledge / cases from overriding a newer explicit user correction.

### Simulated result after fix
PASS.

### Score after fix
2 / 2 / 2 / 2 / 2 / 2 / 2 / 2.

---

## Acceptance conclusion

### Architecture status
**PASS WITH ONE FIX APPLIED**

The five workflows confirm that V1 can preserve the intended behavioral pattern:
- simple tasks remain simple,
- complex commercial issues are diagnosed before writing,
- new-customer development uses opportunity logic rather than generic catalogue pitching,
- technical factory information is converted into customer-safe decisions,
- project-specific facts remain above company-general knowledge and reusable cases,
- unsupported commercial / compliance commitments remain blocked.

### Remaining validation before cross-model claim
This acceptance run validates architecture logic on the current model only. It does **not** prove equivalent behavior on another model.

Before claiming compatibility with a target model/harness such as DeepSeek, run:
1. the 12 core benchmark cases,
2. the company-pack-specific evals,
3. these five E2E scenarios,
4. score using `evals/SCORING.md`,
5. reject any run with a critical fail.

### V1 merge recommendation
From an architecture perspective, V1 is suitable for merging to `main` after final repository-level review. Further case accumulation should be incremental rather than blocking V1.
