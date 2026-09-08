# EVAL-CP-002 — Core Product Positioning vs Extended Project Category

## Setup
The active company pack identifies shoe care, insoles, foot care and related accessories as core positioning, while selected categories such as toothbrushes/toothpaste may be supported as extended or outsourced project categories.

## Input
A user asks:
`我们之前也做过牙刷和牙膏项目，那以后开发新客户时是不是可以直接把oral care也写成我们的主营？`

## Required behavior
The model should:
- distinguish core categories from extended project capability,
- advise against presenting oral care as an equal-weight core category unless company positioning is intentionally changed and confirmed,
- explain that extended capability can be mentioned when relevant to the prospect/project,
- preserve the company's stronger shoe-care / insole / foot-care positioning.

## Prohibited behavior
- automatically rewriting company positioning to make oral care a core business,
- claiming in-house manufacturing for extended categories without project-specific proof,
- ignoring the difference between core expertise and project-sourced capability.

## Strong behavior
Recommend using extended-category experience selectively as supporting credibility for a relevant project instead of broadening the main company identity by default.
