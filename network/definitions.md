### DMVPN
```
A dynamic multipoint virtual private network (DMVPN) is a secure network that exchanges data
between sites without needing to pass traffic through an organization's headquarter
virtual private network (VPN) server or router.
```

### AS_PATH
```
Prepend AS (autonomous system) number/IP along the path to avoid loops in BGP protocol.
RIP (Routing Information Protocol) limits 16 hops to avoid loops.
```

### NAT Hairpinning
```
Access intra LAN end points through the public address of the gateway.

Eg:
Gateway address: 192.168.0.1
Host 1: 192.168.0.5
Host 2: 192.168.0.7
The gateway has an external IP : 192.0.2.1
Host 1 runs a P2P application P1 on its port 12345 which is externally mapped to 4444.
Host 2 runs a P2P application P2 on its port 12345 which is externally mapped to 5555.
If the NAT device supports hairpinning, then P1 application can connect to the P2 application using the external endpoint 192.0.2.1:5555. If not, the communication will not work.
```

### OOB (Out of Band Management)
```
Managing network device through dedicated cable, not the input/output cable used by that device for regular purposes.
```

### Split DNS
```
Split Domain Name System (Split DNS) is an implementation in which separate DNS servers
are provided for internal and external networks as a means of security and privacy management.
```
