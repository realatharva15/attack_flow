# Subdomain fuzzing using gobuster
lets say that the domain name is `nahamstore.thm`. then the command to find subdomains using gobuster would be:

```bash
gobuster vhost -u http://nahamstore.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```
if the response size of the wrong subdomains is the same, you can filter them out by using the `--exclude <common_response_length>` flag. lets say that the common response length is around 900 bytes. we can filter that out by:

```bash
gobuster vhost -u http://nahamstore.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt --exclude-length 900
```

# Subdomain fuzzing using ffuf
sometimes gobuster doesn't work properly for subdomain fuzzing. use ffuf instead. 

```bash
ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt \
  -u http://nahamstore.thm \
  -H "Host: FUZZ.nahamstore.thm" \
  -fw 125
```
here in this command, the response size was variable but the word count of the failure response was constant(125 words). thats why we used the `-fw 125` flag.
