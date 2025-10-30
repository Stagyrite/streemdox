# Language

The Streem language consists of constants, variables, operators, and other elements.

## Code comments

All code comments are prefixed with a hash.

### ./streem [01nil.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/01nil.strm "streemdox/examples/01nil.strm at main · Stagyrite/streemdox")

```ruby
# minimal program that can be called NIL
```

## Types

| Value | Type |
| :---: | :---: |
| "HELLO, world" | string |
| true, false | boolean |
| 42 | integer |
| 4.2 | float |
| [1,2,3] | array |
| x -> x | function |
| map, flatmap etc | built-in function |
| stdin, stdout etc | file descriptor |
| x \| y | x can be a stream |

## Standard output with streams

It's possible to pipe an array into standard output without calling a function. Just use the bar operator. This construct
will be used in the sections covering the language features. Calling 'print()' or 'puts()' can be preferred elsewhere.
The elements are placed vertically on a screen, i.e., they are separated with a new line character.

#### ./streem [02hobbies.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/02hobbies.strm "streemdox/examples/02hobbies.strm at main · Stagyrite/streemdox")

```ruby
hobbies = ["yoga", "Tai Chi", "Qigong", "foreign languages", "Streem"]
hobbies | stdout

# Output:
# yoga
# Tai Chi
# Qigong
# foreign languages
# Streem
```

## Assigning a variable

### ./streem [03assign.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/03assign.strm "streemdox/examples/03assign.strm at main · Stagyrite/streemdox")

Here's how to assign value 3 to variable x.

```ruby
x = 3
```

### ./streem [04assign.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/04assign.strm "streemdox/examples/04assign.strm at main · Stagyrite/streemdox")

Over here, we assign "HELLO, world" to a variable s.

```ruby
s = "HELLO, world"
```

TODO: array, concept of stream, print using stream

## Arithmetic expressions

Use the basic arithmetic operators to perform computations.

| Operator | What is? |
| :---: | :---: |
| + | sum |
| - | difference |
| * | multiplication |
| / | division (float) |
| % | remainder |

### ./streem [05operators.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/05operators.strm "streemdox/examples/05operators.strm at main · Stagyrite/streemdox")

```ruby
x_1 = 2 + 3 # 5
x_2 = x_1 * 4 # 20
x_3 = x_2 / 4 # 5
x_4 = x_3 - 3 # 2
x_5 = x_4 % 2 # 2
[x_1, x_2, x_3, x_4, x_5] | stdout

# Output:
# 5
# 20
# 5
# 2
# 0
```

## Logical expressions

> Logical operators are not implemented. Source code that uses them won't parse.

There's an '\|\|' operator for logical "or", and '&&' operator for logical "and".

## Parentheses

You can enclose expressions in brackets to formulate more complex expressions.

### ./streem [06multiplication.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/06multiplication.strm "streemdox/examples/06multiplication.strm at main · Stagyrite/streemdox")

```ruby
# Output: 20

x = (2 + 3) * 4
[x] | stdout
```

## if statements

If statements are done using the keywords 'if' and 'else'. Use "else if" to add more cases

In the following example, "Two" is assigned to the variable s and printed out.

### ./streem [07one-or-two.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/07one-or-two.strm "streemdox/examples/07one-or-two.strm at main · Stagyrite/streemdox")

```ruby
# Output: Two
x = 2

if (x == 1) {
  s = "One"
} else if (x == 2) {
  s = "Two"
} else {
  s = "Unknown"
}

[s] | stdout
```

## Concatenate strings

Strings can be concatenated with the plus operator. Here's an example that can be part of a traditional Hello World program.

### ./streem [08hello-world.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/08hello-world.strm "streemdox/examples/08hello-world.strm at main · Stagyrite/streemdox")

Pipe what is traditionally said at the beginning of the programming journey
to the standard output.

```ruby
# Output: HELLO, world

name = "world"
s = "HELLO, " + name
[s] | stdout
```

The s parameter's value is now "HELLO, world".

## Array

Arrays are one of the fundamental data types in Streem. They are declared as \[x_1, x_2, ..., x_3\].

## Standard I/O

The 'stdin', 'stdout' and 'stderr' are file descriptors used for the standard I/O operations.

## Stream

Arrays are fundamental data types. Their items are enclosed within square brackets. They can be used with a streaming operator \|.

### ./streem [09hello-world.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/09hello-world.strm "streemdox/examples/09hello-world.strm at main · Stagyrite/streemdox")

It's a hello world program that pipes multiple lines to the standard output.
The 'stderr' file descriptor could have also been used in the example below.

```ruby
x = ["HELLO,", "world"]
x | stdout

# Output:
# HELLO,
# world
```

## Functions

Functions are defined within the curly brackets in a lambda-expression manner. Arguments are used, and the last expression is the return value.

### ./streem [10hello-world.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/10hello-world.strm "streemdox/examples/10hello-world.strm at main · Stagyrite/streemdox")

This particular hello program introduces a concept of procedures, i.e. functions
without arguments.

```ruby
# Output: HELLO
hello = () -> { "HELLO" }
s = hello()
print(s)
```

### ./streem [11hello-world.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/11hello-world.strm "streemdox/examples/11hello-world.strm at main · Stagyrite/streemdox")

More can be done when functions have arguments.

```ruby
# Output: HELLO, world
hello = { name ->
	"HELLO, " + name
}

s = hello("world")
print(s)
```

### Functions with multiple parameters

To pass multiple arguments to a function, a matching number of parameters needs to be declared and surrounded by brackets. More than 2 parameters are allowable.

### ./streem [12add.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/12add.strm "streemdox/examples/12add.strm at main · Stagyrite/streemdox")

```ruby
add = (x, y) -> x + y
addz = (x, y, z) -> {
	xy = add(x, y)
	add(xy, z)
}

a = 123456789
b = 987654321

puts(add(a, b))
puts(addz(a, b, 1))

# Output:
# 1111111110
# 1111111111
```

### Pattern matching

There's a pattern matching for functions. It's a functionality similar to a switch statement in non-prototypical languages. The "case" expression has to return a value depending on whether the two passed arguments match. The underscore can be used for default cases. Variables and string literals can be passed as arguments.

### ./streem [13match.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/13match.strm "streemdox/examples/13match.strm at main · Stagyrite/streemdox")

Tests whether an input animal is a cat.

```ruby
# Input:
# elephant
# cat
# dog
# kitty

matches = {
    case "kitty", "cat"   -> true  # match
    case "cat", "kitty"   -> true  # match
    case "doggie", "dog"  -> true  # match
    case "dog", "doggie"  -> true  # match
    case x, x             -> true  # identical
	case _, _             -> false # no match
}

stdin | map { x -> matches("cat", x) } | stdout

# Output:
# false
# true
# false
# true
```

### Namespaces

Namespaces are structures that consist of variables and functions that can be imported and used. An unimported namespace can't be used. They can be used for greater clarity and to group data.

### ./strm highlander.strm

```ruby
# Output:
# There can be only one
# There can be only one.

namespace highlander {
	tagline = "There can be only one"
	taglineDot = () -> { tagline + "." }
}

import highlander
print(tagline)
print(taglineDot())
```

#### Classes

Classes are identical to namespaces, although one could expect to instantiate objects with them. You can import them and use their read-only content.

### ./strm rpg.strm

```ruby
# Output: 19

class player {
	hp = 19
}

import player
[hp] | stdout
```
