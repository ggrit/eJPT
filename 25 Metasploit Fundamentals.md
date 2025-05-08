# 25 Metasploit Fundamentals

# Installing & Configuring The Metasploit Framework

- The MSF is distributed by Rapid7
- MSF and its required dependencies come pre-packaged with Kali Linux which saves us from the tedious process of installing MSF manually

## The Metasploit Framework Database 

- The Metasploit Framework Database (msfdb) is an integral part of the Metasploit Framework and is used to keep track of all you assessments, host data scans etc.
- The Metasploit Framework uses PostgreSQL as the primary database server, as a result, we will also need to ensure that the PostgreSQL database service is running and configured correctly
- Also facilitates the importation and storage of scan results from various third party tools like nMap and Nessus

## Installation Steps

- Update our repository and upgrade our Metasploit Framework to the latest version
- Start and enable the PostgreSQL database service
- Initialize the Metasploit Framework Database (msfdb)
- Launch MSFconsole 

# MSFconsole Fundamentals

- Metasploit Framework Console (MSFconsole) is an easy-to-use all in one interface that provides you with access to all the functionality of the Metasploit Framework

## What you need to know

1. How to search for module
2. How to select modules
3. How to configure module options & variables
4. How to search for payloads
5. Managing sessions
6. Additional functionality
7. Saving your configuration

## MSF Module Variables

- MSF modules will typically require information like the target & host IP address and port in order to initiate a remote exploit/connection
- These options can be configured through the use of MSF variables
- MSFconsole allows you to set both local variables values or global variables values

| Variable | Purpose                                                                                                  |
| -------- | -------------------------------------------------------------------------------------------------------- |
| LHOST    | Used to store the UP address of the attacker's system                                                    |
| LPORT    | Used to store the port number on the attacker's system that will be used to receive a reverse connection |
| RHOST    | Used to store the IP address of the target system/server                                                 |
| RHOSTS   | Used to specify the IP addresses of multiple target systems or network ranges                            |
| RPORT    | Stores the port number that we are targeting on the target system                                        |

### DEMO

```shell
help # Command available
version
show -h # Show the parameters for show command
search portscan
show options # Module options
back # Exit from module
sessions # Show active sessions
connect # Banner grabbing, similar to interacting via netcat
```

# Creating & Managing Workspaces

## MSF Workspaces

- Workspaces allow you to keep track of all your hosts, scans, and activities and are extremely useful when conducting penetration tests as they allow you to sort and organize your data based on the target or organization
- MSFconsole provides you with the ability to create, manage and switch between multiple workspaces depending on you requirements

### DEMO

```shell
db_status
workspace -h
hosts # Show host used in current workspace
```

#eJPT #cybersecurity 