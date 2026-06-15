Score: 0
Probability: high
Type: theory

# Explain MVC in Rails

## Question

Explain MVC in Rails. What belongs in models, controllers, and views?

## Brief Answer

MVC separates responsibilities: models handle data and domain rules, controllers coordinate requests and responses, and views render HTML/JSON for the user.

## Comprehensive Explanation

In Rails, the router maps an HTTP request to a controller action. The controller should stay thin: read params, authorize, call models/services, and choose a response. Models represent domain objects and database-backed data using Active Record; they hold associations, validations, scopes, and simple domain behavior. Views render the final response, usually HTML, Turbo Stream, or JSON.

A mid-level answer should mention avoiding fat controllers. If a controller action coordinates multiple models, external APIs, background jobs, or side effects, extract that workflow into a service object or command object. Avoid putting every piece of business logic in the model just because Rails makes it easy.

## Practice Prompt

Explain where you would put logic for creating an order, charging Stripe, and sending a confirmation email.
