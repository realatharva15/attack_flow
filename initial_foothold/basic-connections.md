# Basic connection methods which you usually forget:

`1. connecting to a windows machine via xfreerdp`

```bash
xfreerdp /v:<target_ip> /u:<username> /p:<password> /cert:ignore +fonts
```

`2. listing samba shares using smbclient`

```bash
smbclient -L //10.49.137.168 -N
```
