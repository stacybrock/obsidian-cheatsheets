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
