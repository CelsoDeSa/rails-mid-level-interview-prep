Score: 0
Probability: high
Type: theory

# `validates` vs `validate`

## Question

What is the difference between `validates` and `validate` in Rails?

## Brief Answer

`validates` uses Rails built-in validation helpers. `validate` registers a custom validation method.

## Comprehensive Explanation

Use `validates` for common validations:

```ruby
validates :email, presence: true, uniqueness: true
validates :age, numericality: { greater_than: 0 }
```

Use `validate` when the rule is custom or depends on multiple fields:

```ruby
validate :end_date_after_start_date

private

def end_date_after_start_date
  return if end_date.blank? || start_date.blank?
  errors.add(:end_date, "must be after start date") if end_date <= start_date
end
```

Also mention that Rails validations are for application-level feedback, while database constraints protect integrity even under concurrency or code bugs.

## Practice Prompt

Write a custom validation that prevents an event from ending before it starts.
