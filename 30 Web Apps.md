# 30 Web Apps

# Web App vulnerability Scanning with WMAP

- WMAP is a powerful, feature-rich web application vulnerability scanner that can be used to enumerate web server enumeration and scan web applications for vulnerabilities
- WMAP is available as an MSF plugin and can be loaded directly into MSF
- WMAP is fully integrated with MSF, which consequently allows us to perform web app vulnerability scanning from within the MSF

### DEMO

```shell
msf6: load wmap
msf6: wmap_ # Press tab
msf6: wmap_sites -a <ip> # Add sites
msf6: wmap_targets -t http://<ip-name>/ # Add targets
msf6: wmap_run -t # Show all enabled modules
msf6: wmap_run -e # Execute
msf6: wmap_vulns -l # List vulns
```

#eJPT #cybersecurity 