# DNS useful Linux command line

## how to properly setup DNS on Linux machines 

### setup the Global DNS in resolved
In `/etc/systemd/resolved.conf` update `DNS` to yours.

Also `DNSStubListener` , you sand set it **no** to avoid listening on port 53 (if you needed this port)

```bash
[Resolve]
DNS=8.8.8.8 1.1.1.1
#FallbackDNS=
#Domains=
#LLMNR=no
#MulticastDNS=no
#DNSSEC=no
#DNSOverTLS=no
#Cache=no-negative
DNSStubListener=no
#ReadEtcHosts=yes
```

Then restart the service

```bash
sudo systemctl restart systemd-resolved.service
```

Check the status

```bash
resolvectl status
```

### Disable DNS processing in NetworkManager
In `/etc/NetworkManager/conf.d/dns.conf` add the following.  
If the path or file was not there, make/create them.

```bash
[main]
# do not use the dhcp-provided dns servers, but rather use the global
# ones specified in /etc/systemd/resolved.conf
dns=none
systemd-resolved=false
```

Then reload it

```
sudo systemctl reload NetworkManager.service
```

NOTE: if you are using a server not a desktop, you might not have **NetworkManager** on your server.

 - [source](https://andrea.corbellini.name/2020/04/28/ubuntu-global-dns/)   

### Update your /etc/resolv.conf file

Run the following 

```bash
sudo ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

and reboot your machine, when it came up, you should see what you have set for `DNS=` in `/etc/systemd/resolved.conf`.


 - [source](https://www.linuxuprising.com/2020/07/ubuntu-how-to-free-up-port-53-used-by.html)   


## How to query using resolvectl

First example

```bash
>>> resolvectl  query google.com
google.com: 216.239.38.120                     -- link: wlp2s0

-- Information acquired via protocol DNS in 43.2ms.
-- Data is authenticated: no; Data was acquired via local or encrypted transport: no
```

Second example 

```bash
>>> resolvectl --legend=no -t A query google.com
google.com IN A 216.239.38.120
```

 - [source](https://www.freedesktop.org/software/systemd/man/resolvectl.html)
