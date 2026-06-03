# Automated SQLi using sqlmap
first enumerate the databases:
for this to happen we should find the url which contains any parameters. sqlmap needs these parameters so that it can inject SQLis into it. even i parameters are not found, find any directory whose subdirectories are in a predictible manner

in the CTF by THM named Revenge, i found such a directory named /products. the page was getting refreshed when the subdirectory was changed from /products/ to /products/1 and so on.

```bash
sqlmap -u http://<target_ip>/products/1 --dbs
```
in this manner, the database of the website were enumerated
