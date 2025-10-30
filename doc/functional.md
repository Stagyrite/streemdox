# Functional programming

Functions are provided to use typical functional programming. It's actually a kind of iterative programming.

## filter() - filters a stream

A stream can be filtered to find values matching a predicate.

### ./streem 16find-larger.strm

Values 100, 200, and 300 are filtered out because they are less than or equal to 300, and therefore don't match the predicate.

```ruby
array = [100, 200, 300, 400, 500]
predicate = filter { x -> x > 300 }
array | predicate | stdout

# Output:
# 400
# 500
```

## take() - take some elements from a stream

Instantiates a new stream that consists of some elements from an input stream. The number of elements is passed as an argument.

### ./streem 17take.strm

```ruby
random = [0.978470, 0.396758, 0.241088, 0.543190, 0.598714, 0.451562, 0.944703]
random | take(3) | stdout

# Output:
# 0.97847
# 0.396758
# 0.241088
```

## flatmap - flattens the input stream

### ./streem 18flatmap.strm

You can make an array out of a matrix (array of arrays) by calling 'flatmap()'.
Just pass the identity function as its argument, i.e. the '{ x -> x }' lambda expression.
Note that the 'x' variable in the expression is by itself a stream.

```ruby
matrix = [[1, 2], [3, 4]]
identity = { x -> x }
matrix | flatmap(identity) | stdout

# Output:
# 1
# 2
# 3
# 4
```

## Sequence of numbers

To produce a sequence of numbers (1, 2, 3, ..., n) for a given n, call the 'seq' function.

### ./streem 19counter.strm

```ruby
seq(3) | stdout

# Output:
# 1
# 2
# 3
```

## reduce - reduce a stream to an object

To reduce a stream, pass the reduction function as the 'reduce' function argument.

### ./streem 20sum-numbers.strm

In this example, the sequence of numbers from 1 to 50 is summed. It can be done using a mathematical theorem, and the result is 1275. The Streem function that does it is '{ x -> x * (x + 1) / 2 }'.

```ruby
# Output: 1275

seq(50) | reduce { x, y -> x + y } | stdout
```

## each - do for each element in a stream

For each element in an input stream, you can execute a function. There's no output stream required.

### ./streem 21five.strm

This checks whether the passed argument is 3. It prints "true" if yes. Otherwise, it prints "false".

```ruby
# Input:
# 2
# 2
# 2
# 3
# 2

stdin | each { x -> puts(number(x) == 3) }

# Output:
# false
# false
# false
# true
# false
```

## emit - emits some elements to a stream

You need to push several elements to a current stream. Make subsequent calls to the 'emit()' function, passing the return values as subsequent arguments. Wrap the calls into a function and pass it to the 'each()' function, or some other function of choice.

### ./streem powers.strm

This example emits x^2, x^3 and x^4 with the input sequence 4, 5 and 6.

A kind of equivalent function would yield an array of powers, and then flatten the matrix (array of arrays) produced. It's obviously better to push the powers immediately into the output stream.

```ruby
powers = { x ->
  pow2 = x * x
  pow3 = pow2 * x
  pow4 = pow3 * x
  emit(pow2)
  emit(pow3)
  emit(pow4)
}

[4, 5, 6] | each(powers) | stdout

# Output:
# 16
# 64
# 256
# 25
# 125
# 625
# 36
# 216
# 1296
```
