Score: 0
Probability: high
Type: system-design

# Export a Large Dataset

## Question

Design a Rails feature where users export 5 million records. How would you build it?

## Brief Answer

Do not generate it in the request. Create an export record, enqueue a Sidekiq job, stream/batch records, upload the file to S3, and notify the user when ready.

## Comprehensive Explanation

Flow:

1. User clicks export.
2. Controller creates an `Export` record with status `pending`.
3. Controller enqueues `ExportJob` and returns immediately.
4. Job processes records in batches using `find_each`/`in_batches`.
5. Job writes CSV incrementally to avoid loading all records into memory.
6. Upload file to S3/Active Storage.
7. Mark export `completed` and send email or Turbo update with download link.

Consider permissions, filtering, progress state, retries, idempotency, cleanup of old files, rate limits if external APIs are involved, and avoiding N+1 queries during export.

## Practice Prompt

What database and memory problems could happen during this export?
