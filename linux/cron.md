### Syntax

```bash
* * * * *
## min(0-59) hour(0-23) day_of_month(1-31) month(1-12) day_of_week(0-6, sunday = 0)

crontab -e ## edit

# For example you can enter this to run a backup of all your user accounts at 5 a.m every week with:
0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
```
