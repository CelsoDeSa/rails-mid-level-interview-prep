Score: 0
Probability: high
Type: theory

# Rails Caching Basics

## Question

What caching options exist in Rails, and when would you use them?

## Brief Answer

Rails supports page/action-like HTTP caching, fragment caching, low-level caching with `Rails.cache`, Russian doll caching, and external stores like Redis or Memcached. Use caching for expensive repeated reads, not as a substitute for correct queries.

## Comprehensive Explanation

Common caching approaches:

- **Fragment caching:** cache a view partial or component.
- **Russian doll caching:** nested fragments with cache keys based on updated timestamps.
- **Low-level caching:** cache expensive computed values:

```ruby
Rails.cache.fetch("user:#{user.id}:stats", expires_in: 10.minutes) do
  StatsCalculator.new(user).call
end
```

- **HTTP caching:** use ETags/cache headers to avoid sending unchanged responses.

Caching trade-offs:

- invalidation is hard
- stale data may be acceptable or unacceptable depending on feature
- cache keys should include data versioning
- do not cache secrets or user-specific data incorrectly

Interview angle: first fix obviously bad queries/N+1/missing indexes; then cache stable expensive reads.

## Practice Prompt

What would you cache on a dashboard with expensive aggregate statistics?
