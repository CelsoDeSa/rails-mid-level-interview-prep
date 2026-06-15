Score: 0
Probability: medium
Type: theory

# Strings vs Symbols

## Question

What is the difference between strings and symbols in Ruby?

## Brief Answer

Strings are mutable text objects. Symbols are immutable interned identifiers, commonly used as keys or names.

## Comprehensive Explanation

Two identical string literals may be separate objects unless frozen. Symbols with the same name refer to the same interned object.

```ruby
"status".object_id == "status".object_id # often false
:status.object_id == :status.object_id   # true
```

Use strings for user-facing or mutable text. Use symbols for identifiers like hash keys, enum-like values, method names, and Rails params internally. Modern Ruby can freeze string literals with:

```ruby
# frozen_string_literal: true
```

In Rails, params often support indifferent access, but you should still understand the distinction.

## Practice Prompt

When would you use `{ status: "paid" }` versus `{ "status" => "paid" }`?
