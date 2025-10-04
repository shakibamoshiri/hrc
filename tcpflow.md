# tcpflow useful Linux commands 


## how to capture tcp payload 

```bash
tcpflow -C -i lo  dst port 9091
```

this will outbound the tcp payload of tls offloaded which destination port is 9091

## how to convert tcpflow payload into hex

```bash
tcpflow -C -i lo  dst port 9091 | hexdump -C

# or

tcpflow -C -i lo  dst port 9091 | xxd
```
