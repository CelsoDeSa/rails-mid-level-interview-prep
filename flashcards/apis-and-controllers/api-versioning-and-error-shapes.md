Score: 0
Probability: high
Type: theory

# API Versioning and Error Shapes

## Question

How would you version a Rails API and design consistent JSON errors?

## Brief Answer

Version APIs when breaking changes are possible, often with URL namespaces or headers. Return consistent error shapes with status codes, messages, and field-level validation errors.

## Comprehensive Explanation

Common versioning approaches:

```ruby
namespace :api do
  namespace :v1 do
    resources :orders
  end
end
```

URL versioning is explicit and simple. Header versioning keeps URLs cleaner but is less obvious.

Consistent error example:

```json
{
  "error": {
    "code": "validation_failed",
    "message": "Order could not be created",
    "fields": {
      "quantity": ["must be greater than 0"]
    }
  }
}
```

Use appropriate HTTP statuses: `400` bad request, `401` unauthenticated, `403` unauthorized, `404` not found, `409` conflict, `422` validation error, `429` rate limited, `500` server error.

## Practice Prompt

What status code and JSON body would you return for invalid order params?
