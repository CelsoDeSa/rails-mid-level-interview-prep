Score: 0
Probability: high
Type: theory

# What Makes a Good Test

## Question

What makes a good test in a Rails application?

## Brief Answer

A good test verifies meaningful behavior, is reliable, readable, isolated enough, and protects against regressions without being too coupled to implementation details.

## Comprehensive Explanation

Good tests focus on behavior and business rules. Model tests cover validations and domain logic. Request specs cover API/controller behavior, status codes, authentication, and JSON responses. System tests cover critical user flows. Job tests verify async behavior and side effects.

Avoid brittle tests that depend too much on private methods or exact implementation. Use factories/fixtures thoughtfully. Test edge cases and failures, not only happy paths. For bugs, write a regression test that fails before the fix and passes after.

If claiming TDD, be ready to explain the cycle: red, green, refactor. You do not need to practice perfect TDD always, but you should understand how tests guide design.

## Practice Prompt

What would you test for an order creation endpoint?
