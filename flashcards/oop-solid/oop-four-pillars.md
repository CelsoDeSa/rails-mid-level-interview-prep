Score: 0
Probability: high
Type: theory

# OOP Four Pillars

## Question

What are the four pillars of Object-Oriented Programming, and how do they appear in Ruby/Rails?

## Brief Answer

The four pillars are encapsulation, abstraction, inheritance, and polymorphism. In Rails they appear through models/services hiding behavior, Active Record abstractions, inheritance from framework base classes, modules, duck typing, and polymorphic associations.

## Comprehensive Explanation

**Encapsulation** means keeping data and behavior together while hiding internal implementation details. In Ruby this includes private methods, controlled accessors, and service objects that hide complex workflows.

**Abstraction** means exposing a simple public interface while hiding complexity. Active Record is a major Rails abstraction: `User.where(active: true)` hides SQL construction and result mapping.

**Inheritance** lets a class reuse behavior from a parent class. Rails uses this constantly: `User < ApplicationRecord`, `ApplicationController < ActionController::Base`. Ruby supports single inheritance, so modules are often used to share behavior.

**Polymorphism** means different objects can respond to the same message in their own way. Ruby uses duck typing: if objects respond to `generate`, callers do not need to know their exact class. Rails also has polymorphic associations, such as a `Comment` belonging to either a `Post` or an `Image` through `commentable_type` and `commentable_id`.

## Practice Prompt

Explain each OOP pillar using one Ruby or Rails example.
