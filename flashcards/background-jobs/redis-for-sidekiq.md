Score: 0
Probability: high
Type: theory

# Redis for Sidekiq

## Question

What is Redis, why does Sidekiq use it, and can Redis lose data?

## Brief Answer

Redis is an in-memory key-value data store running as a server process. Sidekiq uses it as a fast job queue. Redis can be configured with persistence, but durability depends on configuration.

## Comprehensive Explanation

Redis stores data primarily in memory, which makes it very fast. It supports data structures like lists, sets, sorted sets, and hashes. Sidekiq uses Redis to store queues, scheduled jobs, retries, and job metadata.

Redis supports TTLs for expiring keys, useful for caches and temporary data.

Persistence options include snapshots (RDB) and append-only file (AOF). If persistence is disabled or misconfigured, data can be lost on crash/restart. Even with persistence, Redis is not the same durability model as PostgreSQL.

Interview angle: Redis is great for queues/caching, but critical durable data should usually live in the relational database.

## Practice Prompt

Why should you not treat Redis as the source of truth for billing data?
