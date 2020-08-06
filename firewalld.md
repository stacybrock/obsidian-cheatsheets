# firewalld Cheatsheet

**Open a port**
```
# firewall-cmd --zone=public --add-port=8080/tcp
# firewall-cmd --zone=public --permanent --add-port=8080/tcp
# firewall-cmd --reload
```

**List active zones**
```
# firewall-cmd --get-active-zones
```

**List rich rules**
```
# firewall-cmd --zone=public --list-rich-rules
```

**Add rich rule**
```
# firewall-cmd --permanent --zone=public --add-rich-rule='rule family=ipv4 source address=10.193.0.0/16 port port=22 protocol=tcp accept'
```

## Tags
#linux