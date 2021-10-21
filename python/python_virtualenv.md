# Python virtualenv

Tips for working with #python virtualenvs...

## Common Errors
**Fix `dyld: Library not loaded: @executable_path/../.Python` errors**
```
$ find ~/.virtualenvs/my-virtual-env/ -type l -delete
$ virtualenv ~/.virtualenvs/my-virtual-env
```
This removes symlinks to python executables and rebuilds them.
## Inventory
### Listing Packages Installed In a Virtualenv
```
$ cd ~/.virtualenvs/my-virtual-env
$ bin/pip freeze
```
### Which Virtualenvs Have [SOMEPACKAGE] Installed?
```
$ find ~/.virtualenvs/ -type d -name 'urllib3-1.2*'
```
### Virtualenv Python Versions
Quickly list python versions for all virtualenvs:
```
$ find ~/.virtualenvs/ -type l -name python | xargs ls -la
```
Tack on a `grep` to list virtualenvs running a specific python:
```
$ find ~/.virtualenvs/ -type l -name python | xargs ls -la | grep '3.6'
```
