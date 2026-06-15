Score: 0
Probability: medium
Type: theory

# Interface Segregation Principle

## Question

How does the Interface Segregation Principle apply in Ruby, which has no formal interfaces?

## Brief Answer

In Ruby, ISP means keeping modules and public APIs small and focused so objects do not depend on methods they do not need.

## Comprehensive Explanation

Bad:

```ruby
module Worker
  def code; end
  def design; end
  def deploy; end
end
```

Classes including this module may get methods that do not belong to them. Better:

```ruby
module Coder
  def code; end
end

module Deployable
  def deploy; end
end
```

In Rails, this applies to concerns. A giant `TrackableAndSearchableAndExportable` concern becomes hard to reason about. Prefer cohesive concerns or plain service objects.

## Practice Prompt

What makes a Rails concern too broad?
