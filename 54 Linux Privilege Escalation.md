# 54 Linux Privilege Escalation

# Linux Privilege Escalation - Weak Permissions

## LinEnum

- **LinEnum**
	- A simple bash script that automates common Linux local enumeration checks in addition to identifying privilege escalation vulnerabilities.
	- https://github.com/rebootuser/LinEnum

### DEMO

```shell
# Search for files that every users can write or make changes 
find / -not -type l -perm -o+w
# Found: /etc/shadow (really bad configuration)

# Generate hashed password 
openssl passwd -1 -salt abc <new-pass>
```


# Linux Privilege Escalation - SUDO Privileges

### DEMO

```shell
# Which binary can i run with sudo permissions
sudo -l

# Super 
https://gtfobins.github.io
```


#cybersecurity #eJPT 