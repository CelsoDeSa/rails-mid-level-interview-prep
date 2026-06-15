Score: 0
Probability: high
Type: theory

# Database Transactions

## Question

What is a database transaction, and when would you use one in Rails?

## Brief Answer

A transaction groups multiple database operations so they either all succeed or all roll back. Use it when partial updates would leave invalid or inconsistent data.

## Comprehensive Explanation

Transactions protect consistency. Example: creating an order, creating line items, and decrementing inventory should not partially succeed.

```ruby
Order.transaction do
  order = user.orders.create!(status: "pending")
  cart.items.each do |item|
    order.line_items.create!(product: item.product, quantity: item.quantity)
    item.product.decrement!(:stock, item.quantity)
  end
end
```

If any `create!` or `decrement!` raises, Rails rolls back the database changes. Avoid long transactions around slow external API calls because they can hold locks longer than needed.

## Practice Prompt

Explain why charging Stripe inside a DB transaction can be risky.
