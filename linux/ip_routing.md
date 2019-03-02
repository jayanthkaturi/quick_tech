### Commads
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
