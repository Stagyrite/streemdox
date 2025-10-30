# Key-value store

There are hashtable objects that work as a database.

## Operations

### kvs() - instantiate a new key-value store

Returns a new object of type 'kvs'.

### put() - assign a value to a key

One can assign a particular value to a string key.

### get() - find a value by key

Retrieves a value that is found by a given key.

#### ./streem [25race.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/25race.strm "streemdox/examples/25race.strm at main · Stagyrite/streemdox")

The key-value store in the following example associates 'race' with 'goblin'.

```ruby
db = kvs()
db.put("race", "goblin")
race = db.get("race")
print(race)
# Output: goblin
```

### update() - update a value with a function

Updates an already available value with a value retrieved from a given function. The first argument is a key name, and the second is the update function.

#### ./streem [26japanized-race.strm](https://github.com/Stagyrite/streemdox/blob/main/examples/26japanized-race.strm "streemdox/examples/26japanized-race.strm at main · Stagyrite/streemdox")

The key-value store in the following example associates 'race' with 'goblin 👺', and later prefixes the value with 'Japanese '.

```ruby
db = kvs()
db.put("race", "goblin 👺")
japanize = { s -> "Japanese " + s }
db.update("race", japanize)
race = db.get("race")
print(race)
# Output: Japanese goblin 👺
```

