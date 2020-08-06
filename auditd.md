# auditd Cheatsheet

## Watch Files For Changes

**Set watch**
```
# auditctl -w /var/lib/jenkins/.rbenv/shims -p war -k watch-shims
```
- `-w` - path to watch
- `-p` - permissions filter r=read, w=write, x=execute, a=attribute
- `-k` - key (printed in audit log, to help with searching)

**List rules and watches**
```
# auditctl -l
```

**Delete watch**
```
# auditctl -W /var/lib/jenkins/.rbenv/shims -p war -k watch-shims
```

**See results**
```
# ausearch -f /var/lib/jenkins/.rbenv/shims
# ausearch -k watch-shims
```
- `-f` - search by file
- `-k` - search by key

## Tags
#linux