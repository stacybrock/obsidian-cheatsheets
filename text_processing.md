# Processing Text

## Wrap Long Lines

```
$ fold -w80 -s file.txt
```

- `-w` - width to wrap at
- `-s` - wrap on spaces

## Format Text for Printing

```
$ pr -td file.txt
```

- `-t` - don't print any headers
- `-d` - double-space
