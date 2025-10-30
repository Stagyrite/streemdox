# Strings

The Streem language has a support for the string data type. It can also sort the input strings in a user-defined manner.

## length(s) - length of a string

Returns the number of characters in a string. For instance, `puts(length("hello"))` prints 5, as the length of the string "hello" is 5.

## split(s, separator) - splits the string

Emits the strings obtained from splitting the string passed as the first argument. The second argument is the separator. For instance, when I want to split the "hello, world" string, and the separator is the comma character, I should use the expression `split("hello, world", ",")`. In this example, two strings should be emitted: "hello" and " world".

## s1 + s2 - concatenate strings

I can concatenate two or more strings using the '+' operator. For instance, when I want to build the "hello, world" string, I can use the expression `"hello" + ", " + "world"`.

## chars(s) - split a string into individual characters

Emits each character from a given string as a separate element. For instance, when I want to split the "hello, world" string, I use the expression `chars("hello, world")`. One can expect that there will be 11 elements emitted.

## sort(a, f) - sorts the input array

Sorts the data passed as an array in the first argument. The second argument is options. When it's not given, the ordering will be ascending. For instance, `sort([1, 2, 3])` will emit values 1, 2, and 3. For another instance, if I want to sort numbers in descending order, I can use `sort([1, 2, 3], { x, y -> y - x })`. The emitted values should be 3, 2, and 1.

