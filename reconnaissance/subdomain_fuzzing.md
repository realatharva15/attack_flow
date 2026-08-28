# Subdomain fuzzing using gobuster
lets say that the domain name is `nahamstore.thm`. then the command to find subdomains using gobuster would be:

```bash
gobuster vhost -u http://nahamstore.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```
