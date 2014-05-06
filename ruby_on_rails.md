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
###Why Ruby on Rails?
> DRY principal

> Convention over Configuration

> Gems and Plugins

> Scaffolding

> Pure OOP Concept

###What is MVC? How does it work?
> MVC tends for Model-View-Controlles. MVC flow goes like this: request forst comes to the controller, controller finds an appropriate view, your view interacts with model, model interacts with database. Basically if you URL is something like

> http://localhost:3000/users/new

> user is your controller, new is your method, there must be a file in your view/users folder named new.html.erb, so, once the submit button is pressed, User model or whatwever defined in the rhtml form_for syntax, will be called and values will be stored into the database

###What is Ruby Gems?
> Ruby Gem is a software package called a “gem”. Gem contains packaged Ruby application or native application wrapped with Ruby interface. Ruby Gems software itself allows user ot easly dowload, install and manipulate gems on your system

###What is Bundler?
> Bundelr helps to you manage your gems for the applciation. After specifying gems in a certain configuratin file , you need to execute a bundle install command. It will use already installed gems aor download new ones from repository. Default repository is rubygems.org.

###What is Gemfile and Gemfile.lock?
> The Gemfile is where you specify which gems and versions you want to use. The Gemfile.lock is where Bundler records the exact versions that were installed. This way, when the same application is loaded on another machinem running bundle install will look at the Gemfile.lock and isntall the exact same versions to achieve the same application environment. The user should not ever have to directly edit thee lock file.

###What is ORM in Rails? What is ActiveRecord?
> ORM tends for Object-Relationship-Model, it basically means that your classes are mapped to table in the database and objects are directly mapped to the rows int the table.

> Activerecord is a smart ORM implementations bunlded with Ruby on Rails. Main features:

> Sssotiations among objects

> Automated mapping between tables and classes

> Data validations

> Callbacks

> Inheritance hierarchies

> Database abstraction through adapters

> Migration supprot

###What things we can define in the model?
> Validations (validate_presence_of, numeracility_of)

> Relationships(like has_one, has_many, HABTM etc.)

> Callbacks(like before_save, after_save, before_create etc.)

> Suppose you installed a plugin say validation_group, So you can also define validation_group settings in your model

> Raw Queries in Sql

###What are the engines in MySQL?
> MyISAM (>15% RW rate, simpler, faster, full text indexing, max 232 rows, max 64 indexes per row)

> InnoDB (FK constraints, transactions, row-level locking, higher concurrency, durability, cascading deletes)

> What are the servers supported by Ruby on Rails?

> Webrick, Mongrel, Thin, Puma, Rainbows, Unicorn, Passenger

> What kind of Types of Relationships in a Model class do you know? How they can be defined?

> has_one, has_many, belongs_to, has_and_belongs_to_many, has_many :through

###What is asset pipeline?
Asset pipeline is a paratigm and a set of techniques enable proper organization of CSS and JavaScript

###What is “request.xhr?” How does it works? What this code does?
```ruby
def name
 if (request.xhr?)
   render :text => @name.to_s
 else
   render :action => 'view_attribute', :attr => @name
 end
end
```
> request.xhr? tells controller is a request was sent using AJAX or it’s a regular HTTP request. Browser add the header “X-Requested-With: XMLHttpRequest” to AJAX request

###What is Scaffolding?

###What are the template engines are supported by Rails?
> ERB, HAML, Slim, Stylus, Less, Sass

###What is the differenct in -%> and %> constructions of ERB?
> The extra dash makes ERB not output the newline after the closing tag.

###What is the difference between “form_for” and “form_tag”?
> Both are used to build a form. Form_for tag is for specific model, it builds form from model fields. Form_tag creates a regular form, it is best used for non-model-fields

###What are the helpers? How to use helpers in ROR?
> Helpers (“view helpers”) are modules that provide methods which are automatically usable in your view. They provide shortcuts to commonly used display code

###What’s the difference between the Rails v2 and v3?
> Brand new router with an emphasis on RESTful declarations

> New Action Mailer API modeled after Action Controller

> New Active Record chainable query language built on top of relational algebra

> Unobtrusive JavaScript helpers with drivers for Prototype, jQuery, and more coming (end of inline JS)

> Explicit dependency management with Bundler

###What’s new in Rails 4?
> Rails queue

> Asynchronious Action Mailer

> HTTP PATCH method

> Custom Flash types (:error, :warning)

> Live Streaming (long polling)

> Routing improved

> Strong parameters to avoid insecure mass-assignement

> Turbolinks

> Page and Action cahing removed

> Asset pipeline improved (extracted to plugin, precompilation, performance

> Model.where.not, Model.where.like calls

> Before_filter renamed to before_action

> Chainable relation.none

> Ruby 1.9.3 required

> Plugins support removed

###What is TDD and BDD? Difference between them
> TDD is Test-Driven-Development, BDD is Behaviour-Driven-development

###What are the most common test frameforks supported by Rails
> TestUnit, RSpec, Cucumber

###How to list all routes for an Rails application?
> By writing “rake routes” in terminal

###What is Rake task, Rakefile?
> Rake is a command line utility of Rails. Rake is Ruby Make, it uses Rakefile to build up a list of tasks. Rake is used for common administration tasks.

###Tell my about projects you had been involved.
> Ha-ha, no answers here!


#Scalability
####Let’s say you have an application (Ruby on Rails based) and once you notice your Rails server is under the load of 80% in average. What do you do?

####Ok, now you have environment consisting of several interchangeable servers. How will user work with them?

####But it may happen user logs in on a specific Rails instance but next request will be sent to another one where user has not been logged in!

####What happen with session when this particular server goes down?

























