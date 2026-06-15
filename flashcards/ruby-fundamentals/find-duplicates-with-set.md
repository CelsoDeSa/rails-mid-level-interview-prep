Score: 0
Probability: high
Type: coding

# Find Duplicates Efficiently

## Question

Write a Ruby method to find duplicates in a large array. What is the time complexity?

## Brief Answer

Use a `Set` or Hash to track seen elements in one pass. Time complexity is O(n), space complexity is O(n).

## Comprehensive Explanation

```ruby
require "set"

def duplicates(values)
  seen = Set.new
  dupes = Set.new

  values.each do |value|
    if seen.include?(value)
      dupes.add(value)
    else
      seen.add(value)
    end
  end

  dupes.to_a
end
```

The naive nested-loop approach compares every item with every other item and is O(n²). A Set/Hash gives average O(1) lookups, so scanning the array once is O(n). The trade-off is extra memory for the Set.

## Practice Prompt

Explain why `array.include?(value)` inside a loop can become O(n²).
