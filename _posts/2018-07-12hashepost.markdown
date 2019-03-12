---
layout: post
title:  "Hashe"
date:   2018-07-12 00:55:00 -0800
categories: ruby
---

# [Hashe](https://github.com/guckin/hashe)

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

There are two ways you can use Hashe.

using the class class

```ruby
    hash = Hashe::Hash.new
    hash.foo = 'bar' # 'bar'
    hash[:baz] = 'qux' # 'qux'
    hash # {foo: 'bar', baz: 'qux'}
```

as a mixin mix-in

```ruby
    class MyCustomHash
      include Hashe::Mixin
    end

    hash = MyCustomHash.new
    hash.foo = 'bar' # 'bar'
    hash[:baz] = 'qux' # 'qux'
    hash # {foo: 'bar', baz: 'qux'}
```