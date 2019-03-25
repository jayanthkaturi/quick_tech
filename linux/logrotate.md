```bash
## Dry run a logrotate config file
logrotate -d /etc/logrotate.d/apache2.conf

## In /etc/logrotate.d/ folder or /etc/logrotate.conf file
/var/log/squid/access.log {
    monthly ## frequency
    create 0644 root root ## permissions
    rotate 5 ## only 5 old records
    size=1M ## min size for log file to be rotated
    dateext ## add date extension
    dateformat -%d%m%Y ## format for date
    notifempty ## do not rotate if log is empty
    compress
    delaycompress ## both indicate that the rotated files excluding the latest one should be compressed.
    postrotate
      ## Custom script to run after rotate
      echo "A rotation just took place." | mail root
    endscript
}
```
