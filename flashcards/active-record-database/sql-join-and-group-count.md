Score: 0
Probability: high
Type: coding

# SQL Join and Group Count

## Question

Write a PostgreSQL query to return each user email and the number of orders they have.

## Brief Answer

Use `LEFT JOIN`, `COUNT`, and `GROUP BY`.

## Comprehensive Explanation

```sql
SELECT users.email, COUNT(orders.id) AS total_orders
FROM users
LEFT JOIN orders ON orders.user_id = users.id
GROUP BY users.id, users.email;
```

Use `LEFT JOIN` if you want users with zero orders included. Use `INNER JOIN` if you only want users that have at least one order. In PostgreSQL, grouping by `users.id` may be enough if `email` is functionally dependent on the primary key, but grouping both is explicit and portable.

Add `HAVING` for aggregate filters:

```sql
SELECT users.email, COUNT(orders.id) AS total_orders
FROM users
LEFT JOIN orders ON orders.user_id = users.id
GROUP BY users.id, users.email
HAVING COUNT(orders.id) > 5;
```

## Practice Prompt

Modify the query to return only users with more than 10 orders.
