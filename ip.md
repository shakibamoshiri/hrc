# ip useful Linux commands 

## how to test socks5 speed with iperf3 between two servers

### server A

```bash
ip tuntap add dev tun77 mode tun
ip addr add 192.168.77.2/30 brd + dev tun77
ip link set tun77 up
```

### server B

```bash
ip tuntap add dev tun77 mode tun
ip addr add 192.168.77.1/30 brd + dev tun77
ip link set tun77 up
```

### server A

the localhost:7373 will be the socks5 server address:port

```bash
ssh -vNTCD localhost:7373  REMOTE_SERVER
```

### server A

download tun2socks binary files [https://github.com/xjasonlyu/tun2socks/releases](https://github.com/xjasonlyu/tun2socks/releases)
and 

```bash
./tun2socks  -device tun0 -proxy socks5://127.0.0.1:7373
```

### server A

check with `ping` both ips

 - 192.168.77.2
 - 192.168.77.1

### server B

run `iperf3` server mode 

```bash
iperf3 --server 
```

### server A

run `iperf3` client mode 

```bash
iperf3 --client 192.168.77.1 # server B ip 
```

### NOTE

if you did not want to test socks5 but just SSH you can use 

```bash
ssh -vNTC -w 77:77 REMOTE_SERVER
```

---


