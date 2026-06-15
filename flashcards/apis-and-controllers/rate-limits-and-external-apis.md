Score: 0
Probability: high
Type: debugging

# Rate Limits and External APIs

## Question

How do you handle rate limits and failures when integrating with external APIs like Stripe or Klaviyo?

## Brief Answer

Use background jobs, retries with backoff, respect rate-limit headers, make operations idempotent, log failures, and surface reconnect/action-needed states to users.

## Comprehensive Explanation

External API calls should rarely block critical user requests. Queue work in Sidekiq and process asynchronously. If the provider returns rate-limit responses, respect headers such as `Retry-After` when available. Use exponential backoff for transient failures.

Idempotency is critical. A retry should not duplicate charges, orders, messages, or sync records. Use provider idempotency keys where available, store external IDs, and use database uniqueness constraints to prevent duplicates.

For permanent failures, move jobs to a dead queue or mark the integration as needing attention. Log enough context to debug without logging secrets or tokens.

## Practice Prompt

Stripe sends the same webhook twice. How do you avoid processing it twice?
