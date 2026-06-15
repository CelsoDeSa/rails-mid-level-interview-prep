Score: 0
Probability: high
Type: theory

# Where to Put Business Logic

## Question

Where do you put business logic in a Rails app, and when do you extract service objects?

## Brief Answer

Simple domain behavior can live in models. Multi-step workflows, external API calls, side effects, or logic coordinating several models should usually move to a service object.

## Comprehensive Explanation

Rails encourages rich models, but not every workflow belongs in an Active Record model. A model is a good place for validations, associations, scopes, and behavior tightly related to the record. Controllers should not contain complex business logic; they should coordinate the request.

Use service objects when the operation has a clear verb-like workflow: `CreateOrder`, `ExportContacts`, `StripeRevenueSync`, or `CalendarAvailabilitySync`. This improves testability, keeps controllers small, avoids fat models, and makes dependencies explicit.

An interview-ready answer should include trade-offs: service objects can become a dumping ground if not named clearly or if every tiny method becomes a service. Extract when it improves clarity.

## Practice Prompt

Design a service object for exporting a large CSV and uploading it to S3.
