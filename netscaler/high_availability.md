# NetScaler High Availability

In this example:
- *primary* is `10.123.1.143`
- *secondary* is `10.123.1.168`

The *primary* and *secondary* nodes have distinct NSIPs, but everything else must be shared (running config, SSL certs).

1. On both the *primary* and the *secondary*:

```
> set ha node -failsafe ON
```

2. On the *secondary*:

```
> set ha node -haStatus STAYSECONDARY
```

3. On the *primary*:

```
> add ha node 1 10.123.1.168 -INC DISABLED
> set ha node -haSync ENABLED
```

4. On the *secondary*:

```
> add ha node 1 10.123.1.143 -INC DISABLED
> sh ha nodes
Secondary:> sh ha node
1)  Node ID:      0
    IP:   10.123.1.168
    Node State: STAYSECONDARY
    Master State: Secondary
    Fail-Safe Mode: OFF
    INC State: DISABLED
    Sync State: SUCCESS
    Propagation: ENABLED
    Enabled Interfaces : 0/1
    Disabled Interfaces : None
    HA MON ON Interfaces : None
    Interfaces on which heartbeats are not seen : None
    Interfaces causing Partial Failure: None
    SSL Card Status: NOT PRESENT
    Hello Interval: 200 msecs
    Dead Interval: 3 secs
    Node in this Master State for: 0:0:1:17 (days:hrs:min:sec)
2)  Node ID:      1
    IP:   10.123.1.143
    Node State: UP
    Master State: Primary
    Fail-Safe Mode: OFF
    INC State: DISABLED
    Sync State: ENABLED
    Propagation: ENABLED
    Enabled Interfaces : 0/1
    Disabled Interfaces : None
    HA MON ON Interfaces : None
    Interfaces on which heartbeats are not seen : None
    Interfaces causing Partial Failure: None
    SSL Card Status: NOT PRESENT
 Done
```

5. Then, set the node state back to enabled:

```
> set ha node -haStatus ENABLED
```

## Tags
[[netscaler]]