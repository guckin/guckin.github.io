---
layout: post
title:  "Ruby Hash with dynamic setters and getters"
date:   2018-07-12 00:55:00 -0800
categories: ruby
---

# Hashe

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'hashe'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install hashe

## Usage

*class*

```ruby
    hash = Hashe::Hash.new
    hash.foo = 'bar' # 'bar'
    hash[:baz] = 'qux' # 'qux'
    hash # {foo: 'bar', baz: 'qux'}
```

*mix-in*

```ruby
    class MyCustomHash
      include Hashe::Mixin
    end

    hash = MyCustomHash.new
    hash.foo = 'bar' # 'bar'
    hash[:baz] = 'qux' # 'qux'
    hash # {foo: 'bar', baz: 'qux'}
   
```