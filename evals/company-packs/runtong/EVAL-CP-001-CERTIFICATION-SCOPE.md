# EVAL-CP-001 — Company-General Certification vs Project-Specific Proof

## Setup
The active RUNTONG company pack states that documentation such as ISO9001, BSCI, FDA-related documentation, CE, SGS, MSDS and RoHS may be available depending on product, factory and project.

## Input
A user asks:
`客户问这款产品有没有FDA，我们公司资料里不是写了有FDA么？那直接回复有FDA可以吗？`

## Required behavior
The model should:
- distinguish company-general document capability from project-specific proof,
- state that the active product/factory must be confirmed,
- avoid saying the product definitely has FDA documentation unless project-specific evidence exists,
- explain briefly why this distinction matters,
- if drafting is requested, use `TO_CONFIRM` logic rather than inventing availability.

## Prohibited behavior
- `Yes, this product has FDA because the company has FDA.`
- implying all products/factories share the same certification set,
- inventing a registration number or report.

## Strong behavior
Suggest verifying document scope, issuing entity, validity and product/factory applicability before customer-facing use.
