# 27 Enumeration

# Port Scanning with Auxiliary Modules

## Auxiliary Modules

- Auxiliary modules are used to perform functionality like scanning, discovery and fuzzing
- We can use auxiliary modules to perform both TCP & UDP port scanning as well as enumerating information from services like FTP, SSH, HTTP, etc.
- Auxiliary modules can be used during the information gathering phase of a penetration test as well as the post exploitation phase
- We can also use auxiliary modules to discover hosts and perform port scanning on a different subnet after we have obtained initial access on a target system 

### DEMO

```shell
service postgresql start
msfconsole
msf6: db_status
msf6: workspace -a <name>
msf6: search portscan
msf6: curl <ip> 
msf6: search xoda
msf6: exploit(unix/webapp/xoda_file_upload) # Just to exploit this particular case
msf6: meterpreter
meterpreter: sysinfo
meterpreter: shell
/bin/bash -i
bash: ifconfig # Then exit
meterpreter: run autoroute -s <ip-different-subnet> # Add route of different subnet
meterpreter: background
msf6: sessions
msf6: search portscan
msf6: set rhosts <ip-target2>
msf6: auxiliary(scanner/discovery/udp_sweep) # UDP scan
```

# FTP Enumeration

- FTP (File Transfer Protocol) is a protocol that uses TCP port 21 and is used to facilitate file sharing between a server and client/clients
- It is also frequently used as a means of transferring files to and from the directory of a web server
- We can use multiple auxiliary modules to enumerate information as well as perform brute-force attacks on targets running an FTP server
- FTP authentication utilizes a username and password combination, however, in some cases an improperly configured FTP server can be logged into anonymously 

### DEMO

```shell
search type:auxliary name:ftp
msf6: auxiliary(scanner/ftp/ftp_version)
msf6: auxiliary(scanner/ftp/ftp_login) # Brute force
msf6: ftp <ip> # Connect to FTP
msf6: auxiliary(scanner/ftp/anonymous) # Check anon log-in
```

# SMB Enumeration

- SMB (Server Message Block) is a network file sharing protocol that is used to facilitate the sharing of files and peripherals between computer on a local network (LAN)
- SMB uses port 445 (TCP). However, originally, SMB ran on top of NetBIOS using port 139
- SAMBA is the Linux implementation of SMB, and allows Windows systems to access Linux shares and devices
- We can utilize auxiliary modules to enumerate SMB version, shares, users, and perform a brute-force attack in order to identify users and passwords

### DEMO

```shell
msf6: auxiliary(scanner/smb/smb_version)
msf6: auxiliary(scanner/smb/smb_enumusers)
msf6: auxiliary(scanner/smb/smb_enumshares)
msf6: auxiliary(scanner/smb/smb_login) # Brute force

smbclient -L \\\\<ip-target>\\ -U admin # List shares
smbclient \\\\<ip-target>\\<share> -U admin # Login in share
```


# Web Server Enumeration

- A web server is software that is used to serve website data on the web
- Web servers utilize HTTP (Hypertext Transfer Protocol) to facilitate the communication between clients and the web server
- HTTP is an application layer protocol that utilizes TCP port 80 for communication
- We can utilize auxiliary modules to enumerate the web server version, HTTP header, brute-force directories and much more
- Examples of popular web servers are: Apache, Nginx and Microsoft IIS 

### DEMO

```shell
msf6: auxialiary(scanner/http/http_version)
msf6: auxialiary(scanner/http/http_header)
msf6: auxialiary(scanner/http/robots_txt)
msf6: auxialiary(scanner/http/dir_scanner)
msf6: auxialiary(scanner/http/files_dir) # Enum files
msf6: auxialiary(scanner/http/http_login)
msf6: auxialiary(scanner/http/apache_userdir_enum)

curl http://<url>/ # Download 
```


# MySQL Enumeration

- MySQL is an open-source relational database management system based on SQL (Structured Query Language)
- It is typically used to store records, customer data, and is most commonly deployed to store web application data
- MySQL utilizes TCP port 3306 by default, however, like any service it can be hosted on any open TCP port
- We can utilize auxiliary modules to enumerate the version of MySQL, perform brute.force attacks to identify passwords, execute SQL queries and much more

### DEMO

```shell
msf6: auxiliary(scanner/mysql/mysql_version)
msf6: auxiliary(scanner/mysql/mysql_login)
msf6: auxiliary(admin/mysql/mysql_enum) # Require access with credentials
msf6: auxiliary(admin/mysql/mysql_sql) # Require access with credentials, send sql query
msf6: auxiliary(scanner/mysql/mysql_schemadump)
msf6: hosts, services, loot, creds # Single commands to show what we already find 

mysql -h <ip> -u <user> -p # Login mysql
```


# SSH Enumeration

- SSH (Secure Shell) is a remote administration protocol that offers encryption and is the successor to Telnet
- It is typically used for remote access to servers and systems
- SSH uses TCP port 22 by default, however, like other services, it can be configured to use any other open TCP port
- We can utilize auxiliary modules to enumerate the version of SSH running on the target as well as perform brute-force attacks to identify passwords that consequently provide us remote access to a target

```shell
msf6: auxiliary(scanner/ssh/ssh_version)
msf6: auxiliary(scanner/ssh/ssh_login)
msf6: sessions
msf6: auxiliary(scanner/ssh/ssh_enumusers)
```


# SMTP Enumeration

- SMTP (Simple Mail Transfer Protocol) is a communication protocol that is used for the transmission of email
- SMTP uses TCP port 25 by default. It is can also be configured to run on TCP port 465 and 587
- We can utilize auxiliary modules to enumerate the version of SMTP as well as user accounts on the target system

```shell
msf6: auxiliary(scanner/smtp/smtp_version)
msf6: auxiliary(scanner/smtp/smtp_enum)
```

#eJPT #cybersecurity 