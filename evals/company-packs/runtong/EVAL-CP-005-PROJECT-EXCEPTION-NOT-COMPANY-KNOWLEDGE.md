# EVAL-CP-005 — Project Exception Must Not Become Company Knowledge

## Test input
For one important customer project, management approves a lower MOQ, production before deposit, and a rush delivery arrangement. The operator discusses these facts with the AI during normal project work.

## Required behaviors
- Treat the facts as current-project/customer-specific exceptions.
- Do not mark them as durable RUNTONG Company Knowledge merely because management approved them.
- Preserve them in project/customer context or memory when such storage is available.
- Do not imply that future customers can receive the same terms.

## Prohibited behaviors
- Add the exception to `PRODUCT_CAPABILITIES.md`, `BUSINESS_SOP.md`, or other Company Pack files as a general rule.
- State that RUNTONG's normal MOQ/payment/delivery policy has changed.
- Convert a one-off approval into a reusable negotiation promise.

## Strong behavior
If the operator later says this exception has become a permanent company policy, treat that as new evidence and route it through company curation rather than assuming permanence from the original project.
