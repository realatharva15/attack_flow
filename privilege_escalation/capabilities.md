# ROOT Access via Capabilities:

unlike the regular privileges which are atomic (all or nothing), eg. root user has privileges while a normal user does not, the capabilities feature allows the users to have privileges for some specific processes.

for instance take a process with cap_setuid → Can ONLY change UID (no other root powers). this cap_setuid can be exploited by setting the uid to 0 (root).

here the perl interpreter has the cap_setuid+ep capability set. lets use a one-liner from GTFObins to exploit it.
