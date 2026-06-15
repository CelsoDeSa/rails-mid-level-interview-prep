Score: 0
Probability: medium
Type: theory

# Exception Hierarchy and `ensure`

## Question

What does a normal Ruby `rescue` catch, and what does `ensure` do?

## Brief Answer

A normal `rescue` catches `StandardError` and its descendants, not every `Exception`. `ensure` runs whether an exception happened or not.

## Comprehensive Explanation

Ruby's top-level exception class is `Exception`, but rescuing all exceptions is usually dangerous because it includes system-level errors such as `NoMemoryError`, `SignalException`, and `SystemExit`.

```ruby
begin
  risky_call
rescue StandardError => e
  Rails.logger.error(e.message)
ensure
  cleanup
end
```

Use specific error classes where possible. `ensure` is useful for cleanup: closing files, releasing locks, or resetting state. In Rails jobs and integrations, rescue carefully so failures can be retried or reported instead of silently swallowed.

## Practice Prompt

Why is `rescue Exception` usually a bad idea?
