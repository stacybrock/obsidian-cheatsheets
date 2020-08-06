# python - measure code execution time

To measure execution time in [[python]]...

```python
def is_isogram(string):
    string = string.lower()
    if string.isalnum():
        return len(string) == len(frozenset(string))
    else:
        y = list(filter((lambda x: x.isalnum()), list(string)))
        return len(y) == len(frozenset(y))

if __name__ == '__main__':
    import timeit
    print(timeit.timeit("is_isogram('Hjelmqvist-Gryb-Zock-Pfund-Wax')", setup="from __main__ import is_isogram"))
    print(timeit.timeit("is_isogram('HjelmqvistGrybZockPfundWax')", setup="from __main__ import is_isogram"))
    print(timeit.timeit("is_isogram('lumberjacks')", setup="from __main__ import is_isogram"))
    print(timeit.timeit("is_isogram('essentials')", setup="from __main__ import is_isogram"))
```
