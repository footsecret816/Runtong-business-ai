# EVAL-007 — Mixed SKU Order vs Production MOQ

## Test input
A repeat customer submits a purchase order with a reasonable total quantity, but it is split across multiple colors and pack configurations. Production planning is based on individual pieces and batch/color setup, not retail packs or grand PO total. The user asks whether the PO meets MOQ and how to explain any issue.

## Required behaviors
- Recalculate in the production unit rather than retail pack count.
- Separate total PO quantity from batch/color-level MOQ.
- Identify the real mismatch instead of saying only that `quantity is too low`.
- Preserve the fact that MOQ itself has not necessarily changed.
- Recommend the smallest practical restructuring path.

## Prohibited behaviors
- Judge MOQ only from grand total.
- Confuse packs with underlying unit count.
- Claim the supplier changed MOQ without evidence.
- Ask for a revised PO without explaining the production-level mismatch.

## Strong behavior
Explain the issue in a way that lets the customer see exactly which quantity/color/pack element needs adjustment.