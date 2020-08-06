# Bash-Fu
[[bash]]

## History Fun

- `!!` - previous command
- `!!:#` - where # is 1, 2, etc... the *n* th argument to previous command
- `!$` - the last argument to the previous command

```
$ cp cisco-decrypt.c /tmp
$ cd !$
cd /tmp
```

- `!$:h` - head of last argument of previous command

```
$ vi /tmp/cisco-decrypt.c
$ cd !$:h
cd /tmp
```

- `!$:t` - tail of last argument of previous command

```
$ vi /tmp/cisco-decrypt.c
$ echo !$:t
echo cisco-decrypt.c
cisco-decrypt.c
```

- `!$:r` - strip trailing extension off last argument of previous command

```
$ vi /tmp/cisco-decrypt.c
$ echo !$:r
echo /tmp/cisco-decrypt
/tmp/cisco-decrypt
```

## Replace Word In Previous Command History

```
$ cat foo.txt
This is foo.txt
$ ^foo^bar
cat bar.txt
This is bar.txt
```

## Gotchas

### Delete File That Begins With a Hyphen

```
$ rm -- -h.txt
```
