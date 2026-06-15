Score: 0
Probability: medium
Type: theory

# Private vs Protected

## Question

What is the difference between `private` and `protected` methods in Ruby?

## Brief Answer

Private methods are intended to be called only inside the object without an explicit receiver. Protected methods can be called by other instances of the same class or subclass.

## Comprehensive Explanation

Private methods hide implementation details from external callers. In modern Ruby, some receiver rules have evolved, but the practical interview answer is: private is for internal helper behavior.

Protected is rare. It is useful when one instance needs to compare itself with another instance of the same class using an internal method.

```ruby
class User
  def older_than?(other)
    age > other.age
  end

  protected

  attr_reader :age
end
```

If `age` were private, calling `other.age` would generally not be allowed in the classic explanation. Most Rails code uses private far more often than protected.

## Practice Prompt

When would you make a service object helper method private?
