Score: 0
Probability: low
Type: theory

# Object ID, Singleton Methods, and Eigenclass

## Question

What is `object_id` in Ruby, and can you define a method on only one object instance?

## Brief Answer

`object_id` identifies an object. Ruby can define methods on a single object using singleton methods, stored in that object's singleton class/eigenclass.

## Comprehensive Explanation

Every Ruby object has an `object_id`:

```ruby
user = User.new
user.object_id
```

You can define a method on only that object:

```ruby
user.define_singleton_method(:admin?) { true }
```

Only that instance responds to the new behavior. Internally, Ruby stores this in the object's singleton class, also called eigenclass.

Some objects behave like singletons/interned values, such as symbols, `nil`, `true`, `false`, and some immediate values.

This is less common in day-to-day Rails but useful for understanding Ruby's object model and metaprogramming.

## Practice Prompt

When might Rails or a gem use singleton methods/metaprogramming?
