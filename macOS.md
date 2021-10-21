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

## Show Hidden Files in Finder

```
$ defaults write com.apple.finder AppleShowAllFiles TRUE
$ killall Finder
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

## Disable Keyboard Long Press Accented Characters Popup

```
$ defaults write -g ApplePressAndHoldEnabled -bool false
```

## Remove Unwanted Applications

1. Install/Upgrade to Mojave

2. Reboot into recovery mode. 
    - Shutdown or restart.
    - Hold `Command + R` and press power. Continue to hold the keyboard keys until the Apple logo and loading bar appears.

3. Select Disk Utility from the list of options

4. Select your MacOS Mojave installation disk on the left and click `Mount` on the top right.

5. Close Disk Utility

6. Open Terminal by clicking `Utilities -> Terminal`

7. `cd /Volumes/<Mojave root disk>/Applications/`

8. `rm -rf {News.app,Home.app,Stocks.app}`

## Tags
#macos
