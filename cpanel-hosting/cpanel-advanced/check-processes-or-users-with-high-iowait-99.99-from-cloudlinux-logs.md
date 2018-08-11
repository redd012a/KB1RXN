# Check processes or users with high iowait \(99.99%\) from Cloudlinux Logs



A handy script! I wrote this script to extract the highest ‘waiting’ processes to diagnose high IO wait issues from users, where the results are not obvious from the LVE stats…

```text
grep 99.99 ../*/logfile.txt | tail -n -100000 | awk -v x=12 '{print $x}' | awk -F'/' '{print $2,$3}' | sort | uniq -c | sort -n
```

