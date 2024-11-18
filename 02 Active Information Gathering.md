# 02 Active Information Gathering

## DNS zone transfers

```bash
dig (lookup)
dnsenam
fierce (reconnaissance non-contiguous IP)
```

## Host discovery nMap

```bash
nmap -sn <IP>
netdiscover (ARP request)
```

## Port scanning with nMap

```bash
nmap
-Pn = skip host discovery (no ping, use with firewall)
-sV = service info
-O = os info
-sC = script
-A = -Sv, -O, -sC, --traceroute
-T = (0-5 timing)

-oN = save .txt
-oX = save .xml
```

![[Screenshot 2024-08-30 at 18.24.20.png]]

![[Screenshot 2024-08-30 at 18.23.52.png]]

#eJPT #cybersecurity 