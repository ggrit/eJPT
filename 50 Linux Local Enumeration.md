# 50 Linux Local Enumeration

# Enumerating System Information - Linux

- After gaining initial access to a target system, it is always important to learn more about the system like, what OS is running as well as the OS version. This information is very useful as it gives us an idea of what we can do and what type of exploits we can run. 

- What are we looking for?
	- Hostname
	- Distribution & distribution release version
	- Kernel version & architecture
	- CPU information
	- Disk information & mounted drives 
	- Installed packages/software

### DEMO

```shell
meterpreter: sysinfo

shell: hostname
shell: cat /etc/issue # Distribution version
shell: cat /etc/*release # Info about distribution
shell: uname -a # Hostname, Kernel version, architecture
shell: uname -r # Kernel version
shell: env # Env variable for specific user
shell: lscpu # CPU info
shell: free -h # RAM consumed
shell: df -h # Drives and disks 
shell: df -ht ext4 # Drives and disks, filtered by file extension 
shell: lsblk | grep sd # Disks infromation
shell: dpkg -l # Installed software/packages 
```


# Enumerating Users & Groups - Linux

- After gaining initial access to a target system, it is always important to learn more about the system like, what user account you have access to and other user accounts on the system.
    
- What are we looking for?
    - Current user & privileges
    - Other users on the system
    - Groups

### DEMO

```shell
meterpreter: getuid

shell: whoami
shell: groups # List groups
shell: groups <user> # Which groups is part of
shell: cat /etc/passwd # List users and service account
shell: cat /etc/passwd | grep -v /nologin # Exclude service account 
shell: w # Currently logged on users
shell: who # Currently logged on users
shell: last # Last logged on users
shell: lastlog # Last logged on users
```


# Enumerating Network Information - Linux

- What are we looking for?
	- Current IP address & network adapter
	- Internal networks
	- TCP/UDP services running and their respective ports
	- Other hosts on the network
	- Routing table

### DEMO

```shell
meterpreter: ifconfig # Interface connected
meterpreter: netstat # Connection list
meterpreter: route # Routing table
meterpreter: arp # ARP table

shell: ifconfig # Interface connected
shell: ip a s # Interface connected
shell: cat /etc/networks # Interface and configuration
shell: cat /etc/hostname # Hostname
shell: cat /etc/hosts # Hosts
shell: cat /etc/resolv.conf # DNS info
shell: arp -a # ARP table
```


# Enumerating Processes & Cron Jobs

- After initial access to a target system, it is always important to learn more about the system like, what processes, services and scheduled tasks are currently running.
    
- What are we looking for?
    - Running processes & services
    - Cron Jobs

### DEMO

```shell
meterpreter: ps # Running processes
meterpreter: pgrep <process> # Show PID of specific process

shell: ps # Running processes
shell: ps aux # More processes info 
shell: ps aux | grep <name> # Grep example
shell: top # List processes in dynamic view
shell: crontab -l # Cron Jobs for specific user
shell: ls -la /etc/cron* # Display all Cron files
shell: cat /etc/cron* # Display Cron Job
```


# Automating Linux Local Enumeration

- In addition to performing local enumeration manually, we can also automate the process with the help of a few scripts and MSF modules.
- While local enumeration techniques/commands are important to know, as a penetration tester, you will need to be time efficient. As a result, you will need to learn how to utilize various automated enumeration scripts.
- In addition to automating the process of enumerating information like system information, users & groups etc, these automated enumeration scripts will also provide you with additional information regarding the target system like; privilege escalation vulnerabilities, locally stored passwords etc.

## Linux Local enum Scripts

- **LinEnum**
	- A simple bash script that automates common Linux local enumeration checks in addition to identifying privilege escalation vulnerabilities.
	- https://github.com/rebootuser/LinEnum

### DEMO

```shell
msf6: post(linux/gather/enum_configs) # Linux gather configurations
msf6: post(linux/gather/enum_network) # Linux gather network information
msf6: post(linux/gather/enum_system) # Linux gather system and user information
msf6: post(linux/gather/checkvm) # Check VM

meterpreter: upload linenum.sh
meterpreter: shell
shell: chmod +x linenum.sh
shell: ./linenum.sh
```


#cybersecurity #eJPT 