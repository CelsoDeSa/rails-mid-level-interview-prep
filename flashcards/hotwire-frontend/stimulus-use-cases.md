Score: 0
Probability: medium
Type: theory

# Stimulus Use Cases

## Question

What is Stimulus, and when would you use it in a Rails app?

## Brief Answer

Stimulus is a modest JavaScript framework for adding behavior to server-rendered HTML. Use it for small client-side interactions that do not require a full SPA.

## Comprehensive Explanation

Stimulus connects JavaScript controllers to HTML using data attributes. It is good for dropdowns, modals, auto-submit controls, copy buttons, dynamic form fields, and small UI state.

Example:

```html
<div data-controller="clipboard">
  <button data-action="clipboard#copy">Copy</button>
</div>
```

Stimulus complements Turbo. Turbo handles navigation and partial updates; Stimulus handles local behavior. A good answer should mention progressive enhancement: the HTML should still be meaningful, and JavaScript enhances it.

## Practice Prompt

Give an example of a feature you would build with Stimulus rather than React.
