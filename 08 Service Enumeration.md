# 08 Service Enumeration

## FTP Enumeration
File sharing
TCP 21
```bash
service postgresql start
msfconsole
msf6: workspace -a FTP_ENUM
msf6: search portscan
msf6: use 5
msf6: show options
msf6: set RHOSTS
msf6: run
msf6: back
msf6: search type:auxiliary name:ftp
```

## SMB Enumeration
LAN file sharing, TCP 445 Ran on top of NetBIOS TCP 139
SAMBA is the Linux implementation
```bash
msf6: search type:auxiliary name:SMB
msf6: use 38
msf6: info (module)
msf6: run
msf6: set ShowFiles true
smbclient -L \\\\<IP>\\ -U admin
smbclient \\\\<IP>\\<share> -U admin
```

## Web Server Enumeration
Serve website data on the web via HTTP, TCP 80 or 443 HTTPs
Apache, Nginx and Microsoft IIS
```bash
msf6: setg RHOSTS <IP> (set variable for all module)
msf6: search type:auxiliary name:http
msf6: search http_header
msf6: search robots_txt
curl <IP> (download source)
msf6: search dir_scanner
msf6: search files_dir
msf6: search http_login
msf6: search apache_userdir_enum
```

## MySQL Enumeration
Relational database management
TCP 3306 (usually)
```bash
msf6: setg RHOSTS <IP> (set variable for all module)
msf6: search type:auxiliary name:mysql
msf6: search mysql_login
msf6: set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
msf6: search mysql_enum
msf6: search mysql_sql
msf6: set SQL show databases;
msf6: set SQL use videos;
msf6: search mysql_schema
msf6: hosts
msf6: services
msf6: loot
msf6: creds
mysql -h <IP> -u root -p
MySQL: show databases;
MySQL: use videos;
MySQL: show tables;
```

## SSH Enumeration
Remote access to servers and systems
TCP 22
```bash
msf6: search ssh_version
msf6: search ssh_login
sessions
sessions 1
/bin/bash -i
```

## SMTP Enumeration
Email
TCP 25 (default) also 465 and 587
```bash
msf6: search smtp_version
msf6: search smtp_enum
```

#eJPT #cybersecurity 