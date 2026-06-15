Score: 0
Probability: medium
Type: theory

# Docker Purpose

## Question

What is Docker, and how does it help with “it works on my machine” problems?

## Brief Answer

Docker packages an app with its runtime and dependencies into a container so it runs consistently across environments.

## Comprehensive Explanation

Docker containers isolate the application environment: OS libraries, Ruby version, system packages, and app dependencies. This reduces differences between development, staging, and production.

For Rails, Docker can define services like app, PostgreSQL, Redis, and workers. It helps onboarding and deployment consistency. It is not magic: you still need correct environment variables, persistent volumes, networking, secrets, and production configuration.

## Practice Prompt

Explain the difference between an image and a container.
