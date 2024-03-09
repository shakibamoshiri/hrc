# tcpdump useful Linux commands 


## how to capture the first TCP push on a port

This will capture one packet that has data on port 22

```bash
tcpdump -vv -X -n -i any  -c 1 "tcp[tcpflags] & (tcp-push) != 0 and port 22"
```
