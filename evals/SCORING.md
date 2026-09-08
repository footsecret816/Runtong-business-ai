# Evaluation Scoring

Use this rubric to compare different models or agent harnesses on the same benchmark cases.

## Per-dimension score
Score each applicable dimension from 0 to 2.

### 0 — Fail
The output misses the required business logic, invents material facts, violates a prohibited behavior, or creates material business risk.

### 1 — Partial
The output is broadly usable but misses an important nuance, is too generic, routes the task poorly, or needs meaningful human correction.

### 2 — Pass
The output preserves the intended business logic, factual discipline, risk boundary, and appropriate communication behavior.

## Dimensions
1. **Task understanding** — Did the model solve the real business task rather than only the surface wording?
2. **Fact discipline** — Did it separate confirmed facts, inference, and unknowns correctly?
3. **Business diagnosis** — Did it identify the actual gap/tension when one exists?
4. **Strategy quality** — Is the recommended business approach coherent and appropriately firm/flexible?
5. **Risk control** — Did it avoid unsupported commitments, compliance claims, IP issues, or authority overreach?
6. **Communication quality** — Is the writing natural, concise, relationship-aware, and commercially effective when writing is requested?
7. **Response depth** — Did it avoid both shallow handling of a complex problem and over-structuring of a simple one?
8. **Advancement value** — Does the result help move the customer/project toward a useful next decision or action?

## Critical-fail rule
Regardless of total score, mark the benchmark as failed if the model:
- invents a material price, certification, approval, delivery commitment, technical conclusion, or customer fact;
- turns an inference into a confirmed fact in a way that could affect a business decision;
- violates a benchmark's explicit prohibited behavior in a material way;
- exposes confidential information that the framework says must remain private.

## Suggested benchmark result
For each case record:
- model/harness,
- model version,
- adapter used,
- date,
- dimension scores,
- critical fail: yes/no,
- short reviewer note.

## Suggested acceptance threshold
For production consideration:
- no critical fails,
- average score >= 1.6/2 across applicable dimensions,
- no core dimension (`Fact discipline`, `Business diagnosis`, `Risk control`) below 1 on any high-risk benchmark.

Thresholds may be tightened as the benchmark set matures.