# Iterative programming

It's a kind of iterative programming. One could want to call it a case of functional programming.

## filter(f) - filters a stream

A stream can be filtered to find values matching a predicate.

### ./streem [16find-larger.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/16find-larger.strm "streemdox/examples/16find-larger.strm at main · Stagyrite/streemdox")

Values 100, 200, and 300 are filtered out because they are less than or equal to 300, and therefore don't match the predicate.

```ruby
array = [100, 200, 300, 400, 500]
predicate = filter { x -> x > 300 }
array | predicate | stdout

# Output:
# 400
# 500
```

## map(f) - maps a stream

One can map an input stream into another by passing a mapping function to the 'map()' function.

### ./streem [16find-larger.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/16find-larger.strm "streemdox/examples/16find-larger.strm at main · Stagyrite/streemdox")

For instance, when I want to multiply the input numbers by two, I have to use the `{ x -> 2 * x }` mapping function. The whole expression is `map { x -> 2 * x }`. Let's assume that I've assigned it to the f variable. Now an example program can be `[1, 2, 3] | f | stdout`.

```ruby
f = map { x -> 2 * x }
[1, 2, 3] | f | stdout

# Output:
# 2
# 4
# 6
```

## take(n) - take some elements from a stream

Instantiates a new stream that consists of some elements from an input stream. The number of elements is passed as an argument.

### ./streem [17take.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/17take.strm "streemdox/examples/17take.strm at main · Stagyrite/streemdox")

```ruby
random = [0.978470, 0.396758, 0.241088, 0.543190, 0.598714, 0.451562, 0.944703]
random | take(3) | stdout

# Output:
# 0.97847
# 0.396758
# 0.241088
```

## drop(n) - drop the first n elements

It generates the tail of the input stream. The first n-th elements are the head of it, and won't be available in the output stream. For instance, the expression `seq(10) | drop(9)` will instantiate a stream of a single element 10.

## flatmap(f) - flattens the input stream

### ./streem [18flatmap.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/18flatmap.strm "streemdox/examples/18flatmap.strm at main · Stagyrite/streemdox")

You can make an array out of a matrix (array of arrays) by calling 'flatmap()'.
Just pass the identity function as its argument, i.e. the `{ x -> x }` lambda expression.
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

## seq(n) - Sequence of numbers

To produce a sequence of numbers (1, 2, 3, ..., n) for a given n, call the 'seq()' function.

### ./streem [19counter.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/19counter.strm "streemdox/examples/19counter.strm at main · Stagyrite/streemdox")

```ruby
seq(3) | stdout

# Output:
# 1
# 2
# 3
```

## repeat(x) - repeatedly produce a value

Use this function when you have to produce the same value in a loop. For instance, invoking `repeat("hello")` will instantiate a stream consisting of an unlimited number of "hello" strings. This stream can be passed to the 'stdout' stream.

## cycle(a) - cycle through an array

Pass an array to this function to instantiate an infinite stream consisting of the repeated elements of the given array. For instance, passing the [1, 2, 3] array will produce an infinite stream [1, 2, 3, 1, 2, 3, 1, ...].

## reduce(f) - reduce a stream to an object

To reduce a stream, pass the reduction function as the 'reduce' function argument.

### ./streem [20sum-numbers.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/20sum-numbers.strm "streemdox/examples/20sum-numbers.strm at main · Stagyrite/streemdox")

In this example, the sequence of numbers from 1 to 50 is summed. It can be done using a mathematical theorem, and the result is 1275. The Streem function that does it is `{ x -> x * (x + 1) / 2 }`.

```ruby
# Output: 1275

seq(50) | reduce { x, y -> x + y } | stdout
```

## reduce_by_key(f) - reduce a stream with grouping


You need to group the input pairs, and then reduce each of the groups to a single value. To do that, pass the reducing function as an argument.

### ./streem [40group-and-multiply-numbers.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/40group-and-multiply-numbers.strm "streemdox/examples/40group-and-multiply-numbers.strm at main · Stagyrite/streemdox")

Let's assume that we want to assign 1, 2, 3 to a group with key 1, and 4 to a group with key 4. Then we group the values and compute the product.

```ruby
f = reduce_by_key { x, y -> x * y }
[1, 1, 1, 2] & seq(4) | f | stdout

# Output
# [1, 1]
# [2, 4]
```

## slice(n) - slice the input stream into arrays

Each element of the output stream will consist of an array with at most n elements of the input stream. The elements' order is preserved. Only the last array can have fewer than n elements. An example expression 'seq(10) | slice(3)' will instantiate a stream of arrays: [1, 2, 3], [4, 5, 6], [7, 8, 9], and [10].

## consec(n) - produce an n-element array of the consecutive elements

It will generate an output stream of an array. Each array will contain n elements of the input stream. The m-th array will contain elements of the input stream starting from the m-th element.

### ./streem [41consecutive.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/41consecutive.strm "streemdox/examples/41consecutive.strm at main · Stagyrite/streemdox")

In this case, we produce the 3-element arrays of the consecutive elements.

```ruby
seq(10) | consec(3) | stdout

# Output:
# [1, 2, 3]
# [2, 3, 4]
# [3, 4, 5]
# [4, 5, 6]
# [5, 6, 7]
# [6, 7, 8]
# [7, 8, 9]
# [8, 9, 10]
```

## each(f) - do for each element in a stream

For each element in an input stream, you can execute a function. There's no output stream required.

### ./streem [21five.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/21five.strm "streemdox/examples/21five.strm at main · Stagyrite/streemdox")

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

## emit(x) - emits some elements to a stream

You need to push several elements to a current stream. Make subsequent calls to the 'emit()' function, passing the return values as subsequent arguments. Wrap the calls into a function and pass it to the 'each()' function, or some other function of choice.

### ./streem [22powers.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/22powers.strm "streemdox/examples/22powers.strm at main · Stagyrite/streemdox")

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

## max(f) - maximum of values

Computes a maximum value of the transformed input stream. Pass any function that transforms the input numbers to it. For instance, `[1,5,3] | max { x -> -x } | stdout` outputs 1. Note that we have negated each input value, and therefore, the maximum number is neither 3 nor 5.

## min(f) - minimum of values

Computes a minimum value of the transformed input stream. Pass any function that transforms the input numbers to it. Use the identity function when you don't want to alter them. For instance, `[1,5,3] | min { x -> x } | stdout` outputs 1.

## uniq(f) - find unique values

Searches for the unique values in the input stream. Pass any function to transform them. For instance, `[1, 1, 1, 5] | uniq { x -> x } | stdout` will emit 1 and 5, as those values are unique.

## count() - count the number of input values

Emits the number of elements in the input stream. Use it without any argument. For instance, `seq(100) | count() | stdout` should output 100.

