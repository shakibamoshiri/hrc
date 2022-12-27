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
