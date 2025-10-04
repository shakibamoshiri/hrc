# tcpdump useful Linux commands 


## how to capture the first TCP push on a port

This will capture one packet that has data on port 22

```bash
tcpdump -vv -X -n -i any  -c 1 "tcp[tcpflags] & (tcp-push) != 0 and port 22"
```

note:  
we can use `tcpflow` to capture only the tcp payload 

```bash
tcpflow -C -i lo  dst port 9091
```

this will outbound the tcp payload of tls offloaded which destination port is 9091

## how to filter SSH connection when we do not know the SSH port

Checking TCP header and capture one packet when matched

```bash
tcpdump -vv -X -n -i any  -c 1 'tcp[32:4] = 0x5353482d'
```

see this question and answer 

- [how fast a firewall/DPI system can find an ssh server IP on a random port](https://superuser.com/questions/1822830/how-fast-a-firewall-dpi-system-can-find-an-ssh-server-ip-on-a-random-port)


## how to capture SNI using tcpdump 

```bash
tcpdump -i any  -s 1500 port 443  and  '(tcp[((tcp[12:1] & 0xf0) >> 2)+5:1] = 0x01) and (tcp[((tcp[12:1] & 0xf0) >> 2):1] = 0x16)' -nnXSs0 -ttt
```
# https://www.baeldung.com/linux/tcpdump-capture-ssl-handshake

```bash
tcpdump -vv -X -n -i any   -c 1  'tcp[32:4] = 0x5353482d'
tcpdump -vv -X -n -i any   -c 10  "tcp[tcpflags] & (tcp-push) != 0 and src port 989"
tcpdump -vv -X -n -i any   -c 10 '(tcp[((tcp[12] & 0xf0) >>2)] = 0x16)  && (tcp[((tcp[12] & 0xf0) >>2)+5] = 0x01) and port 8080'
```
