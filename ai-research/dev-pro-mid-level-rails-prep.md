# Dev.Pro Mid-Level Rails Interview Prep

## What to expect from Dev.Pro

Public information about Dev.Pro suggests a process like:

1. **Recruiter intro call**
   - English level
   - salary/rate expectations
   - availability
   - project fit
   - high-level experience

2. **Experience / soft-skills interview**
   - collaboration
   - client communication
   - problem solving
   - examples from past work
   - ability to explain trade-offs

3. **Technical evaluation**
   - likely 45–60 minutes
   - practical Rails/backend questions
   - maybe code discussion, maybe live problem solving, maybe take-home review
   - not necessarily heavy algorithm trivia

4. **Possible client interview**
   - project-specific fit
   - communication style
   - confidence explaining your experience

Dev.Pro appears to care a lot about **practical problem-solving, English communication, and client-readiness**, not only framework trivia.

## Biggest risk

The biggest risk is not that you used AI. The bigger risk is sounding like you **cannot independently reason about your own code**.

Preparation should focus on:

- explaining Rails decisions clearly
- debugging without AI
- talking through trade-offs
- reading/modifying code under pressure
- being honest about AI use without sounding dependent

Good framing:

> “I use AI as a productivity tool, mostly for scaffolding, exploration, refactoring ideas, and speeding up routine work. But I’m responsible for reviewing, testing, debugging, and understanding what ships. I’m comfortable explaining the architecture, trade-offs, and failure modes of the code I work on.”

Avoid:

> “AI writes most of my code.”

Say:

> “AI accelerates me, but I still own the implementation.”

## What they may ask for a mid-level Rails role

### Rails fundamentals

Be ready to explain:

- MVC flow in Rails
- routing and REST conventions
- controllers vs models vs services
- validations vs database constraints
- callbacks: when useful, when dangerous
- concerns: when useful, when overused
- Active Record associations
- scopes
- migrations
- transactions
- N+1 queries
- eager loading with `includes`, `preload`, `eager_load`
- background jobs
- caching basics
- authentication/authorization patterns
- Rails security basics

Example questions:

- “What happens when a request hits a Rails app?”
- “How do you avoid N+1 queries?”
- “When would you use a service object?”
- “What is the difference between validation and database constraints?”
- “How would you handle a slow endpoint?”
- “How do you organize business logic in Rails?”

### Ruby fundamentals

Expect practical Ruby questions:

- blocks, procs, lambdas
- modules and mixins
- `include` vs `extend`
- symbols vs strings
- enumerable methods
- exceptions
- object-oriented design
- `nil` handling
- keyword arguments
- immutability basics

Example questions:

- “What is the difference between `map`, `select`, and `each`?”
- “What is a module used for?”
- “What is the difference between a class method and instance method?”
- “How does Ruby handle truthiness?”
- “What is a block?”

### Database / PostgreSQL

Mid-level Rails interviews often test whether you can reason about data.

Prepare:

- indexes
- foreign keys
- unique constraints
- transactions
- joins
- query optimization
- pagination
- avoiding expensive queries
- schema design

Example questions:

- “How would you design users, posts, comments, and likes?”
- “How would you enforce unique email addresses?”
- “How do you debug a slow SQL query?”
- “What is an index and when can it hurt performance?”
- “What is a database transaction?”

### Testing

Know enough RSpec/Minitest concepts:

- model specs
- request specs
- system tests
- factories/fixtures
- mocking/stubbing basics
- testing happy path and edge cases
- avoiding brittle tests

Example questions:

- “How do you test a Rails API endpoint?”
- “What would you test in a model?”
- “What is the difference between unit and integration tests?”
- “How do you test background jobs?”

### APIs

For mid-level Rails, be ready to design a simple API.

Know:

- RESTful routes
- status codes
- JSON responses
- validations/errors
- authentication
- pagination
- filtering/sorting
- idempotency
- versioning basics

Example:

> “Design an endpoint to create an order.”

Mention:

- `POST /orders`
- authenticated user
- strong params
- model validations
- transaction
- clear error responses
- background job for confirmation email/payment
- tests

### Background jobs

If you mention Sidekiq/Active Job, prepare:

- why use background jobs
- retries
- idempotency
- failures
- queues
- avoiding passing full objects
- passing IDs instead

Example answer:

> “I use background jobs for work that doesn’t need to block the request, like emails, webhooks, reports, or external API calls. I try to make jobs idempotent because retries can happen.”

### Hotwire / Turbo / Stimulus

Since your stack includes Rails 8, Hotwire, and Tailwind, be ready for:

- Turbo Drive
- Turbo Frames
- Turbo Streams
- Stimulus controllers
- progressive enhancement
- when Hotwire is enough vs when React/Vue may be better

Good explanation:

