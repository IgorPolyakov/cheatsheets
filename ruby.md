---
title: Ruby
category: Ruby
layout: 2017/sheet
weight: -3
updated: 2019-03-03
---

## Mainly
{: .-two-column}

### Reserved Words

```ruby
alias   and     BEGIN   begin   break   case    class   def     defined?
do      else    elsif   END     end     ensure  false   for     if
in      module  next    nil     not     or      redo    rescue  retry
return  self    super   then    true    undef   unless  until   when
while   yield
```

### Variables
```ruby
$global_variable
@@class_variable
@instance_variable
CONSTANT
::TOP_LEVEL_CONSTANT
OtherClass::CONSTANT
local_variable
```

{: .-three-column}
## Types

### Numbers

```ruby
123
1_234
123.45
1.2e-3
0xffff   # hex
0b01011  # binary
0377     # octal
?a       # ASCII character (1.8 only -- 1.9 returns a string "a")
?\C-a    # Control-a
?\M-a    # Meta-a
?\M-\C-a # Meta-Control-a
```

### Strings

```ruby
'no interpolation'
"#{interpolation}, and backslashes\n"
%q(no interpolation)
%Q(interpolation and backslashes)
%(interpolation and backslashes)
`echo command interpretation with interpolation and backslashes`
%x(echo command interpretation with interpolation and backslashes)
```

### Symbols

```ruby
:symbol                        == :symbol
:'#{"without"} interpolation'  == :"#{"without"} interpolation"
:"#{"with"} interpolation"     == :"with interpolation"
%s(#{"without"} interpolation) == :"#{"without"} interpolation"
```

Internalized String. Guaranteed to be unique and quickly comparable. Ideal for hash keys.

See: [Symbols](https://tour.golang.org/basics/15)

### Arrays

```ruby
[1, 2, 3]
%w(foo bar baz #{1+1}) == ["foo", "bar", "baz", "\#{1+1}"]
%W(foo bar baz #{1+1}) == ["foo", "bar", "baz", "2"]
```

### Hashes

```ruby
{1=>2, 2=>4, 3=>6}
{ key: val } == { :key => val } # 1.9 only.
```
## Flow control
{: .-three-column}

### Conditional

```ruby
if bool-expr [then]
  body
elsif bool-expr [then]
  body
else
  body
end
```
{: data-line="1,3,5"}

See: [If](https://tour.golang.org/flowcontrol/5)

### Switch

```ruby
case target-expr
when comparison [, comparison]... [then]
  body
when comparison [, comparison]... [then]
  body
# ...
else # optional else
  body
end
```

See: [Switch](https://github.com/golang/go/wiki/Switch)

### Loops
#### Simple loop
```ruby
loop do
  body
end

while bool-expr [do]
  body
end

until bool-expr [do]
  body
end

begin
  body
end while bool-expr

begin
  body
end until bool-expr

for name [, name]... in expr [do]
  body
end

expr.each do | name [, name]... | # preferred form over `for`
  body
end

expr while bool-expr
expr until bool-expr

break # terminates loop immediately.
redo  # immediately repeats w/o rerunning the condition.
next  # starts the next iteration through the loop.
retry # restarts the loop, rerunning the condition.
```

See: [For loops](https://tour.golang.org/flowcontrol/1)

### For-Range loop

```ruby
  entry := []string{"Jack","John","Jones"}
  for i, val := range entry {
    fmt.Printf("At position %d, the character %s is present\n", i, val)
  }
```

See: [For-Range loops](https://gobyexample.com/range)

## What?
{: .-three-column}

### Invoking a Method

```ruby
  method
  obj.method
  Class::method # don't use this
  Class.method

  method(key1 => val1, key2 => val2) # one hash arg, not 2

  method(arg1, *[arg2, arg3]) == method(arg1, arg2, arg3)

  # As ugly as you want it to be:
  method(arg1, key1 => val1, key2 => val2, *splat_arg) #{ block }
```
{: data-line="1"}

Functions are first class objects.

### Defining a Class

```ruby
class Identifier [< superclass ]
  expr..
end

# singleton classes, add methods to a single instance
class << obj
  expr..
end
```

```ruby
func getMessage() (a string, b string) {
  return "Hello", "World"
}
```
### Defining a Module

```ruby
module Identifier
  expr..
end
```

### Defining a Method

```ruby
func split(sum int) (x, y int) {
  x = sum * 4 / 9
  y = sum - x
  return
}
```
{: data-line="4"}

By defining the return value names in the signature, a `return` (no args) will return variables with those names.

See: [Named return values](https://tour.golang.org/basics/7)

## Packages
{: .-three-column}

### Importing

```ruby
require "fmt"
require_relative "math/rand"
```

### Aliases

```ruby
alias re re
```

## References

- [A tour of Go](https://tour.golang.org/welcome/1) _(tour.golang.org)_
- [Golang wiki](https://github.com/golang/go/wiki/) _(github.com)_
- [Awesome Go](https://awesome-go.com/) _(awesome-go.com)_
- [Go by Example](https://gobyexample.com/) _(gobyexample.com)_
- [Effective Go](https://golang.org/doc/effective_go.html) _(golang.org)_
- [JustForFunc Youtube](https://www.youtube.com/channel/UC_BzFbxG2za3bp5NRRRXJSw) _(youtube.com)_
- [Style Guide](https://github.com/golang/go/wiki/CodeReviewComments) _(github.com)_
