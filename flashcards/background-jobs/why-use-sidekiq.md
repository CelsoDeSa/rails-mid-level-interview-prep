Score: 0
Probability: high
Type: theory

# Why Use Sidekiq

## Question

Why use Sidekiq or background jobs instead of doing work inside a web request?

## Brief Answer

Use background jobs for slow, retryable, or non-immediate work so requests stay fast and users do not wait for exports, emails, API syncs, or large processing.

## Comprehensive Explanation

Web requests have time limits and should remain responsive. Jobs are better for CSV exports, emails, webhooks, API syncs, image processing, and scheduled work.

Sidekiq stores job payloads in Redis. Worker processes pull jobs from queues and execute them asynchronously. If a job fails, Sidekiq can retry with backoff and eventually move it to a dead queue.

Do not pass full Active Record objects. Pass primitive IDs and reload records inside the job:

```ruby
ExportContactsJob.perform_async(user.id)
```

## Practice Prompt

Explain how you would export 5 million records using Sidekiq and S3.
