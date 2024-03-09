# ip useful Linux commands 

## how test socks5 speed with iperf3 

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

```bash
ssh -vNTC -w 77:77 REMOTE_SERVER
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

---


