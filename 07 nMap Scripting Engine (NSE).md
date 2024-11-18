# 07 nMap Scripting Engine (NSE)

## Port Scanning & Enumeration with nMap
```bash
nmap -Pn -sV -O
```

## Importing nMap Scan Result into MSF
```bash
nmap -oX
service postgresql start
msfconsole
msf6: db_status
msf6: workspace -a <name>
msf6: db_import </path>
msf6: hosts
smsf6: ervices
msf6: vulns
msf6: db_nmap
```

## Port Scanning With Auxiliary Modules
```bash
msf6: search portscan
msf6: use <id or path>
msf6: show options
msf6: set RHOSTS <IP>
msf6: exploit
meterpreter: sysinfo
meterpreter: shell
meterpreter: /bin/bash -i
msf6: sessions
```

#eJPT #cybersecurity 