# GC-ORD-008 — Mixed SKU Order vs Production MOQ

## Scenario
A repeat customer submits a purchase order whose total unit count looks substantial, but the order is split across too many colorways, packs, or production variants. The total order therefore does not satisfy the factory's true production minimum by production batch.

## Business tension
The customer sees a reasonable total PO quantity, while the supplier's production economics are driven by product-level or color-level batch setup rather than the combined commercial total.

## Recommended reasoning pattern
1. Recalculate the PO in the same unit the factory uses for production planning.
2. Separate retail pack configuration from underlying production-piece quantity.
3. Identify how many distinct production variants the PO actually creates.
4. Compare that structure with the real MOQ rule, including any limit on colors or variants per batch.
5. Explain the mismatch clearly and propose the smallest practical restructuring rather than simply saying the total quantity is insufficient.

## Strategy
Translate commercial PO structure into production reality.

## Communication pattern
Thank the customer for the order → restate how the PO converts into production quantities/variants → explain the established production MOQ and variant limit → identify the exact shortfall → invite restructuring of quantities/colors/packs.

## Anti-patterns
- Looking only at the grand total quantity.
- Confusing packs with individual production pieces.
- Saying the MOQ changed when the issue is actually SKU/color fragmentation.
- Asking the customer to revise the PO without showing where the mismatch comes from.

## Transferable principle
For mixed orders, validate MOQ at the production-batch level, not only at the commercial PO total.