Score: 0
Probability: high
Type: system-design

# API Pagination, Filtering, and Sorting

## Question

How would you design pagination, filtering, and sorting for a Rails JSON API endpoint?

## Brief Answer

Accept explicit params for page/limit, filters, and sort fields. Validate allowed values, use indexes for common filters/sorts, and return metadata with results.

## Comprehensive Explanation

Example endpoint:

```http
GET /api/orders?status=paid&page=2&per_page=25&sort=-created_at
```

Controller/service concerns:

- whitelist filter params (`status`, `created_after`, etc.)
- whitelist sortable columns to avoid SQL injection
- apply pagination with limit/offset or cursor-based pagination
- return metadata such as current page, total count, or next cursor
- add database indexes for common access patterns

Offset pagination is simple but can become slow or inconsistent on very large changing datasets. Cursor pagination is better for large feeds or exports.

## Practice Prompt

Design params and response metadata for `GET /api/users` with filtering by role and sorting by creation date.
