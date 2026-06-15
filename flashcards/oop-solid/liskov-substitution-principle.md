Score: 0
Probability: medium
Type: theory

# Liskov Substitution Principle

## Question

What is the Liskov Substitution Principle? Give a Ruby example.

## Brief Answer

A subclass should be usable anywhere its parent is expected without changing correctness. Subclasses should not break parent contracts or surprise callers.

## Comprehensive Explanation

Classic bad example:

```ruby
class Bird
  def fly
    "flying"
  end
end

class Penguin < Bird
  def fly
    raise "I cannot fly"
  end
end
```

If code expects every `Bird` to fly, `Penguin` breaks the contract. Better model the hierarchy differently:

```ruby
class Bird; end

class FlyingBird < Bird
  def fly
    "flying"
  end
end

class Penguin < Bird
  def swim
    "swimming"
  end
end
```

In Rails, avoid subclassing models or services in ways that violate expected behavior. This matters especially with STI: all subclasses share a table but should still satisfy shared assumptions.

## Practice Prompt

Give an example where STI could violate Liskov if subclasses behave too differently.
