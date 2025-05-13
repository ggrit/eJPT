# 60 Clearing Your Tracks

# Clearing Your Tracks on Windows

- The exploitation and post-exploitation phases of a penetration test involves actively engaging with target systems and the data that is stored on these systems.
- As a result, you may be required to clean/undo any changes you have made to the target systems you have compromised based on the guidelines specified in the rules of engagement.
- If you have transferred any files to the target systems you have compromised, keep track of where they have been saved so that you can remove them when done.
- A good practice is to store all your scripts, exploits and binaries in the C:/Temp directory on Windows and the /tmp directory on Linux.

- It is also important to consider the exploitation framework you are using, an example of this is MSF, which is notorious for generating and storing artifacts on the target system when using exploit or post modules.
- Some well designed MSF modules provide you with instructions and resource scripts that provide you with information regarding where the artifacts are store and how they can be removed.
- In the context of Windows, a typical post-exploitation techniques pertinent to clearing your tracks is to delete the Windows Event Log. This is something that should be avoided during penetration test as the Windows Event Log stores a lot of data that is important to the client you are performing the penetration test for. 

### DEMO

```shell
# Use a Temp dir!
mkdir Temp

# Some MSF have nice resource script to automate clearing
Cleanup Meterpreter RC File
# To use it
meterpreter: resource <rc-file>

# Wipe Windows Event Log
meterpreter: clearev
```


# Clearing Your Tracks on Linux

### DEMO

```shell
# Use a tmp dir! (When system reboot all files are deleted)
mkdir tmp

# Clean history file! 
.bash_history
history -c # Clean all history

# Some MSF have nice resource script to automate clearing
Cleanup Meterpreter RC File
# To use it
meterpreter: resource <rc-file>
```


#cybersecurity #eJPT 