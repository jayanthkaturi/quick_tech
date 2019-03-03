### User management
```bash
## /etc/login.defs has the default configurations of adding users like creating group with user_name and adding this user etc.
useradd --shell /bin/bash --b /home/user_name --create_home user_name
groupadd group_name
usermod -aG group_name ## add to group, a -> append
usermod -G group_name ## remove previous groups and add to only group_name
cat /etc/groups ## to know the group info
cat /etc/passwd ## to know a users info
```

### LDAP
```
Read from right to left Eg. ("CN=Dev-India,OU=Distribution Groups,DC=gp,DC=gl,DC=google,DC=com")
String  X.500 AttributeType
------------------------------
CN      commonName
L       localityName
ST      stateOrProvinceName
O       organizationName
OU      organizationalUnitName
C       countryName
STREET  streetAddress
DC      domainComponent
UID     userid
```

```bash
## -x -> simple login kerb, -w passwd -> login with passwd
ldapsearch -h host_name -p port "(cn=[user_name or group_name])" -x
```
