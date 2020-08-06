# Windows

## Services

Run `cmd.exe` as Administrator:

**Find Service**
```
sc query state=all | FIND "jenkins"
```

**Delete Service**
```
sc delete SOME_SERVICE_NAME
```
