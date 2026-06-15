Score: 0
Probability: high
Type: theory

# Rails Request Lifecycle

## Question

Walk me through what happens when a request hits a Rails app.

## Brief Answer

The browser sends an HTTP request, Rails routes it to a controller action, the controller uses models/services, data may be fetched from PostgreSQL, then Rails renders HTML/JSON/Turbo and returns the response.

## Comprehensive Explanation

A full answer can start outside Rails: DNS resolves the domain to an IP, a load balancer or web server receives the request, and the request reaches an app server such as Puma. Rails routing maps the HTTP verb and path to a controller action. The controller checks params, authentication/authorization, and calls models or services. Active Record builds SQL queries and talks to PostgreSQL. The result is rendered through a view, JSON serializer, or Turbo Stream, then returned to the browser.

For production architecture, mention that Nginx/CDN may serve static assets, a load balancer may distribute traffic, caching may short-circuit work, and background jobs should handle slow non-request-critical work.

## Practice Prompt

Explain the request lifecycle for `GET /users/42/orders`.
