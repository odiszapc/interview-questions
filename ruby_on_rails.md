# Ruby
#### What kinds of variables are declared in Ruby?
> Local – foobar

> Instance - @foobar

> Class - @@foobar

> Global - $foobar

####What is the difference between these two lines
```ruby
foobar = 1
FOOBAR = 1
```
> The last one is a constant, its value can not be changed.

####What is the difference between “and” and && operators in Ruby?
> They are the same but “and” has lower precedence

####What is the difference between method overloading and method overwriting?

####Whai is the use of load() and requre() methods in Ruby?
> Load() is used to execute code, require() is used to import libraries

####How does nil and false differ?
> nil is not a value, where false is. False is a boolean type, where nil is not. Nil is an object for NilClass, false is an object of FalseClass

####Whats the difference between Symbol and String?
> Symbol helps to save memory and CPU time. String are considered  as mutable objects. Whereas, symbols, belongs to the category of immutable. 

####Is there any kind of multiple inheritance in Ruby?
> Ruby support only single inheritance

####What’s the difference between include and extend techniques?
> Include makes the module’s method available to the instance of a class. 

> Extend make these methods available to the class itslef

####What is the difference between lambda and proc?
> Proc object treat itslef more likely to Ruby block. Whereas Lambda is like a method call.

```ruby
# Proc
def test
  1.times { return }	# return from method (not block) (LocalJumpError)
end

def test
  Proc.new { return }  # risk of LocalJumpError
End

# Lambda
def test
  lambda { return }	# safe
end
```

####What is a Meta-programming? How you’re using it inside your application?
> A significant part of Rails is based on meta programming. For example all Active record features like relationships, validations is injected into models via meta-programming

####Differenct between Ruby 1.8 and 1.9?
> Performance (move from Matx to YARV virtual machine)
> Threads/Fibers
> Encoding/Unicode
> gems are built-in now
> {"a","b"} No Longer Supported
```
{1,2}          # 1.8
=> {1=>2}
```

> Array.to_s now Contains Punctuation
```ruby
[1,2,3].to_s
=> "[1, 2, 3]" # 1.9
=> "123"       # 1.8
```

> Colon No Longer Valid In When Statements
```ruby
case 'a'; when /\w/: puts 'word'; end
word                          # 1.8
syntax error, unexpected ':'  # 1.9
```

> Block variables now shadow local variables
```ruby
i=0; [1,2,3].each {|i|}; i
=> 0 # 1.9
=> 3 # 1.8
```

> Hash.index deprecated (use Hash.key)
```ruby
{1=>2}.index(2)
=> 1 # 1.8
```

> Fixnum.to_sym removed

> Hash keys now unordered
```ruby
{:a=>"a", :c=>"c", :b=>"b"}
=> {:a=>"a", :c=>"c", :b=>"b"} # 1.9
=> {:a=>"a", :b=>"b", :c=>"c"} # 1.8
```

> Stricter Unicode Regular Expressions

> instance_methods now an Array of Symbols (replace instance_methods.include? with method_defined?)
```ruby
{}.methods.sort.last
=> :zip  # 1.9
=> "zip" # 1.8
```

> Source file encoding
```
# coding: utf-8
```

> Real threading

> Alternate syntax for symbol as Hash Keys
```ruby
{a: b}    # 1.9
{:a => b} # 1.8
```

> Inject Methods
```ruby
[1,2].inject(:+) # 1.9
[1,2].inject {|a,b| a+b} # 1.8
```

> to_enum added
```ruby
[1, 2, 3].to_enum # 1.9
e = [1,2,3].each # 1.9
```

> Lambda shorthand
```ruby
p = -> a,b,c {a+b+c} # 1.9
puts p.(1,2,3)       # 1.9
puts p[1,2,3]        # 1.9
p = lambda {|a,b,c| a+b+c} # 1.8
puts p.call(1,2,3)         # 1.8
```

> Complex Numbers
```ruby
Complex(3,4) == 3 + 4.im # 1.9
```

> Regex “Properties”
```ruby
/\p{Space}/ # 1.9
/[:space:]/ # 1.8
```

> Fibers

> Break Values

> “Nested” Methods
```ruby
def toggle
  def toggle
    "subsequent times"
  end
  "first time"
end
```

####What’s new in Ruby 2.0
> Keyword arguments
```ruby
def wrap(string, before: "<", after: ">")
  "#{before}#{string}#{after}"
end
```

> Refinements (experimental)
```ruby
module NumberQuery
  refine String do
    def number?
      match(/\A[1-9][0-9]*\z/) ? true : false
    end
  end
end
# ...
using NumberQuery
"123".number?
```

> Module#prepend
```ruby
Object
superclass
included module
class
prepended module
```

> Enumerable#lazy

> Rubygems Gemfile support

> RDoc markdown support

> Asynchronous Thread interrupt handling

> GС improvements

> Default UTF-8 encoding

> Binary string shortcut
```ruby
s = "foo"
s.encoding     #=> #<Encoding:UTF-8>
s.b.encoding   #=> #<Encoding:ASCII-8BIT>
```

> RegExp engine is changed to Onigmo

####What’s new in Ruby 2.1?
> Refinements are not experimental now

> Decimal literals
```ruby
0.1 * 3                # <2.0
=> 0.30000000000000004 # <2.0
###################
0.1r        # 2.1
=> (1/10)   # 2.1
0.1r * 3    # 2.1
=> (3/10)   # 2.1
```

> Frozen String Literals
```ruby
input == "bar"f
```

> Required Keyword Arguments
```ruby
def foo(a: 10) # 2.0
def foo(a:)    # 2.1
```

> Method Definition returns Method Name
```ruby
def foo() end # => nil    # <2.1
def foo() end # => :foo   # 2.1
```

> Faster Numbers for Serious Math using GNU MPA lib


# Rails
