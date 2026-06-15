Score: 0
Probability: high
Type: theory

# Polymorphism and Duck Typing

## Question

Explain polymorphism and duck typing in Ruby.

## Brief Answer

Polymorphism means different objects can respond to the same method call. Ruby uses duck typing: the object's class matters less than whether it responds to the expected method.

## Comprehensive Explanation

Example:

```ruby
class CsvReport
  def generate
    "csv"
  end
end

class PdfReport
  def generate
    "pdf"
  end
end

reports.each { |report| report.generate }
```

The caller does not care whether the object is a `CsvReport` or `PdfReport`; it only cares that it responds to `generate`.

In Rails, polymorphic associations are another example:

```ruby
class Comment < ApplicationRecord
  belongs_to :commentable, polymorphic: true
end
```

The comments table stores `commentable_type` and `commentable_id`, allowing a comment to belong to different models.

## Practice Prompt

Create a Ruby example where two classes implement the same method and can be used interchangeably.
