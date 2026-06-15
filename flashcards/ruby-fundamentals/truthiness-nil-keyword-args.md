Score: 0
Probability: medium
Type: theory

# Truthiness, Nil, and Keyword Arguments

## Question

How does Ruby handle truthiness, `nil`, and keyword arguments?

## Brief Answer

In Ruby, only `false` and `nil` are falsey; everything else is truthy, including `0` and empty strings. Keyword arguments name inputs explicitly and improve readability for option-heavy methods.

## Comprehensive Explanation

Truthiness:

```ruby
if 0
  # runs
end

if ""
  # runs
end
```

Only `nil` and `false` are falsey.

Nil handling patterns:

```ruby
user&.email
value || default
```

Be careful: `||` replaces `false` too, not just `nil`.

Keyword arguments:

```ruby
def create_order(user:, items:, notify: true)
end
```

They make service object APIs clearer and reduce mistakes from positional arguments.

## Practice Prompt

Why can `enabled = params[:enabled] || true` be a bug?
