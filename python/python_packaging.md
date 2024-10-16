# Python Packaging

Packaging [[python]] libraries with `bumpversion` and `twine`...

### Before Packaging
- [ ] commit all changes
- [ ] pull requests merged
- [ ] Sphinx docs built

### Bump Package Version
```
$ bumpversion --dry-run --verbose --current-version x.x.x [major|minor|patch]
$ bumpversion --current-version x.x.x [major|minor|patch]
```
For example, to bump from 0.1.1 to 0.1.2:
```
$ bumpversion --dry-run --verbose --current-version 0.1.1 patch
```
### Tag Upstream
```
$ git push origin <tag_name>
```
### Build Package
```
$ python setup.py sdist bdist_wheel
```

### Test Package
```
$ twine check dist/*
```

### Upload to TestPyPI
```
$ twine upload --repository-url https://test.pypi.org/legacy/ dist/*
```

## Upload to PyPI
```
$ twine upload dist/*
```
