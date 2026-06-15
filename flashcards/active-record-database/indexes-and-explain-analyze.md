Score: 0
Probability: high
Type: theory

# Indexes and `EXPLAIN ANALYZE`

## Question

How do you know you need a database index, and how do you measure whether it helped?

## Brief Answer

Add indexes for frequently queried/filter/sort/join columns. Measure with `EXPLAIN ANALYZE`, query timings, and production metrics.

## Comprehensive Explanation

An index helps the database find rows without scanning the whole table. In PostgreSQL, B-tree indexes are common for equality and range lookups. Examples:

```ruby
add_index :users, :email, unique: true
add_index :orders, :created_at
add_index :orders, [:user_id, :status]
```

Use `EXPLAIN ANALYZE` to see the actual query plan and runtime:

```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'a@example.com';
```

Look for sequential scans on large tables, expensive sorts, bad row estimates, or missing index usage. Indexes have trade-offs: they use disk space and slow writes because inserts/updates must maintain the index.

## Practice Prompt

What index would you add for `Order.where(user_id: id, status: "paid")`?
