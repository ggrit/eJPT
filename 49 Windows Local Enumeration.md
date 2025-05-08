# 49 Windows Local Enumeration

# Enumerating System Information - Windows

- After gaining initial access to a target system, it is always important to learn more about the system like, what OS is running as well as the OS version. This information is very useful as it gives us an idea of what we can do and what type of exploits we can run.

- What are we looking for?
	- Hostname
	- OS Name (Windows 7, 8 etc)
	- OS Build & Service Pack (Windows 7 SP1 7600)
	- OS Architecture (x64, x86)
	- Installed updates/Hotfixes 

### DEMO

```shell
meterpreter: getuid
meterpreter: sysinfo
meterpreter: show_mount # Show mounts/drives
meterpreter: cat \Windows\System32\eula.txt 
# With Windows commands
meterpreter: shell
shell: hostname
shell: systeminfo # Really useful
shell: wmic qfe get Caption,Description,HotFixID,InstalledOn # Enum hotfixes and installed updates, particulary interested in Security Update
```


# Enumerating Users & Groups - Windows

- After gaining initial access to a target system, it is always important to learn more about the system like, what user account you have access to and other user accounts on the system.

- What are we looking for?
	- Current user & privileges
	- Additional user information
	- Other users on the system
	- Groups
	- Members of the built-in administrator group

### DEMO

```shell
meterpreter: getprivs # Privilege info
msf6: postwindows/gather/enum_logged_on_users) # Current and recently logged-on users

# Windows commands
meterpreter: shell
shell: whoami
shell: whoami /priv # Privilege info 
shell: query user # User currently logged-on 

shell: net users # All user account on the system
shell: net user <user> # More info about specific user

shell: net localgroup # Enum groups 
shell: net localgroup <name> # Enum users in a group  
```


# Enumerating Network Information - Windows

- What are we looking for?
	- Current IP address & network adapter
	- Internal networks
	- TCP/UDP services running and their respective ports
	- Other hosts on the network
	- Routing table
	- Windows Firewall state

### DEMO

```shell
shell: ipconfig # Current adapters connected 
shell: ipconfig /all # More adapters/NIC info

shell: route print # Routing table

shell: arp -a # Discover others devices on the network

shell: netstat -ano # Open connections, services running and their ports

shell: netsh firewall show state # Windows Firewall configuration and state
shell: netsh advfirewall show allprofiles # Windows Firewall configuration and state
```


# Enumerating Processes & Services

- After initial access to a target system, it is always important to learn more about the system like, what processes, services and scheduled tasks are currently running. 

- What are we looking for?
	- Running processes & services
	- Scheduled tasks

- A process is an instance of a running executable (.exe) or program.
- A service is a process which runs in the background and does not interact with the desktop. 

### DEMO

```shell
meterpreter: ps # Process list 
meterpreter: pgrep <name>.exe # Search for a process, then tell me the ID
meterpreter: migrate <PID> # Recommended to migrate to explorer.exe (stable)


shell: net start # Windows services are started, NOT processes 
shell: wmic service list brief # List all services 
shell: tasklist /SVC # Process that are running and services under process (useful)

shell: schtasks /query /fo LIST /v # List scheduled tasks (lot output)
```


# Automating Windows Local Enumeration 

- In addition to performing local enumeration manually, we can also automate the process with the help of a few scripts and MSF modules.
- While local enumeration techniques/commands are important to know, as a penetration tester, you will need to be time efficient. As a result, you will need to learn how to utilize various automated enumeration scripts.
- In addition to automating the process of enumerating information like system information, users & groups etc, these automated enumeration scripts will also provide you with additional information regarding the target system like; privilege escalation vulnerabilities, locally stored passwords etc. 

## Windows Local Enum Scripts

- **JAWS**
	- Just Another Windows (Enum) Script
	- A PowerShell script designed to help penetration testers quickly identify potential privilege escalation vectors on Windows systems. It is written using PowerShell 2.0 so 'should' run on every Windows version since Windows 7.
	- https://github.com/411Hall/JAWS

### DEMO

```shell
# Some useful MSF post module 
msf6: post(windows/gather/win_privs) # Show current user privileges
msf6: post(windows/gather/enum_logged_on_users) # Enum current and recently logged on users
msf6: post(windows/gather/checkvm) # Check if running in VM 
msf6: post(windows/gather/enum_applications) # Enum installed applications
msf6: post(windows/gather/enum_computers) # Enum computer in Active Directory domain
msf6: post(windows/gather/enum_patches) # Installed patches, HotFix ID
msf6: post(windows/gather/enum_shares) # SMB shares 

# JAWS
nano jaws.ps1 # If necessary, copy the raw from github in a new local file
meterpreter: cd C:\\
meterpreter: mkdir Temp # In future can delete it
meterpreter: cd Temp
meterpreter: upload jaws.ps1
meterpreter: shell
shell: powershell.exe -ExecutionPolicy Bypass -File .\jaws.ps1 -OutputFilename JAWS-Enum.txt
shell: [CNTL + C]
meterpreter: download JAWS-Enum.txt
```


#cybersecurity #eJPT 