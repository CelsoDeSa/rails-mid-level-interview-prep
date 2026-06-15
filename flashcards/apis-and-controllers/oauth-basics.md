Score: 0
Probability: medium
Type: theory

# OAuth Basics

## Question

Explain OAuth at a high level. How would you handle token refresh and failures?

## Brief Answer

OAuth lets a user grant your app limited access to another service without sharing their password. Store access/refresh tokens securely, refresh expired tokens, handle revocation, and retry carefully.

## Comprehensive Explanation

Typical OAuth flow: user is redirected to the provider, grants permissions, provider redirects back with a code, your server exchanges the code for access and refresh tokens. Access tokens are short-lived; refresh tokens allow getting new access tokens.

In Rails, token values must be protected and never logged. Track expiry time. Before an API call, refresh if expired. Handle revoked tokens by marking the integration disconnected and asking the user to reconnect. For rate limits or transient provider errors, use retry with backoff, ideally in a background job.

## Practice Prompt

How would you design a Google Calendar integration that keeps working after access tokens expire?
