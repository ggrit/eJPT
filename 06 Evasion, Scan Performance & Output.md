# 06 Evasion, Scan Performance & Output

## Firewall Detection & IDS Evasion
```bash
nmap -sA: ACK
nmap -f; --mtu <val>: fragment packets (optionally w/given MTU)
nmap --ttl <val>: Set IP time-to-live field
nmap --data-length (random data to sent packets)
nmap -g <portnum>
nmap -D decoy1[,decoy2][,ME][,...] (Cloak a scan with decoys)
nmap -n: no DNS resolution
```

## Optimizing nMap Scans
```bash
nmap -T<0-5>: Set timing template (higher is faster)
nmap —scan-delay/—max-scan-delay <time>: Adjust delay between probes
nmap —host-timeout <time>: Give up on target after this long
```

## nMap Output Formats
```bash
nmap -oX/-oS/-oG <file>: Output scan in normal, XML, s|<rIpt kIddi3, and Grepable format
nmap -v
nmap —reason: reason a port is in a particular state
```

#eJPT #cybersecurity 