# SSH useful Linux command line

## how to make fake traffic using SSH
The `pv` command should be installed if you liked to check the speed, otherwise, you can remove it.

```
ssh REMOTE_SERVER  'cat /dev/urandom' | pv | cat - &> /dev/null
```

## how to make fake traffic using SSH with crontab
Every hour on Sun, Tue, The will run


```bash
0 */1 * * 0,2,4 timeout 30s ssh irj  'cat /dev/urandom' | pv | cat - &> /dev/null
```


