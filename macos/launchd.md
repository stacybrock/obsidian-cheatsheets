# launchd
## Job Manifest File Locations
Type|Location
--|--
`~/Library/LaunchAgents`|Per-user agents provided by the user.
`/Library/LaunchAgents`|Per-user agents provided by the administrator.
`/Library/LaunchDaemons`|System wide daemons provided by the administrator.
`/System/Library/LaunchAgents`|OS X Per-user agents.
`/System/Library/LaunchDaemons`|OS X System wide daemons.
## CLI Command Reference
```
$ launchctl list
$ launchctl load PATH_TO_PLIST
$ launchctl unload PATH_TO_PLIST
$ launchctl start LABEL
$ launchctl stop LABEL
```
## Tags
#macos
