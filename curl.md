# curl useful Linux commands 


## how to run speedtest with curl and python

```bash
curl -sL https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3 -
```

## how to check speed with more servers 

```bash
### method 1
curl -sL network-speed.xyz | bash -s -- -r eu

### method 2
curl -Lso- bench.sh | bash
```

## how to speed test with curl 

```
### 10M Download
curl --dump-header - --connect-timeout 10 -o /dev/null https://speed.cloudflare.com/__down?bytes=$((10 * 1024 * 1024))

### 10M Upload
curl --dump-header - --connect-timeout 10 -o /dev/null -F up=@/dev/zero https://speed.cloudflare.com/__up?bytes=$((10 * 1024 * 1024))
```

## how to speed test with curl over a socks5 proxy 

```
### 10M Download
curl --dump-header - --socks5-hostname 127.0.0.1:2080 --connect-timeout 10 -o /dev/null https://speed.cloudflare.com/__down?bytes=$((10 * 1024 * 1024))

### 10M Upload
curl --dump-header - --socks5-hostname 127.0.0.1:2080 --connect-timeout 10 -o /dev/null -F up=@/dev/zero https://speed.cloudflare.com/__up?bytes=$((10 * 1024 * 1024))
```

## how to check an IP reputation with curl 

```
### try you own IP address
curl --dump-header - https://reputation.noc.org/api/?ip=1.1.1.1

```
### note
You can check the link [https://reputation.noc.org](https://reputation.noc.org) in your browser


