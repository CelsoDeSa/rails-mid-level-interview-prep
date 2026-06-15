Score: 0
Probability: high
Type: theory

# Migrations and Schema Changes

## Question

What is a Rails migration, and what should you consider when changing a production database schema?

## Brief Answer

A migration is a versioned database schema change. In production, consider data size, locks, indexes, reversibility, deploy order, and avoiding long blocking operations.

## Comprehensive Explanation

Migrations let Rails evolve the database schema over time:

```ruby
class AddEmailToUsers < ActiveRecord::Migration[8.0]
  def change
    add_column :users, :email, :string
    add_index :users, :email, unique: true
  end
end
```

Production concerns:

- adding indexes on large tables can lock or slow writes unless done carefully
- adding `NOT NULL` columns requires defaults/backfills in safe steps
- backfilling large data should often happen in batches/background jobs
- migrations should be reversible when possible
- app deploy and DB changes must be compatible during rolling deploys

A mid-level answer should show you understand migrations are code, but they operate on live data and can affect availability.

## Practice Prompt

How would you add a required `status` column to a large `orders` table safely?
