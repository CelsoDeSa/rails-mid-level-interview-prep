Score: 0
Probability: medium
Type: theory

# DNS, Nginx, Puma, Production

## Question

How does a Rails app go from localhost to being accessible by a real domain in production?

## Brief Answer

Deploy the app to a server/platform, point DNS to the server/load balancer, use a web server/proxy like Nginx, run Rails via Puma, and connect to production services like PostgreSQL and Redis.

## Comprehensive Explanation

When a user enters a domain, DNS resolves it to an IP/load balancer. A web server such as Nginx receives HTTP/HTTPS traffic, handles TLS/static files/proxying, and forwards dynamic requests to Puma, the Rails app server. Puma runs the Rails app, which talks to PostgreSQL, Redis, storage, and external APIs.

Production also needs environment variables/secrets, migrations, asset compilation, logging, monitoring, background workers, and deployment automation/CI.

## Practice Prompt

What is the difference between Nginx and Puma?
