Score: 0
Probability: high
Type: theory

# SOLID Overview

## Question

What are the SOLID principles? Give a short Rails example for each.

## Brief Answer

SOLID means Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion. They guide maintainable object-oriented design.

## Comprehensive Explanation

**S — Single Responsibility:** one class should have one reason to change. Keep controllers thin; extract payment/export/sync workflows to services.

**O — Open/Closed:** open for extension, closed for modification. Add new report formatters through polymorphism instead of editing a giant `case` statement.

**L — Liskov Substitution:** subclasses should be usable wherever the parent is expected without breaking behavior. Do not make a subclass violate parent expectations.

**I — Interface Segregation:** objects should not depend on methods they do not use. In Ruby, prefer small focused modules over giant concerns.

**D — Dependency Inversion:** high-level code should depend on abstractions/collaborators, not hardcoded concrete classes. Inject gateways or clients for easier testing and swapping.

## Practice Prompt

Pick one SOLID principle and explain how it prevents a real Rails maintenance problem.
