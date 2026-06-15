Score: 0
Probability: medium
Type: theory

# Blocks, Procs, and Lambdas

## Question

What are blocks, Procs, and lambdas in Ruby? How are they different?

## Brief Answer

They all represent deferred executable code. Blocks are anonymous code passed to methods; Procs and lambdas are objects that store blocks for later use. Lambdas check arity more strictly and return differently.

## Comprehensive Explanation

A block is passed directly:

```ruby
[1, 2, 3].map { |n| n * 2 }
```

A Proc stores executable code:

```ruby
double = Proc.new { |n| n * 2 }
double.call(3)
```

A lambda is similar but behaves more like a method: it enforces argument count more strictly, and `return` returns from the lambda rather than the enclosing method.

Blocks are generally lighter because they do not require instantiating a Proc object unless captured.

## Practice Prompt

Write a method that accepts a block and yields each active user.
