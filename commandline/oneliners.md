# One Liners

## Extract Matches From Lines In a File

```
$ perl -ne 'print "$1\n" if /(\w*)\./' box_errors.txt
```

If `gawk` is present, the `match()` function can also do this.
