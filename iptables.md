# iptables useful Linux command line

## how to clear all iptables rules 
```bash
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X
```

 - [best way to clear all iptables rules](https://serverfault.com/questions/200635/best-way-to-clear-all-iptables-rules)

## how to allow VPN traffic with iptables
There are three **nat** rules for three VPN servers.  
Change IP address accordingly and `ens160` which is your server interface.  

```bash
iptables -t nat -A POSTROUTING -s 10.147.252.0/24 -o ens160 -m comment --comment openvpn-nat-rule -j MASQUERADE
iptables -t nat -A POSTROUTING -s 10.43.193.0/24 -o ens160 -m comment --comment wireguard-nat-rule -j MASQUERADE
iptables -t nat -A POSTROUTING -s 10.10.10.0/24 -o ens160 -m comment --comment openconnect-nat-rule -j MASQUERADE
```
