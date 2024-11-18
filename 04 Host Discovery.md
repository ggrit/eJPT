# 04 Host Discovery

## Network Mapping
Discovering hosts on a network, performing port scanning and enumeration.
Gather information about the network's layout, understand its architecture, and identify potential entry points.

### Objectives
- Live Hosts
- Open Ports and Services
- Network Topology Mapping
- Operating System Fingerprinting
- Service Version Detection
- Identifying Filtering and Security Measures

## nMap
Nmap offers a range of features and functionalities that make it a valuable tool in various network security contexts:
- Host Discovery
- Port Scanning
- Service Version Detection
- Operating System Fingerprinting

## Hosts Discovery Techniques
Identify live hosts on a network before further exploration and vulnerability assessment.

- **Ping Sweeps (ICMP Echo Requests)**: Sending ICMP Echo Requests (ping).
- **ARP Scanning**: Using Address Resolution Protocol requests to identify hosts on a _local network_. ARP scanning is effective in discovering hosts within the same broadcast domain.
- **TCP SYN Ping (Half-Open Scan)**: Sending TCP SYN packets to a specific port (often port 80) to check if a host is alive. If the host is alive, it responds with a TCP SYN-ACK. This technique is _stealthier_ than ICMP ping.
- **UDP Ping**: Sending UDP packets to a specific port to check if a host is alive. This can be effective for hosts that do not respond to ICMP or TCP probes.
- **TCP ACK Ping**: Sending TCP ACK packets to a specific port to check if a host is alive. This technique expects no response, but if a _TCP RST (reset) is received_, it indicates that the host is alive.
- **SYN-ACK Ping** (Sends SYN-ACK packets): Sending TCP SYN-ACK packets to a specific port to check if a host is alive. If a _TCP RST is received_, it indicates that the host is alive.

The effectiveness of a host discovery technique can be influenced by the specific characteristics of the target network, and the security controls in place.

- Here are a few considerations:
    - **ICMP Ping**:
        - Pros: ICMP ping is a widely supported and quick method for identifying live hosts.
        - Cons: Some hosts or firewalls may be configured to block ICMP traffic, limiting its effectiveness. ICMP ping can also be easily detected.
    - **TCP SYN Ping**:
        - Pros: TCP SYN ping is stealthier than ICMP and may bypass firewalls that allow outbound connections.
        - Cons: Some hosts may not respond to TCP SYN requests, and the results can be affected by firewalls and security devices.

## Ping Sweeps
Network scanning technique used to discover live hosts (computers, servers, or other devices) within a specific IP address range on a network.
The basic idea is to send a series of ICMP Echo Request (ping) messages to a range of IP addresses and observe the responses to determine which addresses are active or reachable.

Ping command: designed to check if a host is alive/reachable.

- Ping sweeps work by sending one or more specially crafted ICMP packets (Type 8 - echo request) to a host.
- If the destination host replies with an ICMP echo reply (Type 0) packet, then the host is alive/online.
- In the context of ICMP (Internet Control Message Protocol), the ICMP Echo Request and Echo Reply messages are used for the purpose of ping. These messages have specific ICMP type and code values associated with them.

#### ICMP Echo Request
- Type: 8
- Code: 0

#### ICMP Echo Reply
- Type: 0
- Code: 0


The "Type" field in the ICMP header indicates the purpose or function of the ICMP message, and the "Code" field provides additional information or context related to the message type.

In the case of ICMP Echo Request and Echo Reply, the Type value 8 represents Echo Request, and the Type value 0 represents Echo Reply.

So, when a device sends an ICMP Echo Request, it creates an ICMP packet with Type 8, Code 0.

When the destination device receives the Echo Request and responds with an Echo Reply, it creates an ICMP packet with Type 0, Code 0.

When the host is offline or not reachable, the ICMP Echo Request message sent by the ping utility will not receive a corresponding ICMP Echo Reply.

The absence of a response doesn't necessarily mean that the host is permanently offline; it could be due to various reasons, such as network congestion, temporary unavailability, or firewall settings that block ICMP traffic.

The ping utility provides a quick and simple way to check the reachability of a host, but it's important to interpret the results in the context of the network conditions and host configuration.

![[Screenshot 2024-09-02 at 20.00.12.png]]

```bash
fping (multiple target) ex. 12.34.56.78/24
```

## Host Discovery with nMap

```bash 
nmap -sn (No port scan)
nmap -PS (TPC SYN port 80 but can change)
nmap -PA (TPC ACK port 80 but can change)
nmap -PE (ICMP echo)
nmap -sn -v -T4
nmap -sn -PS21,22,25,80,445,3389,8080 -T4 (-PU137,138)
```

#eJPT #cybersecurity  