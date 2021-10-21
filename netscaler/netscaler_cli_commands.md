# NetScaler CLI Commands
## Basic Usage
#### Show Stats
```
> sh lb vserver lb_vsvr_name
> sh servicegroup svcgrp_name
> sh server svr_name1
```

#### Disable a Server In a Service Group Pool
```
> disable server [SERVERNAME] [DELAY] -graceFul [NO|YES]
```
* `DELAY` and `-graceFul` are optional

#### Enable a Server In a Service Group Pool
```
> enable server [SERVERNAME]
```

#### Save Running Configuration
It's good practice to save the running config immediately after any set of changes.
```
> save ns config
```
Running config is written out to `/nsconfig/ns.conf`

## Administrative
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