# Checklist for privilege escalation:

`1.` **Look out for any sudo privileges**
```bash
sudo -l
```

`2.` **Search for any suspicious SUIDs**
```bash
find / -type f -perm -4000 2>/dev/null
```

`3.` **Scan for any cronjobs/background tasks**
```bash
cat /etc/crontab
```
or
```bash
# transfer pspy64 to the target machine to scan background tasks
chmod +x pspy64
./pspy64
```
`4.` **Lookout for any open sockets**
```bash
ss -tlnp
```
