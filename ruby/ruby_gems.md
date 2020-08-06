# Ruby Gems Cheatsheet

Working with [[ruby]] gems...

## Show install dir

```
gem contents asciidoctor-pdf --show-install-dir
```

## Uninstall specific gem version

```
gem uninstall --version x.x.x
```

## Delete all gems

```bash
#!/usr/bin/env bash

list=`gem list --no-versions`
for gem in $list; do
    gem uninstall $gem -aIx
done
gem list
gem install bundler
```
