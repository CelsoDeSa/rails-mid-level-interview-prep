Score: 0
Probability: medium
Type: theory

# SQL vs NoSQL

## Question

What is the difference between SQL and NoSQL databases, and when would you choose each?

## Brief Answer

SQL databases use structured relational schemas and are strong for integrity, joins, transactions, and complex queries. NoSQL databases are more flexible for document-like or high-scale unstructured data, but can trade away strict consistency and schema enforcement.

## Comprehensive Explanation

PostgreSQL stores data in tables with defined schemas, relationships, constraints, and ACID transactions. It is a strong choice for billing, users, orders, integrations, and reporting where data correctness matters.

NoSQL databases like MongoDB store flexible document structures. They can be useful when the shape of data varies heavily, when horizontal scaling is a primary concern, or when document access patterns are simple and well-defined.

Avoid saying “NoSQL is always faster.” Performance depends on access patterns, indexes, data model, query shape, and operational constraints. A flexible schema can also allow malformed data if the application writes bad structures.

## Practice Prompt

Would you choose PostgreSQL or MongoDB for Stripe billing records? Why?
