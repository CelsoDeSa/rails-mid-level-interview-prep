Score: 0
Probability: high
Type: theory

# Class Methods vs Instance Methods

## Question

What is the difference between class methods and instance methods in Ruby/Rails?

## Brief Answer

Instance methods are called on individual objects. Class methods are called on the class itself and often represent query/building/factory behavior.

## Comprehensive Explanation

Instance method:

```ruby
class User
  def full_name
    "#{first_name} #{last_name}"
  end
end

user.full_name
```

Class method:

```ruby
class User < ApplicationRecord
  def self.active
    where(active: true)
  end
end

User.active
```

Use instance methods for behavior of one object. Use class methods for behavior of the collection/class, such as queries, factories, or named constructors. In Rails, scopes are a special chainable form of class-level query logic.

## Practice Prompt

Should `User#active?` be an instance method or class method? What about `User.active`?
