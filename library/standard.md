# Standard

Streem has standard functions for processing strings, I/O, CSV, hashtables and bar graphs.

## Built-in objects

### Standard I/O

The 'stdin', 'stdout' and 'stderr' are file descriptors used for the standard I/O operations.

## Built-in functions

Stream contains a variety of built-in functions.  Note that they can return streams.

### puts() - print a string to standard output

The puts() function can be used for printing to standard output.

#### ./streem [27hello-world.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/27hello-world.strm "streemdox/examples/27hello-world.strm at main · Stagyrite/streemdox")

```ruby
# Output: HELLO, world
s = "HELLO, world"
puts(s)
```

### print() - print to standard output

The print() function is an alias to the puts() function.

### Reverse an array

An array can be reversed using a 'reverse' function. Instead of a new array, a stream is created.

#### ./streem [28countdown.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/28countdown.strm "streemdox/examples/28countdown.strm at main · Stagyrite/streemdox")

```ruby
x = [1, 2, 3]
reverse(x) | stdout
# Output:
# 3
# 2
# 1
```

### exit(status)

Terminates with a specified value. Useful in Shell scripts.

#### An execution that fails

```shell
./streem [-e "exit(1)" || echo "failure"](https://github.com/Stagyrite/streemdox/blob/main/examples/-e "exit(1)" || echo "failure" "streemdox/examples/-e "exit(1)" || echo "failure" at main · Stagyrite/streemdox")
# Output: failure
```

#### An execution that succeeds

```shell
./streem [-e "exit(0)" && echo "success"](https://github.com/Stagyrite/streemdox/blob/main/examples/-e "exit(0)" && echo "success" "streemdox/examples/-e "exit(0)" && echo "success" at main · Stagyrite/streemdox")
# Output: success
```

### zip() - zip two streams

Creates a quasi-dictionary structure that consists of the keys given in the left argument and values in the right argument.
Both arguments are arrays. The output array consists of an array of two-element arrays. The first is the key, and the second is the value.

### ./streem [30sheet.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/30sheet.strm "streemdox/examples/30sheet.strm at main · Stagyrite/streemdox")

```ruby
rows = [["cell_1", "cell_2", "cell_3"],
        ["cell_4", "cell_5", "cell_6"],
        ["cell_7", "cell_8", "cell_9"]]
columns = ["column_1", "column_2", "column_3"]
zip(columns, rows) | stdout

# Output:
# ["column_1", ["cell_1", "cell_2", "cell_3"]]
# ["column_2", ["cell_4", "cell_5", "cell_6"]]
# ["column_3", ["cell_7", "cell_8", "cell_9"]]
```

### & - zip two arrays

The & operator is an alias to the zip() function.

#### ./streem [31matrix.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/31matrix.strm "streemdox/examples/31matrix.strm at main · Stagyrite/streemdox")

```ruby
seq(3) & seq(3) | stdout
[1, 1]
[2, 2]
[3, 3]

# Output:
# [1, 1]
# [2, 2]
# [3, 3]
```

### ./streem [32zip-with-counter.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/32zip-with-counter.strm "streemdox/examples/32zip-with-counter.strm at main · Stagyrite/streemdox")

You can zip streams as well, not just arrays.

```ruby
# Input:
# HELLO,
# @stagyrite
# 🐍

stdin & seq(3) | stdout

# Output:
# ["HELLO,", 1]
# ["@stagyrite", 2]
# ["🐍", 3]
```

### Streaming bar graph

A trivial example that counts down from 3 to 0.

#### ./streem [33stag-countdown.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/33stag-countdown.strm "streemdox/examples/33stag-countdown.strm at main · Stagyrite/streemdox")

```ruby
graph = graph_bar()
[3, 2, 1, 0] | graph
```

It can be filled with numbers from the range 1 to 250.

#### ./streem [34stag-linear.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/34stag-linear.strm "streemdox/examples/34stag-linear.strm at main · Stagyrite/streemdox")

```ruby
graph = graph_bar()
seq(250) | graph
```

### Random numbers

> The random number generator is not fully implemented. Random numbers can be acquired only by modifying the source code.

There's an ability to generate random numbers.

#### rand_seed() - generate a random seed

It generates a string that can be used as a random seed.

#### rand() - instantiate a stream of random numbers

It takes one argument, which is a random seed. If no arguments are provided, it uses a randomly generated seed.

It starts to emit floating-point numbers. e.g., 0.978470, 0.396758, 0.241088, etc.

#### rand_norm() - instantiate a streem of normal (or Gaussian) random numbers

Generate Gaussian noise using the Marsaglia polar method.

#### sample() - retrieves a sample of data

Pass a number n to retrieve the n-th element from a stream.

### String manipulation

Strings can be transformed and manipulated with a set of built-in functions.

#### number() - converts a string to a number

You need to parse out an integer or a floating-point number from a string, possibly user input. The 'number()' function returns a number that can be used with mathematical operators.

##### ./streem [35number.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/35number.strm "streemdox/examples/35number.strm at main · Stagyrite/streemdox")

```ruby
# Output: 58
eight = number("8")
seven = number("7.0")
puts(eight * seven)
```

