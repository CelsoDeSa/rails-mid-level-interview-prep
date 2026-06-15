Score: 0
Probability: high
Type: coding

# `group_by` and `transform_values`

## Question

Given an array of orders, write Ruby code to count how many orders exist per status.

## Brief Answer

Use `group_by` and `transform_values(&:count)`.

## Comprehensive Explanation

Example:

```ruby
orders = [
  OpenStruct.new(status: "paid"),
  OpenStruct.new(status: "pending"),
  OpenStruct.new(status: "paid")
]

counts = orders.group_by(&:status).transform_values(&:count)
# { "paid" => 2, "pending" => 1 }
```

Alternative using `each_with_object`:

```ruby
counts = orders.each_with_object(Hash.new(0)) do |order, hash|
  hash[order.status] += 1
end
```

The `each_with_object` version is often more memory-efficient because `group_by` creates arrays of grouped objects first.

## Practice Prompt

Write the `each_with_object` version from memory.
