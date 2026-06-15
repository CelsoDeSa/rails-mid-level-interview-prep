Score: 0
Probability: high
Type: theory

# Dependency Inversion Principle

## Question

Explain the Dependency Inversion Principle with a Rails service example.

## Brief Answer

High-level code should not hardcode low-level dependencies. Inject collaborators such as gateways or clients so code is easier to test and change.

## Comprehensive Explanation

Bad:

```ruby
class PaymentProcessor
  def initialize(order)
    @order = order
    @gateway = StripeGateway.new
  end
end
```

The service is tightly coupled to Stripe and harder to test.

Better:

```ruby
class PaymentProcessor
  def initialize(order, gateway: StripeGateway.new)
    @order = order
    @gateway = gateway
  end

  def call
    @gateway.charge(@order.total_cents)
  end
end
```

Tests can inject a fake gateway. Production can use Stripe. Later, another gateway can be introduced with less change.

This principle is especially useful for external APIs, storage providers, mailers, and anything slow or unreliable.

## Practice Prompt

How would dependency injection help test a Klaviyo sync service?
