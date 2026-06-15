Score: 0
Probability: medium
Type: theory

# Ruby Memory Management and GC

## Question

How does Ruby handle memory management, and how would you diagnose a memory leak?

## Brief Answer

Ruby allocates objects automatically and uses garbage collection to free unreachable objects. Diagnose leaks by monitoring memory growth and using tools like memory_profiler, derailed_benchmarks, logs, APM, and heap dumps.

## Comprehensive Explanation

Ruby uses automatic memory management. When objects are no longer referenced, the garbage collector can reclaim them. Memory issues often happen when code keeps references unintentionally: global arrays, class variables, unbounded caches, large Active Record collections, or background jobs loading huge datasets.

Diagnosis steps:

- observe memory over time in production metrics
- reproduce with realistic data
- check recent changes and endpoints/jobs with memory spikes
- use `memory_profiler` or `derailed_benchmarks`
- avoid loading all records; use `find_each`, `in_batches`, `pluck`, or streaming

Interview angle: do not claim deep VM expertise; show practical debugging and prevention.

## Practice Prompt

Why can `User.all.each` be risky on a table with millions of rows?
