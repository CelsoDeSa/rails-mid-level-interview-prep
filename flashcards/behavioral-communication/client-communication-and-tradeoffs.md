Score: 0
Probability: high
Type: behavioral

# Client Communication and Trade-offs

## Question

How do you communicate technical trade-offs to a client or non-technical stakeholder?

## Brief Answer

Explain the business impact, options, risks, cost, and recommendation in plain language. Avoid unnecessary jargon and confirm the decision criteria.

## Comprehensive Explanation

A good structure:

1. Clarify the goal.
2. Present 2–3 options.
3. Explain trade-offs: speed, cost, risk, maintainability, user impact.
4. Recommend one option.
5. Ask for confirmation or constraints.

Example:

> “We can ship the export quickly inside the request, but it may time out for large customers. The safer option is a background job with a download link. It takes longer to build, but it scales better and avoids bad UX. I recommend the background job path.”

Dev.Pro/client-readiness angle: show you can work in a service/client environment, not just code in isolation.

## Practice Prompt

Explain to a client why a large export should be asynchronous instead of immediate.
