Score: 0
Probability: medium
Type: coding

# Reverse String and Count Words

## Question

Write Ruby methods to reverse a string and count word frequencies in a sentence.

## Brief Answer

Use `reverse` for a simple string reversal. For word counts, normalize, split, and count with a Hash default.

## Comprehensive Explanation

Simple reverse:

```ruby
def reverse_string(text)
  text.reverse
end
```

Word frequency:

```ruby
def word_counts(sentence)
  words = sentence.downcase.scan(/\b[\w']+\b/)

  words.each_with_object(Hash.new(0)) do |word, counts|
    counts[word] += 1
  end
end
```

Interview angle: talk through edge cases: case sensitivity, punctuation, empty strings, Unicode, and whether contractions count as one word.

## Practice Prompt

Implement `word_counts("Hello, hello world!")` so it returns `{ "hello" => 2, "world" => 1 }`.
