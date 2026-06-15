Score: 0
Probability: high
Type: theory

# Encapsulation in Rails

## Question

Explain encapsulation with a Ruby/Rails example.

## Brief Answer

Encapsulation means hiding internal details and exposing a controlled interface. In Rails, a service object can expose `.call` while hiding the steps for payment, syncing, or exporting.

## Comprehensive Explanation

Encapsulation keeps an object's internal state and helper methods from leaking across the application. In Ruby, use `private` methods, public methods, and accessors intentionally.

Example:

```ruby
class PaymentProcessor
  def initialize(order)
    @order = order
  end

  def call
    validate_order!
    charge_customer
    mark_paid
  end

  private

  def validate_order!
    # internal detail
  end

  def charge_customer
    # internal detail
  end

  def mark_paid
    @order.update!(status: "paid")
  end
end
```

The caller only needs `PaymentProcessor.new(order).call`. It does not need to know the internal steps.

## Practice Prompt

Refactor controller payment logic into an encapsulated service object.
