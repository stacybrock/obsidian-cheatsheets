# Git Tricks

## Ignore everything inside a directory

**Objective:** You want a dir called `logs/` in your [[git]] repo, but you don't want to track its contents.

**Add a `.gitignore` file inside the directory:**
```
# Ignore everything in this directory
*
# Except this file
!.gitignore
```

## Change Author Email Across All Commits In a Repo
==DANGER!== Using `git-filter-branch` is not for the faint of heart!

```
$ git filter-branch --commit-filter 'if [ "$GIT_AUTHOR_EMAIL" = "bademail@someplace.edu" ]; then export GIT_AUTHOR_EMAIL=goodemail@someplace.edu; fi; git commit-tree "$@"'
$ git push -f origin master:master
```