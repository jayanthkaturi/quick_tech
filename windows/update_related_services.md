### Net command (manage services, devices, files, accounts)
```cmd
net start <service_name>
net stop <service_name>
net view <resource>
```

### Services related to windows update
```cmd
net stop bits
net stop wuauserv
net stop appidsvc
net stop cryptsvc
```

### svchost
```cmd
## sc create: Creates a subkey and entries for a service in the registry and in the Service Control Manager database.
## svchost.exe -k netsvcs => start network related services (including windows update services)
sc create BITS binpath= “c:\windows\system32\svchost.exe -k netsvcs” start= delayed-auto
sc config w32tm type= own
```
