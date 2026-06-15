Score: 0
Probability: high
Type: theory

# Validations vs Database Constraints

## Question

What is the difference between Rails validations and database constraints?

## Brief Answer

Rails validations give user-friendly application-level checks. Database constraints enforce integrity at the database level and protect against race conditions or non-Rails writes.

## Comprehensive Explanation

Rails validations run before saving through Active Record. They are great for clear error messages and business rules. But they are not enough for critical integrity because concurrent requests can bypass assumptions.

For example, `validates :email, uniqueness: true` can still race if two requests create the same email at the same time. Add a unique database index:

```ruby
add_index :users, :email, unique: true
```

Use both: validation for UX, database constraint for correctness. Common database constraints include `null: false`, foreign keys, unique indexes, check constraints, and referential integrity.

## Practice Prompt

How would you enforce unique emails safely in a Rails app?
