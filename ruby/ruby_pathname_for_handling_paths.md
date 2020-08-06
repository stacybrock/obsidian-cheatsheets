# Ruby Pathname For Handling Paths

`Pathname` is a [[ruby]] standard library for handling file paths.

```ruby
require "pathname"

# create from string
path = Pathname("/etc/hosts")

# create relative to current file
path = Pathname(__dir__) + "config.yml"

# building paths
path = Pathname(__dir__)      # /home/brock
path = path + "output"        # /home/brock/output
path = path + "somefile.txt"  # /home/brock/output/somefile.txt

# inquiries (returns true or false)
path.directory?
path.exist?
path.readable?
path.writable?

# traversal
path.ascend   # iterator
path.descend  # iterator
path.children # returns array
```

## References

- https://robm.me.uk/ruby/2014/01/18/pathname.html
