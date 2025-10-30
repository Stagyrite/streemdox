# Comma-separated value

The CSV and tab-separated value (TSV) files are supported.

## Operations

### csv() - instantiate a new CSV stream

Returns a new input stream that can accept a CSV file and output its values. The first array passed to the stream should contain the types of each column. Types are strings, integers, floats, etc. Next, it can read an entire CSV file that consists of the headers and the rows.

#### ./streem [24medicines.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/24medicines.strm "streemdox/examples/24medicines.strm at main · Stagyrite/streemdox")

Here's the input file '24medicines.csv'.

```csv
id,social security number,medicine,start date,end date
1,01010111111,vitamin bears,20250822,20251128
2,22020222222,fluoride tablets,20250111,
3,01010111111,cod liver oil,20250601,20250630
```

It can be read, and all values are piped to the standard output.

```ruby
data = csv()
["integer,string,string,time,time"] | data
stream = fread("24medicines.csv") | data
stream | stdout

# Output:
# ["integer", "string", "string", "time", "time"]
# [integer:"integer", string:"social security number", string:"medicine", time:"start date", time:"end date"]
# ["1", "01010111111", "vitamin bears", "20250822", "20251128"]
# ["2", "22020222222", "fluoride tablets", "20250111", ""]
# ["3", "01010111111", "cod liver oil", "20250601", "20250630"]
```

