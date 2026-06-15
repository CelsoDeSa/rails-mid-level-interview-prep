I asked GPT:
I need to prepare for the technical interview at Dev Pro for a mid level Rails position. As I've been mostly coding with AI for the past 2 years I feel underprepared and the interview is in 2 days (it will take up to 01 hour and half) and I've never been in a tech interview before.

Attached is my latest Resume, I feel it oversells it a bit, but I shared just so you are aware of the technologies I work with. Based on your knowledge of mid level positions, specifically with Rails, and based on what you know about dev.pro interview process, what should I expect and how should I prepare?

GPT repied:
First, you're probably in a better position than you think.

Your resume may oversell a few things, but it doesn't read like someone pretending to be senior. It reads like someone who has spent 4+ years shipping production Rails code, integrating APIs, working with Sidekiq, PostgreSQL, Hotwire, AWS S3, Heroku, and debugging real customer issues. Those are exactly the experiences a mid-level Rails interviewer usually wants to explore.

The bigger risk isn't lack of experience.

It's that AI has become your "second brain" for recalling concepts, and technical interviews temporarily remove that crutch.

---

# What I would expect from Dev.Pro

Dev.Pro is a services/consulting company, not a venture-backed startup trying to hire Rails celebrities.

For a mid-level Rails role, I'd expect some combination of:

### 1. Conversational experience review (20-30 min)

Questions like:

* Tell me about PostPilot
* What did you actually build?
* What's a difficult bug you solved?
* How do you approach a new feature?
* How do you work remotely?
* How do you use AI in your workflow?

This is usually where people underestimate themselves.

You have plenty to talk about:

* Export system overhaul
* Active Storage + S3 migration
* Sidekiq background jobs
* Stripe integrations
* Klaviyo integrations
* PostgreSQL debugging
* Hotwire/Turbo work
* OAuth scheduling engine at Leadster

Those are solid stories.

---

### 2. Rails fundamentals (20-30 min)

This is where I'd focus your preparation.

Expect questions such as:

#### MVC

* Explain MVC in Rails
* What belongs in models?
* What belongs in controllers?
* Why are fat controllers bad?

#### ActiveRecord

* Difference between:

  * `includes`
  * `joins`
  * `preload`
  * `eager_load`

* What is N+1?

Example:

```ruby
users = User.all

users.each do |user|
  puts user.posts.count
end
```

Why is this bad?

---

#### Migrations

Questions like:

* What is a migration?
* How do you add an index?
* Why add indexes?

Know:

```ruby
add_index :users, :email
```

and why it improves lookup performance.

---

#### Associations

Know:

* belongs_to
* has_many
* has_one
* has_many :through

Example:

```ruby
class User
  has_many :orders
end
```

What SQL gets generated?

---

#### Validations

```ruby
validates :email, presence: true
```

vs database constraints.

Very common interview topic.

---

### 3. PostgreSQL basics (10-15 min)

Not DBA level.

But know:

#### Indexes

What problem do they solve?

#### EXPLAIN

What is it used for?

#### Common query optimization

Example:

```sql
SELECT *
FROM users
WHERE email = ?
```

Why index email?

---

### 4. Sidekiq / Background Jobs

You literally have this on your resume. Expect questions.

Know:

#### Why use Sidekiq?

Instead of:

```ruby
ExportService.call
```

inside a request.

Because:

* request timeout
* user waits
* large datasets

---

#### Retry mechanism

What happens if a job fails?

#### Idempotency

Very popular interview question.

Example:

If Stripe webhook arrives twice:

How do you avoid charging twice?

---

### 5. API Integration Questions

You have Stripe and Klaviyo on your resume.

Expect:

* REST vs GraphQL
* GET/POST/PATCH/DELETE
* Authentication
* OAuth basics
* Rate limits
* Error handling

---

### 6. Hotwire

Because you explicitly mention it.

Know:

#### Turbo

What does it solve?

#### Stimulus

When would you use it?

#### Why choose Hotwire instead of React?

---

### 7. Testing

Your resume mentions TDD.

Be careful here.

If someone sees TDD, they may dig deeper.

Be ready to explain:

* unit tests
* integration tests
* request specs
* system specs

Common question:

> What makes a good test?

---

### 8. System Design Lite (Mid-Level)

Not senior architecture.

Questions like:

"Users need to export 5 million records."

Walk through:

1. User clicks export
2. Controller creates job
3. Sidekiq processes
4. CSV generated
5. Upload to S3
6. Email link

You literally implemented something similar.

---

# What they probably WON'T ask

For a mid-level role:

Probably not:

* Red-black trees
* Dynamic programming
* Leetcode hard
* Distributed consensus
* CAP theorem
* Event sourcing

I'd be surprised.

---

# The AI-Assisted Coding Question

This is the part I would prepare for.

Someone may ask:

> How much do you rely on AI?

Don't say:

> Almost everything.

Instead:

> I use AI heavily for implementation speed, boilerplate generation, test generation and research. However, I still own architecture decisions, debugging, production incidents, database analysis, code review and final implementation decisions.

That answer lands much better.

---

# Your 2-Day Crash Plan

## Tonight (2 hours)

Review:

* MVC
* ActiveRecord associations
* N+1
* includes vs joins
* migrations
* validations

---

## Tomorrow (2 hours)

Review:

* Sidekiq
* PostgreSQL indexes
* REST APIs
* OAuth
* Hotwire

---

## Tomorrow night (1 hour)

Prepare stories.

Have answers ready for:

### Biggest technical challenge

Use the export system overhaul.

### Production incident

Use something from PostPilot.

### Difficult bug

Pick a real one.

### Conflict with teammate

Prepare one.

### Using AI

Prepare one.

---

# The one thing I'd do if I were you

Open a blank document and answer, in your own words:

1. What is ActiveRecord?
2. What is N+1?
3. What is Sidekiq?
4. What is Turbo?
5. What is Stimulus?
6. What is an index?
7. What is OAuth?
8. What is a migration?
9. What is TDD?
10. Tell me about the export system project.

If you can explain each of those clearly without AI assistance, you're probably already at the level expected for a mid-level Rails interview.

Based on your experience at PostPilot and Leadster, my estimate is that the interview is more likely to expose gaps in Rails terminology recall than gaps in actual software engineering ability. The next two days should focus on refreshing concepts and practicing explanations, not trying to learn entirely new material.
