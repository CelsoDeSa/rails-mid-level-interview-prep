Score: 0
Probability: high
Type: theory

# Testing Background Jobs

## Question

How do you test background jobs in Rails?

## Brief Answer

Test that jobs are enqueued when expected, and test the job's `perform` behavior separately. For side effects, use test adapters, mocks/fakes, and assertions on database changes or delivered emails.

## Comprehensive Explanation

Two levels:

1. The request/service enqueues the job:

```ruby
expect {
  post exports_path
}.to have_enqueued_job(ExportJob)
```

2. The job performs correctly:

```ruby
expect {
  described_class.perform_now(export.id)
}.to change { export.reload.status }.from("pending").to("completed")
```

For Sidekiq-specific behavior, projects may use `sidekiq/testing`. Avoid real external API calls in tests; inject clients or use fakes/stubs. Test missing records and retry-safe/idempotent behavior.

## Practice Prompt

How would you test an export job that uploads a file to S3?
