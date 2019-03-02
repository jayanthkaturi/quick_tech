### Commands
```bash
ifconfig ## show interfaces on a host
ifconfig [interface] up ## bring up an interface (eg. eth0)
ifconfig [interface] down ## bring down an interface (eg. eth0)
/etc/init.d/networking restart ## restart networking interfaces
dhclient -r [interface (optional)] ## release ip address on interface
dhclient [interface (optional)] ## get an ip address
```

### Routing Commads
```bash
route -n ## show kernel routing table
ip route ## or ip r
ip r show table local ## show local routing table
ip r add [dst_ip/subnetmask] via [gateway_addr] ## add route
ip r del [dst_ip/subnetmask] ## delete route
```

### IP scope and it's validity
```
global - valid everywhere
site - valid only within this site (IPv6)
link - valid only on this device
host - valid only inside this host (machine)
```
