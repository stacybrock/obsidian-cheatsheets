# macOS Cheatsheet

## Flush DNS Cache

Mac OS X 10.10.4+:

```
$ sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder;
```

## Fix Borked Camera

```
$ sudo killall VDCAssistant
```

## Adjust Spacing of Menu Bar Icons
```
$ defaults -currentHost write -globalDomain NSStatusItemSpacing -int x
$ defaults -currentHost write -globalDomain NSStatusItemSelectionPadding -int y
```
where `x` and `y` are integers, 0 minimum value, 4 seems to be a good spacing value

Logout to make changes take effect.

To revert back to defaults:
```
$ defaults -currentHost delete -globalDomain NSStatusItemSelectionPadding
$ defaults -currentHost delete -globalDomain NSStatusItemSpacing
```

## Show/Hide Hidden (Dot) Files in Finder

```
$ defaults write com.apple.finder AppleShowAllFiles -bool YES; killall -HUP Finder
```

## Edit crontab

```
crontab: temp file must be edited in place
```

The fix is to `:set nobackup` and `:set nowritebackup` in vim.

## Fix quarantine permissions

If the OS keeps asking you if you want to run an app that was downloaded from the internet and doesn't seem to remember that you said yes, do this:

```
$ sudo xattr -d com.apple.quarantine /path/to/the.app
```

## Check SSD Usage with smartmontools
```
sudo smartctl --all /dev/disk0
```
## Remove Unwanted Applications
1. Reboot into recovery mode.
    - Shutdown or restart.
    - Hold `Command + R` and press power. Continue to hold the keyboard keys until the Apple logo and loading bar appears.
2. Select Disk Utility from the list of options
3. Select your MacOS Mojave installation disk on the left and click `Mount` on the top right.
4. Close Disk Utility
5. Open Terminal by clicking `Utilities -> Terminal`
6. `cd /Volumes/<Mojave root disk>/Applications/`
7. `rm -rf {News.app,Home.app,Stocks.app}`

## Tags
#macos
