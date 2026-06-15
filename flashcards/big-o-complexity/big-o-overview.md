Score: 0
Probability: high
Type: theory

# Big-O Overview

## Question

Explain Big-O notation and common complexities using Ruby/Rails examples.

## Brief Answer

Big-O describes how runtime or memory grows as input size grows. Common examples: O(1) Hash lookup, O(log n) indexed database lookup, O(n) array scan, O(n log n) sorting, and O(n²) nested loops or repeated linear lookups.

## Comprehensive Explanation

Examples:

- **O(1):** `hash[:key]`, array access by index.
- **O(log n):** binary search, many indexed database lookups using B-tree indexes.
- **O(n):** iterating over an array, `array.include?` on unsorted arrays.
- **O(n log n):** typical efficient sorting, `sort_by`.
- **O(n²):** nested loops comparing every item to every other item.

In Rails, complexity appears in database access too. A missing index can cause a table scan. An N+1 query can make one page issue many database calls. A mid-level developer should be able to explain the cost and propose a better data structure/query.

## Practice Prompt

Classify the complexity of looking up IDs using Array#include? in a loop versus using a Set.
