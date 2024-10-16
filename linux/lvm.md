# LVM cheatsheet
## Add New Disk
Get the name of the new disk:
```
# cat /proc/partitions; /sbin/rescan-scsi-bus; cat /proc/partitions
```
Do LVM things:
```
# pvcreate /dev/sdb
# vgcreate silo-vg /dev/sdb
# lvcreate --name silo -l +100%FREE silo-vg
# mkfs.ext4 /dev/silo-vg/silo
# blkid
# 
```

#linux