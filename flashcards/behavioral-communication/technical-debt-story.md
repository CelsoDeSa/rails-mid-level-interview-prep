Score: 0
Probability: high
Type: behavioral

# Technical Debt Story

## Question

Tell me about a time you identified technical debt and helped fix it.

## Brief Answer

Use a STAR story: describe the legacy problem, risk, proposed solution, implementation, and measurable impact.

## Comprehensive Explanation

Suggested structure based on the research material:

- Situation: legacy export system was synchronous/browser-blocking and failed as datasets grew.
- Task: make exports reliable without timing out requests or freezing UX.
- Action: move export generation to Sidekiq, process asynchronously, store result in S3/Active Storage, notify user with a link, keep UI responsive with Hotwire.
- Result: requests no longer blocked, large datasets could be processed, user experience improved, and technical risk decreased.

Make it specific and honest. If exact metrics are unknown, do not invent numbers. Say “reduced timeouts” or “made the process reliable for larger exports” if that is what you can support.

## Practice Prompt

Answer using STAR in under 2 minutes.
