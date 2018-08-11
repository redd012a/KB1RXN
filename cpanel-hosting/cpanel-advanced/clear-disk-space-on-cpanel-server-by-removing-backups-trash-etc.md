# Clear disk space on cPanel Server by removing backups, trash etc



```text
for user in `/bin/ls -A /var/cpanel/users` ; do rm -fv /home*/$user/backup-*$user.tar.gz ; done
rm -fv /home*/*/tmp/Cpanel_*
rm -rfv /home*/*/softaculous_backups
rm -rfv /home*/*/public_html/wp-content/updraft/*
find /home*/*/.trash/* -exec rm -rf {} \;
#find /home -type f -name error_log -exec rm -f {} \;
yum clean all
rm -rf /var/cache/yum
find /home -type f -name error_log -exec rm -f {} \;
```

