# NetScaler CLI Commands

**Open a Shell**
```
> shell
```

**Inspect Running Config**
```
> sh running
> sh running | more
> sh running | grep something
```

**Save Running Configuration**
```
> save ns config
```
Running config is written out to `/nsconfig/ns.conf`

**Show Licenses**
```
> sh license
```
License files go in `/nsconfig/license/`. Appliance reboot is required when changing license files.

**Informational**
```
> show ns ip
> show version 
> show hardware 
```

**Networking-Related**
```
> sh route
> sh ip -type SNIP
> sh vlan -summary
```

**Show/Enable Features**
```
> sh ns feature
> enable ns feature <ACRONYM>
```

**Reset Running Configuration to Factory Defaults**
```
> clear ns config <basic|extended|full>
```

See also [How to Use clear ns config Command on NetScaler](http://support.citrix.com/article/CTX112695)

## Tags
[[netscaler]]