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

### round(x)

Return the rounding of x.

```
# Output: 10
print(round(9.76))
```

### frexp(x, y)

Decompose x into mantissa and exponent. y is the exponent.

```
# Output: 0.512500
print(frexp(16.4,5))
```

### ldexp(x, y)

Return the power y of x times 2. (x * (2 ^ y))

```
# Output: 6.00000
print(ldexp(6,3))
```

## Trigonometric functions

### sin(x)

Return the sine of x.

### cos(x)

Return the cosine of x.

### tan(x)

Return the tangent of x.

### asin(x)

Return the arc sine of x.

### acos(x)

Return the arc cosine of x.

### atan(x)

Return the arc tangent of x.

### hypot(x, y)

Return the `sqrt(x * x + y * y)`(Euclidean norm).

```
# Output: 5
print(hypot(3,4))
```

## Hyperbolic functions

### asinh(x)

Return the inverse hyperbolic sine of x.

### acosh(x)

Return the inverse hyperbolic cosine of x.

### atanh(x)

Return the inverse hyperbolic tangent of x.

### cosh(x)

Return the hyperbolic cosine of x.

### sinh(x)

Return the hyperbolic sine of x.

### tanh(x)

Return the hyperbolic tangent of x.

## logarithmic functions

### exp(x)

Return e raised to the power x.

### log(x)

Return the natural logarithm of x.

### log2(x)

Return the base-2 logarithm of x.

### log10(x)

Return the base-10 logarithm of x.

## Power functions

### pow(x,y)

Return x raised to the power y.

```
# Output: 25
print(pow(5,2))
```

### sqrt(x)

Return the square root of x.

```
# Output: 5
print(sqrt(25))
```
