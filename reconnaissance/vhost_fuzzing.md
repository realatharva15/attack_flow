# vHost fuzzing using Gobuster

just make sure that the domain you are trying to fuzz is present in your /etc/hosts file. if not present, then use the following command:

```bash
echo "<target-ip> <domain>" | sudo tee /etc/hosts
```

now we have to use the following command for fuzzing the host

```bash
gobuster vhosts -u http://<target-ip> --domain <domain> -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt --append-domain
```
