# iptables Cheatsheet

**Drop packets from a specific IP**
```
# iptables -I INPUT_changeme -s 128.193.x.x -j DROP
```
Use the `-I` flag to insert into the chain; use `-A` to append.

**Delete iptables rule**
```
# iptables -L INPUT_changeme -n --line-numbers
Chain INPUT (1 references)
num  target     prot opt source               destination
1    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1194 /* 'dapp_ghe-1194' */
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:122 /* 'dapp_ghe-122' */
3    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:161 /* 'dapp_ghe-161' */
# iptables -D INPUT_changeme 2
```

## Tags
#linux
