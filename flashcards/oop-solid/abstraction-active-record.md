Score: 0
Probability: high
Type: theory

# Abstraction and Active Record

## Question

Explain abstraction using Active Record as an example.

## Brief Answer

Abstraction hides implementation details behind a simpler interface. Active Record lets you query using Ruby methods instead of manually writing SQL most of the time.

## Comprehensive Explanation

Abstraction reduces complexity for the caller. With Active Record, this Ruby code:

```ruby
User.where(active: true).order(created_at: :desc)
```

abstracts away SQL generation, database connection handling, object instantiation, and result mapping. The developer can think in terms of domain objects while Rails handles database details.

Good abstraction exposes useful behavior without leaking too many internals. But a mid-level developer should know when to look beneath the abstraction: inspect generated SQL, use `EXPLAIN ANALYZE`, and write raw SQL when the query is too complex or performance-critical.

## Practice Prompt

Give one benefit and one risk of relying on Active Record abstractions.
