# curl useful Linux commands 


## how to check speed with curl and cloudflare 

### download 

Run for 10 seconds to see average whine 10 seconds

```bash
curl --max-time 10 -o /dev/null https://speed.cloudflare.com/__down?bytes=9000000000
```

### upload 

Run for 10 seconds to see average whine 10 seconds

```bash
curl --max-time 10 -o /dev/null -F up=@/dev/zero https://speed.cloudflare.com/__up?bytes=9000000000
```

## how to run speedtest with curl and python

```bash
curl -sL https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3 -
```

## how to check speed with more servers 

```bash
curl -sL network-speed.xyz | bash -s -- -r eu
```
