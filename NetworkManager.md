# NetworkManager
Network interface files are stored in `/etc/sysconfig/network-scripts/ifcfg-*`
## nmcli
**show connections**
```
$ nmcli con show
```
**up/down connection**
```
$ nmcli con up id CONNECTION_NAME
$ nmcli con down id CONNECTION_NAME
```
**devices**
```
$ nmcli d show
$ nmcli d show INTERFACE_NAME
```

## Tags
#linux