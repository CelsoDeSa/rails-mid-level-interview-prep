Score: 0
Probability: high
Type: theory

# Advanced Associations

## Question

Explain `has_and_belongs_to_many`, `has_many :through`, STI, and polymorphic associations.

## Brief Answer

HABTM is a simple many-to-many join table. `has_many :through` uses a real join model. STI stores subclasses in one table with a `type` column. Polymorphic associations let one model belong to multiple possible parent models.

## Comprehensive Explanation

**HABTM:** simple many-to-many with only foreign keys. Less flexible.

**has_many :through:** preferred when the relationship needs timestamps, validations, callbacks, or extra fields.

```ruby
class User < ApplicationRecord
  has_many :memberships
  has_many :projects, through: :memberships
end
```

**STI:** single table inheritance. `Admin < User` and `Customer < User` share the `users` table and Rails uses a `type` column. Good when subclasses share most fields/behavior; bad when they diverge heavily.

**Polymorphic association:** one model can belong to several types:

```ruby
class Comment < ApplicationRecord
  belongs_to :commentable, polymorphic: true
end
```

Table has `commentable_type` and `commentable_id`.

## Practice Prompt

When would you choose `has_many :through` over HABTM?
