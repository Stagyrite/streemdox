# Usage

## Normal usage

### no arguments

Start ./streem and input your program that ends with EOF.

### filename

Provide a path to a Streem program as an argument. The filename should end with '.strm'.

```shell
./streem hello_world.strm
```

## -e

Execute one-liners by using the 'e' option.

### ./streem -e 'print("HELLO, shell")'

```ruby
# Output: HELLO, shell
```

## -v

Verbose output about the Streem grammar is available with '-v'.

### ./streem -v [23grammar.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/23grammar.strm "streemdox/examples/23grammar.strm at main · Stagyrite/streemdox")

```ruby
print("HELLO, grammar")
# Output:
# NODES:
#  CALL:
#    print
#    ARRAY:
#     VALUE(STRING): "HELLO, grammar"
# HELLO, grammar
```
