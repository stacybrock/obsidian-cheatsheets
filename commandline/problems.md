# Command-line Problems
## Can't paste in a long line
or, long lines are truncated when pasting into a command-line program.

**Solution:** set terminal to non-canonical input
```
$ stty -icanon
$ ./some-script.py
$ stty icanon
```