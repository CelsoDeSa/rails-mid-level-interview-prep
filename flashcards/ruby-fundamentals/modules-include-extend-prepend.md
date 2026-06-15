Score: 0
Probability: high
Type: theory

# Modules: `include`, `extend`, and `prepend`

## Question

How do `include`, `extend`, and `prepend` work in Ruby modules?

## Brief Answer

`include` adds module methods as instance methods. `extend` adds them as class/singleton methods. `prepend` adds instance methods before the class in the method lookup chain.

## Comprehensive Explanation

```ruby
module Trackable
  def track
    "tracked"
  end
end

class Order
  include Trackable
end

Order.new.track
```

`extend` is used when you want methods on the class object itself:

```ruby
class Order
  extend Trackable
end

Order.track
```

`prepend` places the module before the class in lookup order, so it can wrap or override existing behavior while still calling `super`.

Ruby searches the receiver's class, prepended modules, included modules, superclasses, and eventually `BasicObject`; if no method exists, `method_missing` leads to `NoMethodError`.

## Practice Prompt

Explain one Rails concern use case and one concern misuse.
