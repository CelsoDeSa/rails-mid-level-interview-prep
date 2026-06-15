Score: 0
Probability: high
Type: theory

# Single Responsibility Principle

## Question

Explain the Single Responsibility Principle and give a Rails example.

## Brief Answer

A class should have one responsibility and one reason to change. In Rails, avoid putting API sync, payment logic, and email sending inside a controller or model; extract focused service objects.

## Comprehensive Explanation

SRP does not mean a class has only one method. It means the class owns one coherent responsibility. A controller should handle the HTTP layer, not complex business workflows. A model should represent domain data and core rules, not every side effect in the system.

Bad:

```ruby
class OrdersController < ApplicationController
  def create
    # validate cart, create order, charge Stripe, send email, sync CRM...
  end
end
```

Better:

```ruby
class OrdersController < ApplicationController
  def create
    result = OrderCreator.call(user: current_user, params: order_params)
    # render result
  end
end
```

Now the controller changes when HTTP behavior changes, and `OrderCreator` changes when order creation rules change.

## Practice Prompt

Explain how SRP applies to a Stripe integration service.
