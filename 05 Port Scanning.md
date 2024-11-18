# 05 Port Scanning

## Port Scanning With nMap
```bash
default: -sT full TCP (1000 commonly use)
default root: -sS SYN Scan (1000 commonly use)
nmap -Pn (no ping, no host discovery)
nmap -sU UDP scan
nmap -F (fast 100 commonly use)
```

## Service Version & OS Detection
```bash
nmap -sV Service Version
nmap -sV Service Version —version-intesity (set 0 to 9)
nmap -O Operating System
nmap -O —osscan-guess (aggressive)
```

## nMap Scripting Engine (NSE)
```bash
ls -al /usr/share/nmap/scripts/
nmap -sC (default)
nmap —script=<name>
nmap —script-help=<name> (info)
```

## Scan
```bash
nmap -A: OS detection, version detection, script scanning, and traceroute
```

#eJPT #cybersecurity 