> “Hotwire lets me keep most complexity server-side while still delivering dynamic UX. I’d use Turbo Frames for partial page updates, Turbo Streams for real-time or multi-target updates, and Stimulus for small client-side behavior.”

## Two-day preparation plan

### Day 1 — Rails core + your story

1. Prepare your self-introduction:

> “I’m a Rails-focused developer with experience building web applications using Ruby on Rails, PostgreSQL, Hotwire, Tailwind, and modern deployment practices. Recently I’ve worked a lot with AI-assisted development, but I stay focused on understanding the code, testing behavior, and making pragmatic product decisions. I’m strongest in building practical features quickly, improving UX, and debugging across the Rails stack. I’m looking for a mid-level role where I can contribute reliably and keep growing with a strong team.”

2. Prepare 3 project stories using STAR:
   - A Rails feature you built
   - A bug/performance issue you fixed
   - A time you had ambiguity or had to learn quickly

3. Review Rails fundamentals:
   - routes/controllers/models/views
   - Active Record associations
   - validations
   - migrations
   - scopes
   - transactions
   - N+1 queries
   - service objects
   - background jobs

4. Practice explaining out loud:
   - “Explain MVC in Rails.”
   - “How does a request flow through Rails?”
   - “How do you debug a production bug?”
   - “How do you improve a slow Rails page?”
   - “How do you decide where business logic belongs?”

### Day 2 — mock interview + weak spots

1. Mentally build or review a tiny Rails feature:

> Users can create projects. Projects have tasks. Tasks can be completed. Send an email when all tasks are complete.

Be able to describe:

- tables
- models
- associations
- validations
- controller actions
- routes
- background job
- tests
- edge cases

2. Practice live coding basics without AI:
   - reverse a string
   - count words
   - group array values
   - find duplicates
   - implement simple filtering
   - parse a hash/array
   - use `map`, `select`, `reduce`, `group_by`

Example:

```ruby
orders.group_by(&:status).transform_values(&:count)
```

3. Review SQL:

```sql
SELECT users.id, COUNT(posts.id)
FROM users
LEFT JOIN posts ON posts.user_id = users.id
GROUP BY users.id;
```

Know joins, indexes, unique constraints, and transactions.

4. Prepare questions to ask them:
   - “What does success look like for this role in the first 3 months?”
   - “How is code reviewed?”
   - “Is the project more maintenance, new feature development, or modernization?”
   - “What Rails version and frontend approach does the team use?”
   - “How much direct client communication is expected?”
   - “What are the biggest technical challenges on the project?”

## How to handle resume overstatement

Do not apologize or confess broadly. Calibrate honestly.

If asked about something you used lightly:

> “I’ve used it in a practical context, but I wouldn’t call myself an expert. I understand the main workflow and can be productive with documentation.”

If asked about something AI helped with:

> “I used AI to speed up implementation, but I reviewed the generated code, adapted it to the app, tested it, and debugged the issues.”

If you don’t know:

> “I haven’t handled that exact case before, but I’d approach it by checking the Rails docs, reproducing the issue locally, writing a small test, and validating the fix before shipping.”

That sounds mid-level. Pretending does not.

## High-priority topics to cram

1. Rails request lifecycle
2. Active Record associations and queries
3. N+1 and performance debugging
4. REST API design
5. Validations vs DB constraints
6. Transactions
7. Background jobs/idempotency
8. Testing strategy
9. Security basics
10. Your project stories

## Likely interview questions with short answer angles

### “How do you debug a slow Rails endpoint?”

Mention:

- reproduce locally/logs
- check Rails logs and SQL queries
- look for N+1
- use `includes`
- inspect indexes
- measure before/after
- add caching/background job if needed
- add regression test if possible

### “Where do you put business logic?”

Good answer:

> “Simple logic can stay in the model if it belongs to the domain object. If the workflow coordinates multiple models, external APIs, or side effects, I usually extract a service object or command-style object. I try not to put complex business logic in controllers.”

### “How do you prevent invalid data?”

Mention both:

- Rails validations for user feedback
- database constraints for integrity

Example:

> “For unique email, I’d use a Rails uniqueness validation and a unique database index, because validations alone can have race conditions.”

### “How do you handle background job retries?”

Mention:

- jobs should be idempotent
- pass IDs, not full objects
- handle missing records
- avoid duplicate side effects
- log failures
- use retry/dead queue behavior

### “What do you test?”

Mention:

- model validations/business rules
- request specs for endpoints
- system specs for critical user flows
- job specs for async behavior
- edge cases and regressions

## Interview strategy

You do not need to sound senior. For mid-level, aim to show:

- you can build features
- you understand Rails conventions
- you know common pitfalls
- you communicate clearly
- you ask good questions
- you can be honest about gaps
- you can work with clients/team members

Keep this sentence in mind:

> “I may not know every answer instantly, but I can reason through the problem, communicate clearly, and validate the solution.”
