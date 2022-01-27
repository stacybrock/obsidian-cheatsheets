# launchd
## Job Manifest File Locations
Type|Location
--|--
User Agents|`~/Library/LaunchAgents/`
Global Agents|`/Library/LaunchAgents/`
System Agents|`/System/Library/LaunchAgents/`

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
