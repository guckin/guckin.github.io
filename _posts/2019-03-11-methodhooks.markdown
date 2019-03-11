---
layout: post
title:  "Method Hooks"
date:   2019-03-11 00:55:00 -0800
categories: ruby
---

Powerful method hooks for ruby

Available Hooks 

`.before` - before a method execute callback 

`.after` - after a method execute callback

`.rescue_on_fail` - if failure then rescue then call callback

`.time_box_method` - time box and call callback

FYI: My Dogs name is slippy

## Usage

###  `.before`
The before hook will be called before the method call.
```ruby
class MyClass
  include SlippyMethodHooks
  
  def a(args)
    puts "#a called with args #{args}"
  end

  def b(args)
      puts "#b called with args #{args.join(', ')}"
  end

  before(:a, :b) do |name, args|
    puts name # this is the name of the method
    puts args # yields the args 
  end
end
my_class = MyClass.new
my_class.b('arg 1', 'arg 2')
# b
# ['arg 1', 'arg 2']
# b called with args arg 1, arg 2
```
 

### `.after`
after runs after the method is called and yields the the result of
the method
```ruby
after(*methods) do |result|
  log(result)
end
```

### `.rescue_on_fail`

Rescue on will wrap a function in a catch all and then yield to you an error if the method fails
```ruby
rescue_on_fail(:failing_method) do |e|
  log(e)
  raise e
end
...
my_class = MyClass.new
my_class.failing_method
```

### `.time_box_method`

Timeout methods that run forever
```ruby
time_box_method(1, :method_with_long_execution_time)
```