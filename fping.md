# fping useful Linux command line

## how to find alive hosts and sort the result 
```bash
fping -aeqg 162.159.192.0/24 | sed 's/[()]//g' | sort -rnk2 | column -t
```

the fastest are shown at the bottom of the result, if you want to see the top 10 apply this (remove `-r` of `sort` command)

```bash
fping -aeqg 162.159.192.0/24 | sed 's/[()]//g' | sort -nk2 | column -t | head

# sample output
162.159.192.155  64.2  ms
162.159.192.200  64.2  ms
162.159.192.233  64.2  ms
162.159.192.62   64.2  ms
162.159.192.123  64.3  ms
162.159.192.80   64.3  ms
162.159.192.90   64.3  ms
162.159.192.95   64.3  ms
162.159.192.106  64.4  ms
162.159.192.34   64.4  ms
```

the options

```bash
fping --help | grep -e -a, -e -e, -e q, -e -g, 
   -g, --generate     generate target list (only if no -f specified),
   -a, --alive        show targets that are alive
   -e, --elapsed      show elapsed time on return packets
   -q, --quiet        quiet (don't show per-target/per-ping results)
```
