I asked:
Explain SOLID with brief Ruby/Rails examples

Gemini replied:
SOLID is an acronym representing five design principles in Object-Oriented Programming (OOP) that make software more understandable, flexible, and maintainable.
Here is a breakdown of each principle with brief Ruby/Rails examples.
1. Single Responsibility Principle (SRP)
Definition: A class should have only one reason to change, meaning it should have only one job or responsibility.
Violation in Rails: A Fat Model that handles database logic, business logic, and sending emails.



Ruby
# Bad
class User < ApplicationRecord
  def calculate_tax
    # complex tax logic
  end

  def send_welcome_email
    # email sending logic
  end
end


Good Ruby/Rails Example: Extracting responsibilities into separate Service Objects or Mailers.



Ruby
# Good
class User < ApplicationRecord
  # Only handles data/DB concerns
end

class TaxCalculator
  def initialize(user)
    @user = user
  end

  def calculate
    # complex tax logic here
  end
end

class UserMailer < ApplicationMailer
  def welcome_email(user)
    # email sending logic
  end
end


2. Open-Closed Principle (OCP)
Definition: Software entities (classes, modules, functions) should be open for extension but closed for modification. You should be able to add new functionality without changing existing code.
Violation in Ruby: Hardcoding specific types using a case statement, meaning you must modify the class every time a new type is introduced.



Ruby
# Bad
class ReportGenerator
  def generate(type)
    case type
    when :pdf
      # generate PDF
    when :csv
      # generate CSV
    end
  end
end


Good Ruby/Rails Example: Using Polymorphism and Duck Typing. You can add new report types without ever touching the ReportGenerator class.



Ruby
# Good
class ReportGenerator
  def generate(formatter)
    formatter.generate_report
  end
end

class PdfFormatter
  def generate_report
    # generate PDF
  end
end

class CsvFormatter
  def generate_report
    # generate CSV
  end
end


3. Liskov Substitution Principle (LSP)
Definition: Objects of a superclass should be replaceable with objects of its subclasses without breaking the application. Subclasses must behave in the way the parent class is expected to behave.
Violation in Ruby: A subclass that changes the return type or raises unexpected exceptions for methods defined in the parent class.



Ruby
# Bad
class Bird
  def fly
    "I'm flying!"
  end
end

class Penguin < Bird
  def fly
    raise "I can't fly!" # Breaks the expectation of the Bird class
  end
end


Good Ruby/Rails Example: Refactoring the class hierarchy so that subclasses adhere to the behavior expected from their parent interfaces.



Ruby
# Good
class Bird
  # generic bird methods
end

class FlyingBird < Bird
  def fly
    "I'm flying!"
  end
end

class Penguin < Bird
  def swim
    "I'm swimming!"
  end
end


4. Interface Segregation Principle (ISP)
Definition: Clients should not be forced to depend on methods they do not use. Since Ruby does not have formal "Interfaces" like Java or C#, this usually translates to not creating "fat" classes or modules that force objects to implement unused methods.
Violation in Ruby: A module that groups too many unrelated behaviors together.



Ruby
# Bad
module Worker
  def code; end
  def test; end
  def design; end
end

class Programmer
  include Worker
  # Has to implement #design even if they only code and test
end


Good Ruby/Rails Example: Segregating behaviors into smaller, highly cohesive modules so classes only include what they need.



Ruby
# Good
module Coder
  def code; end
end

module Tester
  def test; end
end

class Programmer
  include Coder
  include Tester
end


5. Dependency Inversion Principle (DIP)
Definition: High-level modules should not depend on low-level modules; both should depend on abstractions. In Ruby, this usually means utilizing Dependency Injection rather than hardcoding dependencies inside a class.
Violation in Ruby: Hardcoding a specific service dependency inside a class, making it hard to test or swap out.



Ruby
# Bad
class PaymentProcessor
  def initialize(amount)
    @amount = amount
    @gateway = StripeGateway.new # Hardcoded dependency
  end

  def process
    @gateway.charge(@amount)
  end
end


Good Ruby/Rails Example: Injecting the dependency into the constructor. This allows you to easily swap StripeGateway with PaypalGateway or a MockGateway for testing.



Ruby
# Good
class PaymentProcessor
  def initialize(amount, gateway:)
    @amount = amount
    @gateway = gateway # Dependency injected
  end

  def process
    @gateway.charge(@amount)
  end
end

# Usage:
PaymentProcessor.new(100, gateway: StripeGateway.new).process
