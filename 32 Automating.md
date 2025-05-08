# 32 Automating

# Automating Metasploit with Resource Scripts

- Metasploit resource scripts are a great feature of MSF that allow you to automate repetitive tasks and commands
- They operate similarly to batch scripts, whereby, you can specify a set of Msfconsole commands that you want to execute sequentially
- You can then load the script with Msfconsole and automate the execution of the commands you specified in the resource script
- We can use resource scripts to automate various tasks like setting up multi handlers as well as loading and executing payloads

### DEMO

```shell
msfconsole -r <path/to/script> # Lauch msfconsole with script
msf6: resource <path/to/script> # Lanch script in msfconsole 
msf6: makerc <path/to/save> # Create .rc file with commands used 

# Just write a file with commands used into msfconsole .rc
```

#eJPT #cybersecurity 