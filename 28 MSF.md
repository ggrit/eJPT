# 28 MSF

# Vulnerability Scanning with MSF

- Vulnerability scanning & detection is the process of scanning a target for vulnerabilities and verifying whether they can be exploited
- So far, we have been able to identify and exploit misconfiguration on target systems, however, in this section we will be exploring the process of utilizing auxiliary and exploit modules to scan and identify inherent vulnerabilities in services, operating systems and web applications
- This information will come in handy during the exploitation phase of this course
- We will also be exploring the process of utilizing third party vulnerability scanning tools like Nessus and how we can integrate Nessus functionality in to the MSF

```shell
searchsploit # Search exploit in exploitdatabase
searchsploit | grep -e "Metasploit"
msf6: db_nmap -sS -sV -O <ip>
msf6: hosts, services
msf6: db_autopwn -p -t -PI <port>
msf6: analyze, vulns
```

#eJPT #cybersecurity 