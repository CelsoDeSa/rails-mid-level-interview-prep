Score: 0
Probability: high
Type: theory

# Job Idempotency

## Question

What does idempotency mean for background jobs, and why does it matter?

## Brief Answer

An idempotent job can run more than once without causing duplicate or incorrect side effects. It matters because jobs can retry after failures.

## Comprehensive Explanation

Sidekiq jobs may be retried if exceptions happen. A job that sends an email, charges a card, or creates records must handle duplicate execution safely.

Strategies:

- pass IDs, not objects
- check current state before acting
- use unique database constraints
- store external IDs or idempotency keys
- make state transitions explicit
- avoid non-repeatable side effects before risky operations

Example: before processing a Stripe webhook, store the webhook event ID in a table with a unique index. If the same event arrives twice, skip the second processing.

## Practice Prompt

Design idempotency for an export job that emails a download link.
