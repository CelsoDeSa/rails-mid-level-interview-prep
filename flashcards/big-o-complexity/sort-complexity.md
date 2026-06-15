Score: 0
Probability: medium
Type: theory

# Sorting Complexity

## Question

What is the usual complexity of sorting in Ruby, and what should you consider when sorting Rails records?

## Brief Answer

Sorting is usually O(n log n). In Rails, prefer database sorting with proper indexes when possible, and avoid loading huge datasets into Ruby just to sort them.

## Comprehensive Explanation

Ruby example:

```ruby
users.sort_by(&:created_at)
```

This requires all users to be loaded into Ruby memory, then sorted. Sorting itself is typically O(n log n), plus memory overhead.

Rails/database example:

```ruby
User.order(created_at: :desc)
```

The database handles sorting. This is usually better for large datasets, especially with pagination and useful indexes. But sorting on an unindexed column over many rows can still be expensive.

## Practice Prompt

When would `User.all.sort_by(&:created_at)` be worse than `User.order(:created_at)`?
