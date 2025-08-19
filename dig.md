# dig useful Linux commands 


## how to query to DoT server using dig?

```bash
### https://developers.cloudflare.com/1.1.1.1/encryption/dns-over-tls/

# no debug mode
dig @1.0.0.1 +tls-ca +tls-host=one.one.one.one youtube.com

# enable debug mode
dig -d @1.0.0.1 +tls-ca +tls-host=one.one.one.one youtube.com

### notice
# port 853 should be opened 

### tcpdump check 
# tcpdump -qni any dst port 853
```
