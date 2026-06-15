Score: 0
Probability: high
Type: theory

# Inheritance vs Composition

## Question

What is inheritance, and why do developers often say “favor composition over inheritance”?

## Brief Answer

Inheritance models an “is-a” relationship and reuses parent behavior. Composition models a “has-a” relationship and is often more flexible because behavior is delegated to collaborator objects instead of locked into a class hierarchy.

## Comprehensive Explanation

Rails uses inheritance heavily:

```ruby
class User < ApplicationRecord
end

class OrdersController < ApplicationController
end
```

Inheritance is useful when the child truly is a specialized version of the parent. But deep inheritance trees can become fragile: changing parent behavior can unexpectedly affect many subclasses.

Composition creates objects that collaborate:

```ruby
class ExportRunner
  def initialize(storage: S3Storage.new, generator: CsvGenerator.new)
    @storage = storage
    @generator = generator
  end
end
```

This is easier to test and swap. A mid-level Rails answer should recognize both: use framework inheritance normally, but prefer composition/service collaborators for business workflows.

## Practice Prompt

When would a module or service object be better than subclassing?
