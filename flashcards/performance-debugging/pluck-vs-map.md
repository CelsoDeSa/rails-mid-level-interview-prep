Score: 0
Probability: high
Type: theory

# `pluck` vs `map`

## Question

What is the difference between `User.all.map(&:email)` and `User.pluck(:email)`?

## Brief Answer

`map` loads full Active Record objects into Ruby memory and then extracts emails. `pluck` asks the database to return only the email column.

## Comprehensive Explanation

```ruby
User.all.map(&:email)
```

This instantiates every `User` record, including all selected columns, then runs Ruby code to extract emails. It uses more memory and can be slower.

```ruby
User.pluck(:email)
```

This generates SQL selecting only the needed column and returns an array of values. It is usually better for large datasets when you only need raw values.

Use full objects when you need model behavior, validations, associations, or callbacks. Use `pluck` for simple column extraction.

## Practice Prompt

How would you fetch only IDs for active users efficiently?
