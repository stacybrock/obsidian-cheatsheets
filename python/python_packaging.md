# Python Packaging

Packaging [[python]] libraries with `bumpversion` and `twine`...

**Bump Package Version**
```
$ bumpversion --dry-run --verbose --current-version x.x.x [major|minor|patch]
$ bumpversion --current-version x.x.x [major|minor|patch]
```

**Build Package**
```
$ python setup.py sdist bdist_wheel
```

**Test Package**
```
$ twine check dist/*
```

**Upload to TestPyPI**
```
$ twine upload --repository-url https://test.pypi.org/legacy/ dist/*
```

**Upload to PyPI**
```
$ twine upload dist/*
```
