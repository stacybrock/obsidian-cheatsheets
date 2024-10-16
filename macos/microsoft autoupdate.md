# Microsoft AutoUpdate
## Remove MAU
```
$ cd "/Library/Application Support/Microsoft/"
$ sudo su
# rm MAU2.0
# rm /Library/LaunchDaemons/com.microsoft.autoupdate.helper.plist
# rm /Library/PrivilegedHelperTools/com.microsoft.autoupdate.helper
# rm /Library/LaunchAgents/com.microsoft.update.agent.plist
```
```
/usr/bin/pkill -9 -x "Microsoft AutoUpdate"
/usr/bin/pkill -9 -x "Microsoft Update Assistant"
/usr/bin/pkill -9 -x "com.microsoft.autoupdate.helper"
```
## Tags
#macos