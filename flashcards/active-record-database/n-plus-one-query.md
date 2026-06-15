Score: 0
Probability: high
Type: debugging

# N+1 Queries

## Question

What is an N+1 query in Rails and how do you fix it?

## Brief Answer

An N+1 query happens when one query loads parent records and then one extra query runs per parent for an association. Fix it with eager loading such as `includes`, or with joins when filtering/sorting by the association.

## Comprehensive Explanation

Example problem:

```ruby
users = User.all
users.each { |user| puts user.company.name }
```

This runs 1 query for users and N queries for companies. Use:

```ruby
users = User.includes(:company)
users.each { |user| puts user.company.name }
```

`includes` usually loads associations in separate queries and stores them in memory. `joins` creates SQL joins and is useful for filtering or ordering by associated tables, but it does not automatically preload association objects for later access.

Mention how to detect N+1: Rails logs, Bullet gem, query counts, APM tools, and slow endpoint investigation.

## Practice Prompt

Given users and posts, rewrite code that prints each user's post titles without N+1 queries.
