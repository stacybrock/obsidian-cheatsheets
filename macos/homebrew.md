## homebrew Cheatsheet

## Install a Specific Version of Software

First, search git logs for git commit with the correct version:

```
$ cd /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core && git log -- Formula/terragrunt.rb
```

Look through the log for the last commit with the version we want. Example, we want to install **0.19.26** so we want to revert to `e0bac83f8c65bd49944b3b1104e1307707da4eab`. Make sure you use the most recent commit for that version *including* bottle updates.

```
commit c0a9e18e85afb61ab2e964edbdfd2dc9b746a4dc
Author: Rui Chen <someemail@gmail.com>
Date:   Wed Sep 25 23:27:18 2019 -0400

    terragrunt 0.19.27

    Closes #44594.

    Signed-off-by: Rui Chen <someemail@gmail.com>

commit e0bac83f8c65bd49944b3b1104e1307707da4eab
Author: BrewTestBot <homebrew-test-bot@lists.sfconservancy.org>
Date:   Tue Sep 24 13:05:12 2019 +0000

    terragrunt: update 0.19.26 bottle.

commit a7e960c2a6e90e9b0ff6cac256fd55c3847b4311
Author: Rui Chen <someemail@dot.com>
Date:   Tue Sep 24 08:49:29 2019 -0400

    terragrunt 0.19.26

    Closes #44541.

    Signed-off-by: FX Coudert <someemail@gmail.com>
```

Check out that version:

```
$ git checkout e0bac83f8c65bd49944b3b1104e1307707da4eab Formula/terragrunt.rb
```

Install it:

```
$ HOMEBREW_NO_AUTO_UPDATE=1 brew install terragrunt
```

Optionally, pin the version to prevent automatic upgrades with `brew upgrade`:

```
$ brew pin terragrunt
```

## Reset Homebrew

To resolve errors like "Some installed formulae are not readable" that seem to indicate that homebrew hasn't cloned its formulae properly from git...

```
$ brew update-reset
```

## Fix Specific Errors
### Error: Permission denied @ apply2files
```
$ brew cleanup
...
Error: Permission denied @ apply2files - /usr/local/lib/docker/cli-plugins
```
Resolution:
```
$ sudo chown -R ${LOGNAME}:staff /usr/local/lib/docker/
$ brew cleanup
```

## Tags
#macos