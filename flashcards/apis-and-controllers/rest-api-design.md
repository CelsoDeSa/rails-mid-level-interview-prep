Score: 0
Probability: high
Type: system-design

# REST API Design

## Question

Design a REST API endpoint to create an order. What should you consider?

## Brief Answer

Use `POST /orders`, authenticate the user, validate params, create records in a transaction, return correct status codes and errors, and offload slow side effects to background jobs.

## Comprehensive Explanation

A solid flow:

```ruby
POST /orders
```

Controller responsibilities:

- authenticate user
- authorize action
- permit strong params
- call an `OrderCreator` service
- render `201 Created` on success
- render `422 Unprocessable Entity` for validation errors

The service may use a database transaction to create the order and line items. It should not block the request on slow email or external API calls unless the business requires it. Use background jobs for confirmations, webhooks, or heavy processing.

Also mention idempotency if duplicate requests could create duplicate orders, pagination/filtering for list endpoints, and consistent JSON error shape.

## Practice Prompt

Sketch a Rails controller action for `OrdersController#create`.
