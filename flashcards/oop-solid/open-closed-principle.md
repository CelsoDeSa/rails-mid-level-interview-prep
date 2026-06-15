Score: 0
Probability: medium
Type: theory

# Open/Closed Principle

## Question

Explain the Open/Closed Principle with a Ruby example.

## Brief Answer

Code should be open for extension but closed for modification. Add new behavior by introducing new classes/modules rather than repeatedly editing stable code.

## Comprehensive Explanation

Bad:

```ruby
class ReportGenerator
  def generate(type)
    case type
    when :csv then generate_csv
    when :pdf then generate_pdf
    end
  end
end
```

Every new report type requires modifying `ReportGenerator`.

Better:

```ruby
class ReportGenerator
  def generate(formatter)
    formatter.generate
  end
end

class CsvFormatter
  def generate
    # csv
  end
end

class PdfFormatter
  def generate
    # pdf
  end
end
```

Now new formats can be added as new formatter classes. The stable orchestration code does not change.

## Practice Prompt

How would you design export formats so adding XLSX does not require changing CSV code?
