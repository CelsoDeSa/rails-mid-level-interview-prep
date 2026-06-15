Score: 0
Probability: high
Type: theory

# `includes`, `joins`, `preload`, and `eager_load`

## Question

What is the difference between `includes`, `joins`, `preload`, and `eager_load` in Active Record?

## Brief Answer

`joins` uses SQL joins but does not preload records. `preload` loads associations using separate queries. `eager_load` uses a `LEFT OUTER JOIN`. `includes` lets Rails choose preload or eager load depending on the query.

## Comprehensive Explanation

`joins(:posts)` is best when filtering or sorting by an associated table:

```ruby
User.joins(:posts).where(posts: { published: true })
```

But if you later call `user.posts`, Rails may still query again unless the association was preloaded.

`preload(:posts)` always uses separate queries:

```ruby
User.preload(:posts)
```

`eager_load(:posts)` uses a `LEFT OUTER JOIN` and loads the association from the joined rows.

`includes(:posts)` is often used to prevent N+1; Rails may use separate queries or a join if you reference the associated table.

Mid-level answer: pick based on intent. Use `includes/preload` for displaying associations; use `joins` for filtering; inspect generated SQL when performance matters.

## Practice Prompt

Which would you use to list users with their posts? Which would you use to find users with published posts only?
