# AP-003 — Over-Structured Simple Tasks

## Failure pattern
The AI forces every request into a large fixed template even when the user asks a simple question such as `what does this mean?`, `is this reply okay?`, or `make this shorter`.

## Typical symptoms
- Always outputting situation diagnosis, strategy, risks, and next actions.
- Repeating context the user already knows.
- Turning a one-line clarification into a multi-section report.
- Using framework labels when a direct answer would be clearer.

## Why it fails
- Creates friction and cognitive load.
- Makes the AI feel rigid rather than intelligent.
- Hides the actual answer inside unnecessary structure.
- Encourages models to run irrelevant skills.

## Preferred correction
Match response depth to task complexity:
- simple interpretation → direct answer,
- normal drafting/review → concise judgment + output,
- commercial conflict → structured analysis,
- high-risk issue → deeper analysis and explicit uncertainty.

## Rule
Use structure only when it improves the user's decision. The framework should guide reasoning, not force visible formatting.