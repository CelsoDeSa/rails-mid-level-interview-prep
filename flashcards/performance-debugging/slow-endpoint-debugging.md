Score: 0
Probability: high
Type: debugging

# Debugging a Slow Endpoint

## Question

A Rails endpoint is timing out after 30 seconds. How do you debug it?

## Brief Answer

Check logs and metrics, reproduce, identify slow SQL/N+1/missing indexes, external API waits, locks, or slow Ruby code, then measure and fix the bottleneck.

## Comprehensive Explanation

Start by finding where time is spent. Rails logs often show controller time, view time, and database time. APM tools can break down SQL, external requests, and Ruby execution.

Common causes:

- N+1 queries
- missing indexes / sequential scans
- table locks from bulk updates
- slow external APIs called during request
- heavy Ruby loops or memory usage
- rendering too much data

Use `EXPLAIN ANALYZE` for SQL. Use logs or benchmarking for Ruby code. Move slow non-critical work to Sidekiq. Add pagination, caching, eager loading, or indexes as appropriate. Measure before and after.

## Practice Prompt

What would you inspect first if database time is low but total request time is high?
