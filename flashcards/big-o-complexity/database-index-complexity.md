Score: 0
Probability: high
Type: theory

# Database Index Complexity

## Question

How do database indexes relate to Big-O complexity?

## Brief Answer

Without an index, the database may scan many rows, roughly O(n). With a B-tree index, lookup is often O(log n), which scales much better.

## Comprehensive Explanation

Query without index:

```sql
SELECT * FROM users WHERE email = 'a@example.com';
```

If `email` is not indexed, PostgreSQL may perform a sequential scan, checking row by row. On a large table this is expensive.

With an index:

```ruby
add_index :users, :email, unique: true
```

PostgreSQL can use the index to locate matching rows much faster. Many common indexes use B-tree structures, where lookup is approximately O(log n).

Always validate with `EXPLAIN ANALYZE`; indexes have write and storage costs.

## Practice Prompt

Why should you index foreign keys used in joins?
