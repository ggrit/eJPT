# 24 Metasploit Framework Overview

# Introduction To The Metasploit Framework

- Automate every stage of the pentest life cycle
- Largest database of public, tested exploits
- Modular, allowing for new functionality to be implemented with ease

## Essential Terminology

- **Interface**
	- Methods of interacting with the Metasploit Framework
- **Module**
	- Pieces of code that perform a particular task, an example of a module is an exploit
- **Vulnerability**
	- Weakness or flaw in a computer system or network that can be exploited
- **Exploit**
	- Piece of code/module that is used to take advantage a vulnerability within a system, service or application
- **Payload**
	- Piece of code delivered to the target system by an exploit with the objective of executing arbitrary commands or providing remote access to an attacker
- **Listener**
	- A utility that listens for an incoming connection from a target 

## Metasploit Framework Interfaces

- Metasploit Framework Console (MSFconsole)
	- All in one interface
- Metasploit Framework Command Line Interface (MSFcli)
	- Utility used to facilitate the creation of automation scripts that utilize Metasploit modules
	- It can be used to redirect output from other tools in to msfcli and vice versa
- Metasploit Community Edition
	- Web based GUI
- Armitage
	- Free Java based GUI 

# Metasploit Framework Architecture

![[Screenshot 2025-02-25 at 16.41.43.png]]

- **Module**
	- Piece of code that can be utilized by the MSF
- **MSF Libraries**
	- Facilitate the execution of modules without having to write the code necessary in order to execute them

## MSF Modules

- **Exploit**
	- A module that is used to take advantage of vulnerability and is typically paired with a payload
- **Payload**
	- Code that is delivered by MSF and remotely executed on the target after successful exploitation
	- An example is a reverse shell that initiates a connection from the target system back to the attacker
- **Encoder**
	- Used to encode payloads in order to avoid AV detection
	- For example, shikata_ga_nai is used to encode Windows payloads
- **NOPS**
	- Used to ensure that payloads sizes are consistent and ensure the stability of a payload when executed
- **Auxiliary**
	- A module that is used to perform additional functionality like port scanning and enumeration

## MSF Payload Types

- **Non-Staged Payload**
	- Payload that is sent to the target system as is along with the exploit
- **Staged Payload**
	- A staged payload is sent to the target in two parts
		- The first part (**stager**) contains a payload that is used to **establish a reverse connection** back to the attacker, download the second part of the payload (**stage**) and execute it

## Stagers & Stages

- **Stagers**
	- Typically used to **establish a stable communication channel between the attacker and target**, after which a *stage* payload is downloaded and executed on the target system
- **Stages**
	- Payload components that are downloaded by the stager

## Meterpreter Payload

- The **Meterpreter** (Meta-Interpreter) payload is an advanced multi-functional payload that is **executed in memory** on the target system making it difficult to detect
- It communicates over a stager socker and provides an attacker with an **interactive command interpreter** on the target system that facilitates the execution of system commands, file system navigation, keylogging and much more

## MSF Module Locations

- MSF stores modules under the following directory on Linux systems:
	- `/usr/share/metasploit-framework/modules`
- User specified/custom modules are stored under
	- `~/.ms4/modules`

# Penetration Testing with the Metasploit Framework

- Automate various tasks that fall under the penetration testing life cycle
- Can adopt the PTES (Penetration Testing Execution Standard) as a roadmap

## Penetration Testing Execution Standard

- https://github.com/penetration-testing-execution-standard/ptes

## Penetration Testing Phases

1. Information Gathering
2. Enumeration
3. Exploitation
4. Post Exploitation
	1. Privilege Escalation
	2. Maintaining Persistent Access
	3. Clearing Tracks

## Penetration Testing with MSF

| **Penetration Testing Phase**       | **Metasploit Framework Implementation** |
| ----------------------------------- | --------------------------------------- |
| Information Gathering & Enumeration | Auxiliary Modules                       |
| Vulnerability Scanning              | Auxiliary Modules - Nessus              |
| Exploitation                        | Exploit Modules & Payloads              |
| Post Exploitation                   | Meterpreter                             |
| Privilege Escalation                | Post Exploitation Modules - Meterpreter |
| Maintaining Persistent Access       | Post Exploitation & Persistence Modules |

#eJPT #cybersecurity 