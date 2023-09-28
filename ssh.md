# SSH useful Linux command line

## local port forwarding
forward (= send) from local (`1111`) to a remote (=receive) (`2222`)

```bash
ssh -L localhost:1111:localhost:2222 remote
```

use case: 
 - access an single port/application from a private network

## remote port forwarding
forward (= send) from remote (`2222`) to a local (= receive) (`1111`)

```bash
ssh -R localhost:2222:localhost:1111 remote
```

use case: 
 - expose a single port/application from a public network to private one

## dynamic port forwarding
forward (= send) from local (`1111`) to remote (= receive) (`all ports + interfaces`)

```bash
ssh -D localhost:1111 remote
```

use case: 
 - access a network (usually public network) from a private one
 - open FireFox, add localhost:1111 as socks5 to access the remote network (`in local network`)

## remote dynamic port forwarding (new feature)
forward (= send) from remote to local (= receive) (`all ports + interfaces`)

```bash
ssh -R localhost:2222 remote
```

use case:
 - expose a network (usually private network) to a public one
 - open FireFox, add localhost:1111 as socks5 to access the local network (`in remote network`)

--- 

## better dynamic port forwarding 

```bash
ssh -o ConnectTimeout=10 -fNTCD localhost:1234 remote

# -f : fork = go to background
# -N : N not command will be executed at remote 
# -T : no TTY
# -C : Compression on
# -D : dynamic
```

## better remote dynamic port forwarding 

```bash
ssh -o ConnectTimeout=10 -fNTCR localhost:1234 remote

# -f : fork = go to background
# -N : N not command will be executed at remote 
# -T : no TTY
# -C : Compression on
# -R : remote
```


## test access to/from dynamic/remote-dynamic port forwarding

```bash
curl --socks5-hostname localhost:PORT api.ipify.org
```

## check which applications are connecting to

```bash
# on remote/local
lsof -ni :PORT
```
## how to make fake traffic using SSH
The `pv` command should be installed if you liked to check the speed, otherwise, you can remove it.

```
ssh REMOTE_SERVER  'cat /dev/urandom' | pv | cat - &> /dev/null
```

## how to make fake traffic using SSH with crontab
Every hour on Sun, Tue, The will run


```bash
0 */1 * * 0,2,4 timeout 30s ssh REMOTE_SERVER'cat /dev/urandom' | pv | cat - &> /dev/null
```
