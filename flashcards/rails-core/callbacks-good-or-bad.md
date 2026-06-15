Score: 0
Probability: high
Type: theory

# Rails Callbacks

## Question

Are Rails model callbacks good to use? How can we avoid overusing them?

## Brief Answer

Callbacks are useful for simple data normalization, but heavy side effects in callbacks make code hidden and hard to debug. Prefer explicit service objects for workflows.

## Comprehensive Explanation

Callbacks such as `before_validation` or `before_save` can be reasonable for local record cleanup, like downcasing an email or stripping whitespace. The danger is using callbacks for important side effects: sending emails, charging payments, calling APIs, or destroying related records with complex behavior.

Heavy callbacks create hidden execution chains. Developers may save or destroy a record without realizing many side effects will run. Some operations like `delete_all` skip callbacks while `destroy_all` runs them, which can create surprising differences.

A better pattern is an explicit service class, for example `UserCreator`, that wraps record creation and side effects in a clear transaction and queues background jobs intentionally.

## Practice Prompt

Refactor an `after_commit :send_welcome_email` callback into a service-object flow.
