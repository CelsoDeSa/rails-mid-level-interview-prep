Score: 0
Probability: medium
Type: theory

# Numeric Types, Float, and BigDecimal

## Question

What numeric classes does Ruby have, and why should you avoid `Float` for money?

## Brief Answer

Ruby has `Integer`, `Float`, `Rational`, `Complex`, and `BigDecimal` via the standard library. Avoid `Float` for money because binary floating-point can introduce precision errors; use integer cents or `BigDecimal`.

## Comprehensive Explanation

Ruby numeric hierarchy includes `Numeric` as a base class, with common subclasses like `Integer` and `Float`. `BigDecimal` is used for decimal precision:

```ruby
require "bigdecimal"

BigDecimal("10.25") + BigDecimal("0.10")
```

Floats are approximate:

```ruby
0.1 + 0.2 # may not equal exactly 0.3
```

For money in Rails, common approaches are storing integer cents (`amount_cents`) or using decimal columns with appropriate precision/scale. Never rely on float columns for billing/accounting.

## Practice Prompt

How would you store Stripe charge amounts in PostgreSQL?
