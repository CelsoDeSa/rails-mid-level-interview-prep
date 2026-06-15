Score: 0
Probability: high
Type: theory

# Scopes vs Class Methods

## Question

What are Rails scopes, and when would you use a scope versus a class method?

## Brief Answer

Scopes are reusable query fragments that return Active Record relations. Use them for chainable query logic; use class methods when the logic is more complex or needs branching.

## Comprehensive Explanation

Example scope:

```ruby
class User < ApplicationRecord
  scope :active, -> { where(active: true) }
  scope :recent, -> { order(created_at: :desc) }
end

User.active.recent.limit(10)
```

Scopes are useful because they remain chainable. They should usually return an `ActiveRecord::Relation`.

A class method can be clearer for logic with parameters, conditionals, or multiple steps:

```ruby
def self.search(term)
  return all if term.blank?

  where("name ILIKE ?", "%#{sanitize_sql_like(term)}%")
end
```

Interview angle: scopes are not for business workflows; they are for query composition.

## Practice Prompt

Write scopes for `published`, `recent`, and `by_author(author_id)` on a `Post` model.
