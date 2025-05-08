# 47 AV Evasion & Obfuscation

# AV Evasion with Shellter

## Defense Evasion

- Defense Evasion consists of techniques that adversaries use to avoid detection throughout their compromise. Techniques used for defense evasion include uninstalling/disabling security software or obfuscating/encrypting data and scripts. Adversaries also leverage and abuse trusted processes to hide and masquerade their malware. - MITRE

## AV Detection Methods

AV software will typically utilize signature, heuristic and behaviour based detection.

1. **Signature based detection**
	- An AV signature is a unique sequence of bytes that uniquely identifies malware. As a result, you will have to ensure that your obfuscated exploit or payload doesn't match any known signature in the AV database.

		We can bypass signature-based detection by modifying the malware's byte sequence, therefore changing the signature. 

2. **Heuristic-based detection**
	- Relies on rules or decisions to determine whether a binary is malicious. It also looks for specific patterns within the code or program calls.

3. **Behavior based detection**
	- Relies on identifying malware by monitoring it's behavior. (Used for newer strains of malware).

## AV Evasion Techniques

#### On-disk Evasion Techniques

- **Obfuscation**
	- Obfuscation refers to the process of concealing something important, valuable, or critical. Obfuscation reorganizes code in order to make it harder to analyze or RE. 
- **Encoding**
	- Encoding data is a process involving changing data into a new format using a scheme. Encoding is a reversible process; data can be encoded to a new format and decoded to its original format.
- **Packing**
	- Generate executable with new binary structure with a smaller size and therefore provides the payload with a new signature.
- **Crypters**
	- Encrypts code or payloads and decrypts the encrypted code in memory. The decryption key/function is usually stored in a stub. 

#### In-Memory Evasion Techniques

- Focuses on manipulation of memory and does not write files to disk.
- Injects payload into a process by leveraging various Windows APIs.
- Payload is then executed in memory in a separate thread.


### DEMO

```shell
shellter # Official Kali repo package, 32-bit applications only 
# To install 32-bit package and execute it 
sudo dpkg --add-architecture i386
sudo apt-get install wine32 # Execute .exe 32-bit

# To execute .exe file on Linux
sudo wine <file>.exe

# Find some Windows binaries on Linux
/usr/share/windows-binaries

# Copy an original binary in another directory
# Shellter will creare a backup of original executable under
/usr/share/windows-resources/shellter/Shellter_Backups

# Use shellter
sudo wine shellter.exe
shellter: # First, select operation mode
shellter: PE Target: <path-to-exe> # Portable executable target (ligitimate executable)
shellter: Stelth Mode? # Want to exe to function as intended (usually, y)
shellter: Listed payload or custom? # Select the payload 
# The malicious exe overwrite the selected one 
```


# Obfuscating PowerShell Code

## Obfuscation

- Obfuscation refers to the process of concealing something important, valuable, or critical. Obfuscation reorganizes code in order to make it harder to analyze or RE.
- As a penetration tester, you will find yourself working with PowerShell code frequently. Most AV solutions will immediately flag malicious PowerShell code, as a result, you must be able to obfuscate/encode your PowerShell code and scripts in order to avoid detection.

## Invoke-Obfuscation

- Invoke-Obfuscation is an open source PowerShell v2.0+ compatible PowerShell command and script obfuscator.

https://github.com/danielbohannon/Invoke-Obfuscation


### DEMO

```shell
# Clone repo
git clone https://github.com/danielbohannon/Invoke-Obfuscation
# Install dependencies
sudo apt-get install powershell -y
# Launch PowerShell
pwsh 
cd Invoke-Obfuscation
dir
Import-Module <name-of-module>.psd1
cd .. # Get out of Invoke-Obduscation dir
Invoke-Obfuscation # Launch the tool 

# How to use
# Copy in a file Reverse Shell PowerShell code, can find online
# Delete from the code "powershell commands..." and the quotation marks ""
# Change the IP and port
# Save as <name>.ps1

# Example 1
Invoke-Obfuscation: SET SCRIPTPATH <path-to-powershell-script>.ps1 # Previously created
# Now have obfuscate option
Invoke-Obfuscation: ENCODING # Then it provides various options
Invoke-Obfuscation: 1 # Select the option
# It generates the code, now have to copy in new file and get to the target 

# Another example
Invoke-Obfuscation: SET SCRIPTPATH <path-to-powershell-script>.ps1 # Previously created
Invoke-Obfuscation: AST # Power
Invoke-Obfuscation: ALL # All obfuscation techniques
Invoke-Obfuscation: 1
# Get the new obfuscated code
```


#cybersecurity #eJPT 