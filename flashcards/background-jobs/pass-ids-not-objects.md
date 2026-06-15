Score: 0
Probability: high
Type: theory

# Pass IDs, Not Objects

## Question

Why should you pass IDs instead of Active Record objects to background jobs?

## Brief Answer

Jobs are serialized and may run later. Passing IDs keeps payloads small and lets the job reload current database state, handling deleted or changed records safely.

## Comprehensive Explanation

Bad:

```ruby
WelcomeEmailJob.perform_async(user)
```

Good:

```ruby
WelcomeEmailJob.perform_async(user.id)
```

Inside the job:

```ruby
def perform(user_id)
  user = User.find_by(id: user_id)
  return unless user

  UserMailer.welcome(user).deliver_now
end
```

Passing full objects can serialize stale data, produce large payloads, and fail unpredictably if the record changes or is deleted before the job runs.

## Practice Prompt

What should a job do if the record ID no longer exists?
