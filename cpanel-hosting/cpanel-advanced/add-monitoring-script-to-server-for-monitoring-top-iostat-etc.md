# Add monitoring script to server for monitoring top, iostat etc

Create a directory under /var/log/server-status

Inside this directory, create a file called ‘getstats.sh’ and paste the following contents…

```text
#!/bin/sh
path="/var/log/server-status"
ddd=`date +%Y-%m-%d`
logfile=$path/$ddd/logfile.txt

### Check if direction to store log exists, if doesn't - create it ###
if [ ! -d $path/$ddd ]; then
    mkdir $path/$ddd
fi

### Add blank line and head 5 of top on every script run ###
echo >> $logfile
echo "!-------------------------------------------- top 20" >> $logfile
COLUMNS=512 /usr/bin/top -cSb -n 1 | head -20                           >> $logfile

echo "!---------------------------------------- vmstat 1 4" >> $logfile
/usr/bin/vmstat 1 4                                         >> $logfile

### Check if load average is greater or equal 7 if it does - collect needed stats ###

if [ `cat /proc/loadavg | /usr/bin/awk '{ print $1 }' | /usr/bin/cut -d. -f1-1` -ge 3 ]
then

### INSERT custom gathering commands after this line, they are executed only when LA is above 7

###

echo "!---------------------------------- netstat by state" >> $logfile
/bin/netstat -an|awk '/tcp/ {print $6}'|sort|uniq -c        >> $logfile

echo "!-------------------------------- ps by memory usage" >> $logfile
ps aux | sort -nk +4 | tail                                 >> $logfile

echo "!------------------------------------- iotop -b -n 3" >> $logfile
/usr/sbin/iotop -b -o -n 3                                  >> $logfile

echo "!------------------------------------------- ps axuf" >> $logfile
ps axuf                                                     >> $logfile

echo "!---------------------------- mysqladmin processlist" >> $logfile
/usr/bin/mysqladmin processlist -v                          >> $logfile

fi

### Do something more if load average does not match threshold ###

### Remove directories older then 30 days ###
cd $path
ls -1r|grep -v getstatus|sed -n '30,$p'|xargs -i rm -rf "{}"
```

You will also need to create a cron for this…

```text
vi /etc/cron.d/getstats
```

```text
* * * * * root /usr/bin/flock -n /var/run/cloudlinux_getstats.cronlock /bin/sh /var/log/server-status/getstats.sh >/dev/null 2>&1
```

