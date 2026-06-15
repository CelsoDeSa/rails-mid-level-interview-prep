Score: 0
Probability: medium
Type: theory

# REST vs GraphQL

## Question

What is the difference between REST and GraphQL? When would you choose each?

## Brief Answer

REST exposes resource-oriented endpoints with HTTP verbs. GraphQL exposes a typed query language where clients request exactly the fields they need. REST is simpler and cache-friendly; GraphQL can reduce over/under-fetching but adds complexity.

## Comprehensive Explanation

REST example:

```http
GET /orders/1
POST /orders
PATCH /orders/1
```

GraphQL example:

```graphql
query {
  order(id: 1) {
    id
    total
    customer { email }
  }
}
```

Choose REST when resources are straightforward, HTTP semantics/caching matter, and simplicity is valuable. Choose GraphQL when clients need flexible nested data, multiple frontend clients have different data needs, or over/under-fetching is a real issue.

Trade-offs: GraphQL requires schema design, query complexity controls, authorization at field/resolver level, and caching strategy.

## Practice Prompt

Would you use REST or GraphQL for an internal admin export API? Why?
