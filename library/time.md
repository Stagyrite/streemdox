# Date and time library

## System time retrieval

### now() - check the current date and time

Returns the current system date and time in ISO format.

#### ./streem [36currenttime.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/36currenttime.strm "streemdox/examples/36currenttime.strm at main · Stagyrite/streemdox")

The current date and time in this example depend on the system clock.

```ruby
datetime = now()
[datetime] | stdout
# Output: 2025.09.05T16:03:38.323+01:00
```

### + - add  minutes to time

Given a return value of a now() function call, I can move it forward by using the plus operator.

#### ./streem [37in-five-minutes.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/37in-five-minutes.strm "streemdox/examples/37in-five-minutes.strm at main · Stagyrite/streemdox")

```ruby
current = now()
in_five_minutes = current + 5
[current, in_five_minutes] | stdout
# Output:
# 2025.09.05T16:17:15.580+01:00
# 2025.09.05T16:17:20.580+01:00
```

### - - subtract minutes from time

Given a return value of a now() function call, I can move it backwards by using the minus operator.

#### ./streem [38before-five-minutes.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/38before-five-minutes.strm "streemdox/examples/38before-five-minutes.strm at main · Stagyrite/streemdox")

```ruby
current = now()
before_five_minutes = current - 5
[current, before_five_minutes] | stdout
# Output:
# 2025.09.05T16:20:51.810+01:00
# 2025.09.05T16:20:46.810+01:00
```

