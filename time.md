# time useful Linux command line

## how to reconfigure a Linux server timezone 

This commands asks you some question in order to set the time

```bash
sudo dpkg-reconfigure tzdata
```

## how to synchronize time

List of timezones

```bash
timedatectl list-timezones
```

Set you time zone

```bash
timedatectl set-timezone <YOURS>
```

Check `ntpd` status

```bash
systemctl status ntp
```

More status

```bash
ntpq -p
```

Remove `ntp` to switch to **systemd** 

```bash
apt purge ntp
```

Start **systemd** time-sync service

```bash
systemctl start systemd-timesyncd
```

Check the status 

```bash
systemctl status systemd-timesyncd
```

Check if **NTP service** is active

```bash
timedatectl
```

Sample output

```bash
               Local time: Mon 2023-01-23 16:39:10 +0330
           Universal time: Mon 2023-01-23 13:09:10 UTC
                 RTC time: Mon 2023-01-23 13:10:01
                Time zone: Asia/Tehran (+0330, +0330)
System clock synchronized: no
              NTP service: active                                <==== here
          RTC in local TZ: no
```
