Score: 0
Probability: high
Type: coding

# Array `include?` Inside a Loop

## Question

Why can using `array.include?` inside a loop be slow, and how would you optimize it?

## Brief Answer

`array.include?` is O(n). If it runs inside a loop over n items, the total can become O(n²). Convert the lookup array to a Set for average O(1) membership checks.

## Comprehensive Explanation

Slow:

```ruby
allowed_ids = [1, 2, 3, 4]

users.select do |user|
  allowed_ids.include?(user.id)
end
```

If both collections are large, each lookup scans the array. Better:

```ruby
require "set"

allowed_ids = Set.new([1, 2, 3, 4])

users.select do |user|
  allowed_ids.include?(user.id)
end
```

This changes membership checks from O(n) to average O(1), making the whole operation roughly O(n + m) instead of O(n*m).

## Practice Prompt

Rewrite a nested lookup using a Hash or Set and explain the complexity change.
