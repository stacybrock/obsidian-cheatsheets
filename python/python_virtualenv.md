# Python virtualenv

Working with [[python]] virtualenvs...

**Fix `dyld: Library not loaded: @executable_path/../.Python` errors**
```
$ find ~/.virtualenvs/my-virtual-env/ -type l -delete
$ virtualenv ~/.virtualenvs/my-virtual-env
```

**What's installed in a virtualenv?**
```
$ cd ~/.virtualenvs/my-virtual-env
$ bin/pip freeze
```
