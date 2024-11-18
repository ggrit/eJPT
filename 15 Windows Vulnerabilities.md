# 15 Windows Vulnerabilities

## Overview

- Microsoft Windows has various OS versions and releases which makes the threat surface fragmented in terms of vulnerabilities. For example, vulnerabilities that exist in Windows 7 are not present in Windows 10.
- Regardless of the various versions and releases, all Windows OS’s share a likeness given the development model and philosophy:
	- Windows OS’s have been developed in the C programming language, making them vulnerable to buffer overflows, arbitrary code execution etc.
	- By default, Windows is not configured to run securely and require a proactive implementation of security practices in order to configure Windows to run securely.
	- Newly discovered vulnerabilities are not immediately patched by Microsoft and given the fragmented nature of Windows, many systems are left unpatched.
- The frequent releases of new versions of Windows is also a contributing factor to exploitation, as many companies take a substantial length of time to upgrade their systems to the latest version of Windows and opt to use older versions that may be affected by an increasing number of vulnerabilities.
- In addition to inherent vulnerabilities, Windows is also vulnerable to cross platform vulnerabilities, for example SQL injection attacks.
- Systems/hosts running Windows are also vulnerable to physical attacks like; theft, malicious peripheral devices etc.

## Types

- **Information disclosure:** Vulnerability that allows an attacker to access confidential data.
- **Buffer overflows:** Caused by a programming error, allows attackers to write data to a buffer and overrun the allocated buffer, consequently writing data to allocated memory addresses.
- **Remote code execution:** Vulnerability that allows an attacker to remotely execute code on the target system.
- **Privilege escalation:** Vulnerability that allows an attacker to elevate their privileges after initial compromise.
- **Denial of Service (DOS):** Vulnerability that allows an attacker to consume a system/host’s resources (CPU, RAM, Network etc) consequently preventing the system from functioning normally.

## Frequently Exploited

| **Protocol/Service**                            | **Ports**          | **Purpose**                                                                                                                                              |
| ----------------------------------------------- | ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft IIS (Internet Information services)   | TCP ports 80/443   | Proprietary web server software developer by Microsoft that runs on Windows                                                                              |
| WebDAV (Web Distributed Authoring & Versioning) | TCP ports 80/443   | HTTP extension that allows client to update, delete, move and copy files on a web server. WebDAV is used to enable a web server to act as a file server. |
| SMB/CIFS (Service Message Block Protocol)       | TCP port 45        | Network file sharing protocol that is used to facilitate the sharing of files and peripherals between computers on a local network (LAN).                |
| RDP (Remote Desktop Protocol)                   | TCP port 3389      | Proprietary GUI remote access protocol developed by Microsoft and is used to remotely authenticate and interact with a Windows system.                   |
| WinRM (Windows Remote Management Protocol)      | TCP ports 5986/443 | Windows remote management protocol that can be used to facilitate remote access with Windows systems.                                                    |

#eJPT #cybersecurity 