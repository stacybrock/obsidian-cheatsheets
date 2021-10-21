# cron

## Run on Reboot
Files can be placed in `/etc/cron.d/`
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
@reboot root /root/some-script.sh 2>&1 >> /tmp/somescript.log
```
