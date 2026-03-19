# reMarkable and reMarkable Paper Pro (RMPP)
## Custom Suspend Screen
**Sizes (in pixels)**
- reMarkable 2: 1404w x 1872h
- reMarkable Paper Pro: 1620w x 2160h

```bash
$ cd /usr/share/remarkable
$ cp suspended.png suspended.png-backup
$ cp ~/yourfile.png suspended.png
```
Changes take effect immediately.

## Remove Rotating Images on Suspend Screen
```bash
$ cd /usr/share/remarkable/carousel/
```
Delete all the images or move them somewhere else to disable them from being superimposed on the suspend screen.

## Permanently Disable Updates
```bash
$ mount -o remount,rw /
$ umount -R /etc
```
Toggle the option for Automatic Updates in the UI, then restart the device.

## Enable SSH
1. Enable Developer Mode (RMPP only)
2. Settings > About > Copyright and Licenses for SSH connection info
3. Plug in USB cable
```bash
$ ssh root@10.11.99.1
```
4. Enable WLAN
```bash
$ rm-ssh-over-wlan on
```

## Read-only Directories (RMPP Only)
```bash
$ mount -o remount,rw /
```
