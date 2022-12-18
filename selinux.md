# SeLinux useful Linux commands


## how to disable selinux temporarily 
```bash
# check the status
sestatus

# disable/permissive it
sudo setenforce 0

# check the status
sestatus
```

## how to disable selinux permanently
```bash
# check the status
sestatus

# edit the file
sudo vim /etc/sysconfig/selinux

# update 
SELINUX=enforcing
# to
SELINUX=permissive
# or
SELINUX=disable

# reboot
# then check
sestatus
```


