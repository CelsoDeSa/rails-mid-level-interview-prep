Score: 0
Probability: medium
Type: theory

# Functional vs Non-Functional Requirements

## Question

What is the difference between functional and non-functional requirements?

## Brief Answer

Functional requirements define what the system should do. Non-functional requirements define how well it should do it: performance, reliability, security, scalability, and usability.

## Comprehensive Explanation

Functional examples:

- users can export contacts
- Google Calendar availability syncs
- Stripe revenue records are imported

Non-functional examples:

- export should support 5 million records
- sync should complete within 5 minutes
- endpoint should respond under 500ms
- tokens must be stored securely
- jobs should retry safely

Mid-level engineers should clarify both. Many technical risks come from unstated non-functional requirements: scale, concurrency, rate limits, timeouts, data integrity, and monitoring.

## Practice Prompt

For a calendar sync feature, list three functional and three non-functional requirements.
