Score: 0
Probability: high
Type: theory

# Turbo Drive, Frames, and Streams

## Question

What are Turbo Drive, Turbo Frames, and Turbo Streams?

## Brief Answer

Turbo Drive speeds normal navigation, Turbo Frames update isolated page sections, and Turbo Streams send DOM changes like append/replace/remove to one or more targets.

## Comprehensive Explanation

Turbo Drive intercepts link clicks and form submissions to replace the page body without a full browser reload.

Turbo Frames define independent page regions. A link or form inside a frame can update only that frame:

```erb
<%= turbo_frame_tag "comments" do %>
  ...
<% end %>
```

Turbo Streams represent DOM operations, often returned after form submissions or broadcast asynchronously:

```erb
<%= turbo_stream.append "comments", @comment %>
```

Use Hotwire when server-rendered Rails can deliver the UX with less frontend complexity. Use heavier frontend frameworks when the client-side state and interactions are genuinely complex.

## Practice Prompt

When would you use a Turbo Frame instead of a Turbo Stream?
