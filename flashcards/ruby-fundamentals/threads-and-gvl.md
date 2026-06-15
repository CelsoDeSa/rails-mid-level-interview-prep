Score: 0
Probability: low
Type: theory

# Ruby Threads and GVL

## Question

If MRI Ruby has a Global VM Lock, why are threads still useful?

## Brief Answer

Threads are useful for I/O-bound work. While one thread waits for network, disk, or database I/O, Ruby can let another thread run.

## Comprehensive Explanation

MRI Ruby's Global VM Lock prevents multiple Ruby threads from executing Ruby bytecode truly in parallel. This limits CPU-bound parallelism. However, threads still help for I/O-bound tasks because the lock can be released while waiting on external operations.

Example: downloading many files, making HTTP API calls, or waiting for database responses. While one thread waits for an HTTP response, another thread can continue.

For CPU-heavy parallel work, consider background jobs, processes, native extensions, or other concurrency models. In Rails, understand Puma threads and database connection pool sizing.

## Practice Prompt

Why can too many Puma threads cause database connection problems?
