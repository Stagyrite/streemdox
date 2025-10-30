# Math library

Streem standard library contains built-in functions that correspond
to the C standard.

## Constant values

### PI - π

The mathematical constant π = 3.141592…, to available precision.

```
# Output: 3.1415926353898
print(PI)
```

### E - e (Euler's number)

The mathematical constant e = 2.718281…, to available precision.

```
# Output: 2.718281828459
print(E)
```

## Number-theoretic and representation functions

### ceil(x) - ceiling function

Computes the smallest number not less than x.

```
# Output: 46
print(ceil(45.54))
```

### fabs(x) - absolute function

Computes the absolute value of x.

```
# Output: 2
print(fabs(-2))
```

### gcd(x, y) - greatest common divisor function

Computes the greatest common divisor of the integers x and y.

```
Output: 2
print(gcd(4,10))
```

### trunc(x) - truncation function

Computes the real value x truncated to an integer.

```
Output: 9
print(trunc(9.13))
```

### int(x) - alias for the truncation function

Same as trunc(x).

### floor(x) - floor function

Computes the largest number not greater than x.

```
# Output: 2
print(floor(2.7))
```

### round(x) - round to nearest integer, away from zero

Return the rounding of x.

```
# Output: 10
print(round(9.76))
```

### frexp(x, y) - convert floating-point number to fractional and integral components

Decompose x into mantissa and exponent. y is the exponent.

```
# Output: 0.512500
print(frexp(16.4,5))
```

### ldexp(x, y) - multiply floating-point number by integral power of 2

Return the power y of x times 2. (x * (2 ^ y))

```
# Output: 6.00000
print(ldexp(6,3))
```

## Trigonometric functions

### sin(x) - sine function

Return the sine of x.

### cos(x) - cosine function

Return the cosine of x.

### tan(x) - tangent function

Return the tangent of x.

### asin(x) - arc sine function

Return the arc sine of x.

### acos(x) - arc cosine function

Return the arc cosine of x.

### atan(x) - arc tangent function

Return the arc tangent of x.

### hypot(x, y) - Euclidean distance function

Return the `sqrt(x * x + y * y)` (Euclidean norm).

```
# Output: 5
puts(hypot(4, 3))
```

## Hyperbolic functions

### asinh(x) - inverse hyperbolic sine function

Return the inverse hyperbolic sine of x.

### acosh(x) - inverse hyperbolic cosine function

Return the inverse hyperbolic cosine of x.

### atanh(x) - inverse hyperbolic tangent function

Return the inverse hyperbolic tangent of x.

### cosh(x) - hyperbolic cosine function

Return the hyperbolic cosine of x.

### sinh(x) - hyperbolic sine function

Return the hyperbolic sine of x.

### tanh(x) - hyperbolic tangent function

Return the hyperbolic tangent of x.

## logarithmic functions

### exp(x) - base-e exponential function

Return e raised to the power x.

### log(x) - natural logarithmic function

Return the natural logarithm of x.

### log2(x) - base-2 logarithmic function

Return the base-2 logarithm of x.

### log10(x) - base-10 logarithmic function

Return the base-10 logarithm of x.

## Power functions

### pow(x,y) - power functions

Return x raised to the power y.

```
# Output: 36
puts(pow(6, 2))
```

### sqrt(x) - square root function

Return the square root of x.

```
# Output: 6
puts(sqrt(36))
```
