# tcpdump useful Linux commands 


## how to capture the first TCP push on a port

This will capture one packet that has data on port 22

```bash
tcpdump -vv -X -n -i any  -c 1 "tcp[tcpflags] & (tcp-push) != 0 and port 22"
```

## how to filter SSH connection when we do not know the SSH port

Checking TCP header and capture one packet when matched

```bash
tcpdump -vv -X -n -i any  -c 1 'tcp[32:4] = 0x5353482d'
```

see this question and answer 

- [how fast a firewall/DPI system can find an ssh server IP on a random port](https://superuser.com/questions/1822830/how-fast-a-firewall-dpi-system-can-find-an-ssh-server-ip-on-a-random-port)
