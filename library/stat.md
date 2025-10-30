# Statistical library

## Built-in functions

### sum(f) - sum a series of numbers

You need to reduce the input stream to a sum of numbers. You might need to transform the input data as well. Just pass the desired mapping function as the argument. For instance, use the identity function when you just have to sum the numbers up `seq(10) | sum { x -> x } | stdout`. It should output 55, which is a trivial mathematical task. Passing `{ x -> x + 1 }` would turn the number to 65.

### mean(f) - mean value

Computes the mean value from the input stream of numbers. `seq(10) | mean { x -> x } | stdout` should output, 5.5 which is obviously the average value of numbers from 1 to 10. Pass a different function as the argument to change the input values, e.g., `{ x -> x + 1 }` would change the output value to 6.5.

### average() - compute an average value

To compute an average value, we need to provide an input array. The output value should be equal to the sum of the numbers divided by the length of the array. For instance, `seq(100) | average() | stdout` will print 50.5, as it's the average value of the numbers between 1 and 100.

### moving_average(x) - compute a moving average

It computes a moving average from the input stream. Consider using it with the graph bar available in Streem. For instance, this program will produce a graph `seq(100) | moving_average(4) | graph_bar()`. It's a series of averages, not just one average.

### rolling_mean(f) - alias for the moving_average() function

It computes a rolling mean, also known as the moving average.

### stdev(f) - standard deviation

Computes the standard deviation. Pass the identity function or any other function that you like as the argument. For instance, `seq(1000) | stdev { x -> x } | stdout` outputs 288.81943609575.

### variance(f) - variance

Computes the variance of the input numbers. Pass any function as the first argument. For instance, `seq(1000) | variance { x -> x } | stdout` outputs 83416.666666667.

### mean_variance(f) - mean & variance

It computes both the mean value and the variance of the same input numbers. Pass any function that you like. For instance, `seq(1000) | mean_variance { x -> x } | stdout` should output [500.5, 83416.666666667].

### mean_stdev(f) - mean & standard deviation

It computes both the mean value and the standard deviation of the same input numbers. Pass any function that you like. For instance, `seq(1000) | mean_stdev { x -> x } | stdout` should output [500.5, 288.81943609575].

### correl() - correlation coefficient

It computes the correlation coefficient based on the given input stream. For instance, `seq(10) & seq(10) | correl() | stdout` outputs `. Changing the input stream to `seq(10) & [5,4,3,2,1,5,4,3,2,1]` changes the output to -0.49236596391733.

