# 29 Nessus

# Vulnerability Scanning with Nessus

- Nessus is a proprietary vulnerability scanner developed by Tenable
- We can utilize Nessus to perform a vulnerability scan on a target system, after which, we can import the Nessus results in to MSF for analysis and exploitation
- Nessus automates the process of identifying vulnerabilities and also provides us with information pertinent to a vulnerability like the CVE code
- We can use the free version of Nessus (Nessus Essentials), which allows us to scan up to 16 IPs

## Export to MSF and use

```shell
db_import <path> # First, export scanning from Nessus
msf6: vulns -p <port> # Specify port for vulns
msf6: search cve:<year> name:<service>
```

#eJPT #cybersecurity 