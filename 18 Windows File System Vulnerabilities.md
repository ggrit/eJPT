# 18 Windows File System Vulnerabilities

# Alternate Data Streams

- Alternate Data Streams (ADS) is an NTFS (New Technology File System) file attribute and was designed to provide compatibility with the MacOS HFS (Hierarchical File System).
- Any file created on an NTFS formatted drive will have two different forks/streams:
	- Data stream - Default stream that contains the data of the file.
	- Resource stream - Typically contains the metadata of the file.
- Attackers can use ADS to hide malicious code or executables in legitimate files in order to evade detection.
- This can be done by storing the malicious code or executables in the file attribute resource stream (metadata) of a legitimate file.
- This technique is usually used to evade basic signature based AVs and static scanning tools.

## Demo

```shell
notepad test.txt:secret.txt

C:\Temp>type payload.exe > windowslog.txt:winpeas.exe
C:\Tempo>start windowslog.txt:winpeas.txt
C:\Windows\System32>mklink wupdate.exe C:\Temp\windowslog.txt:winpeas.exe
C:\Windows\System32>wupdate
```

#eJPT #cybersecurity 