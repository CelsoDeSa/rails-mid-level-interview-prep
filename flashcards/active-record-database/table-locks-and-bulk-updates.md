Score: 0
Probability: medium
Type: debugging

# Table Locks and Bulk Updates

## Question

How can bulk updates or migrations cause production performance problems?

## Brief Answer

Large updates can lock rows or tables, saturate the database, slow queries, and cause request timeouts. Use batched updates, background migrations, and careful deploy steps.

## Comprehensive Explanation

Operations like `update_all`, large backfills, adding constraints, or creating indexes can create locks or heavy load. Even row-level locks can block related writes; some schema changes can lock whole tables depending on database/version/options.

Bad pattern:

```ruby
User.update_all(active: true)
```

on a huge table during peak traffic.

Safer pattern:

```ruby
User.in_batches(of: 1_000) do |relation|
  relation.update_all(active: true)
  sleep 0.1
end
```

For large production changes, use background migrations, monitor DB load, avoid long transactions, and deploy schema changes in compatible phases.

## Practice Prompt

How would you backfill a new `normalized_email` column for millions of users?
