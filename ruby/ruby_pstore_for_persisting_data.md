# Ruby PStore For Persisting Data

`PStore` is a [[ruby]] standard library for handling persistent data. Data is written to disk as a byte stream, and is not human-readable.

```ruby
require "pstore"

store = PStore.new("data.pstore")

# writing data
store.transaction do
  store[:last_file] = "example.txt"
end

# reading data
last_file = store.transaction { store[:last_file] }

# abort in transaction
# (you can also commit in transactions)
store.transaction do
  store[:last_file] = "example.txt"

  user = User.get_current_user
  store.abort unless user

  store[:last_file_user] = user
end
```

`YAML::Store` uses YAML as its format when persisting to disk. Usage is the same as with PStore.

```ruby
require "yaml/store"

store = YAML::Store.new("data.yml")
```

## References

- https://robm.me.uk/ruby/2014/01/25/pstore.html
