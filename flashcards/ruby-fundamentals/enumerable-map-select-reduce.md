Score: 0
Probability: high
Type: coding

# `map`, `select`, and `reduce`

## Question

What is the difference between `map`, `select`, and `reduce` in Ruby? Code examples.

## Brief Answer

`map` transforms each element, `select` filters elements, and `reduce` combines elements into one result.

## Comprehensive Explanation

```ruby
numbers = [1, 2, 3, 4]

numbers.map { |n| n * 2 }      # [2, 4, 6, 8]
numbers.select { |n| n.even? } # [2, 4]
numbers.reduce(0) { |sum, n| sum + n } # 10
```

`map` returns a new array with the same number of elements. `select` returns only elements where the block is truthy. `reduce`/`inject` accumulates a single value, such as a sum, hash, or grouped result.

In interviews, explain both behavior and when you would use each. Also be ready to use Rails alternatives like `pluck` when data is still in the database.

## Practice Prompt

Given an array of orders with `status`, return a hash counting orders by status.
