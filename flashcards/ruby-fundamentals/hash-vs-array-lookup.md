Score: 0
Probability: high
Type: theory

# Hash vs Array Lookup

## Question

What is the time complexity of finding a key in a Hash versus finding a value in an Array?

## Brief Answer

Hash key lookup is average O(1). Searching an unsorted Array is O(n).

## Comprehensive Explanation

Ruby Hashes use hashing to locate values by key quickly. Arrays are ordered lists; if you search by value, Ruby may need to inspect each element until it finds a match or reaches the end.

```ruby
roles = { admin: 1, editor: 2 }
roles[:admin] # average O(1)

ids = [1, 2, 3, 4]
ids.include?(4) # O(n)
```

For repeated membership checks over a large collection, convert the array to a Set or Hash. For ordered iteration, arrays are still appropriate.

## Practice Prompt

How would you optimize checking whether 10,000 user IDs are allowed?
