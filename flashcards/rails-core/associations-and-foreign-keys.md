Score: 0
Probability: high
Type: theory

# Associations and Foreign Keys

## Question

If a `Book` belongs to a `User`, where does the foreign key live? How would you model common Rails associations?

## Brief Answer

The foreign key lives on the table with `belongs_to`, so `books` has `user_id`. Common associations include `belongs_to`, `has_many`, `has_one`, and `has_many :through`.

## Comprehensive Explanation

In Rails, `belongs_to :user` means the current model stores the foreign key:

```ruby
class Book < ApplicationRecord
  belongs_to :user
end

class User < ApplicationRecord
  has_many :books
end
```

The `books` table should have `user_id`, ideally with a database foreign key and index:

```ruby
add_reference :books, :user, null: false, foreign_key: true
```

For many-to-many relationships, prefer `has_many :through` when the join needs validations, timestamps, or business logic. `has_and_belongs_to_many` is simpler but less flexible.

## Practice Prompt

Model users, projects, and memberships where users can belong to many projects.
