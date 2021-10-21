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

## Networking

### List Open Ports
```
netstat -ano | FindSTR LISTENING
```

### Flush DNS Cache
```
ipconfig /flushdns
ipconfig /displaydns
```

### Test a Network Connection
```
Test-NetConnection -ComputerName bob -Port xxx
```

### Configure System Proxy
Set proxy:
```
netsh winhttp set proxy proxy.mydomain.com:8080
```
Clear proxy:
```
netsh winhttp reset proxy
```

## PowerShell
### Equivalent of grep
`Get-ChildItem -recurse | Select-String -pattern "dummy"`

`Select-String -path *.txt -pattern "^blah"`

## Licensing
89 days +- 89 days
slmgr -dlv