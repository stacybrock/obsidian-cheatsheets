# Fun With RAM Disks
```
$ VOLUME_NAME=RamDisk
$ SIZE_IN_MB=1024
$ DEVICE=`hdiutil attach -nobrowse -nomount ram://$(($SIZE_IN_MB*2048))`
$ diskutil erasevolume HFS+ $VOLUME_NAME $DEVICE
```
