Score: 0
Probability: medium
Type: theory

# Rails Security Basics

## Question

What Rails security basics should a mid-level developer know?

## Brief Answer

Know strong params, authentication, authorization, SQL injection prevention, XSS protection, CSRF protection, safe secret handling, and secure external API token storage.

## Comprehensive Explanation

Rails protects against many issues by default, but developers must still be careful. Use strong parameters to avoid mass assignment. Use parameterized queries or Active Record query methods instead of interpolating SQL. Escape user content in views; be careful with `html_safe`. Rails includes CSRF protection for browser forms.

Authentication verifies identity; authorization checks permissions. For secrets and API tokens, never commit them, never log them, and store them in encrypted credentials or environment/secret managers.

For integrations, protect OAuth tokens, handle revocation, and avoid exposing sensitive errors to clients.

## Practice Prompt

Why is `User.where("email = '#{params[:email]}'")` dangerous?
