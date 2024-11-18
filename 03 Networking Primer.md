# 03 Network primer

## Networking Fundamentals

**host** = any system that’s running an operating system that can communicate on a network

| **#** | **OSI LAYER**          | **FUNCTION**                                                                                                                                                                                | **EXAMPLES**                            |
| ----- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| **7** | **APPLICATION LAYER**  | Provides network services directly to end-users or applications.                                                                                                                            | HTTP, FTP, IRC, SSH, DNS                |
| **6** | **PRESENTATION LAYER** | Translates data between the application layer and lower layers. Responsible for data format translation, encryption, and compression to ensure that data is presented in a readable format. | SSL/TLS, JPEG, GIF, SSH, IMAP           |
| **5** | **SESSION LAYER**      | Manages sessions or connections between applications. Handles synchronization, dialog control, and token management. (Interhost communication)                                              | APIs, NetBIOS, RPC<br>                  |
| **4** | **TRANSPORT LAYER**    | Ensures end-to-end communication and provides flow control.                                                                                                                                 | TCP, UDP                                |
| **3** | **NETWORK LAYER**      | Responsible for logical addressing and routing.(Logical Addressing)                                                                                                                         | IP, ICMP, IPSec                         |
| **2** | **DATA LINK LAYER**    | Manages access to the physical medium and provides error detection. Responsible for framing, addressing, and error checking of data frames. (Physical addressing)                           | Ethernet, PPP, Switches                 |
| **1** | **PHYSICAL LAYER**     | Deals with the physical connection between devices.                                                                                                                                         | USB, Ethernet Cables, Coax, Fiber, Hubs |

## Network Layer (3)
Logical addressing, routing, and the fragmentation and reassembly of data packets.
Standardized way to identify and locate hosts.

- Determine the **optimal path for data**
- Allows the creation of a cohesive internetwork
- Responsible for **logical addressing, routing, and forwarding data packets**

### Protocols

**Internet Protocol (IP)**
- IPv4 (Internet Protocol version 4): 32-bit addresses
- IPv6 (Internet Protocol version 6): 128-bit addresses    

**Internet Control Message Protocol (ICMP)**
- Used for error reporting and diagnostics. ICMP messages include ping (echo request and echo reply), traceroute and various error messages

#### Internet Protocol (IP)

##### Functionality

- **Logical Addressing**
    - IP addresses serve as logical addresses assigned to network interfaces. These addresses uniquely identify each device on a network.
    - IP addresses are **hierarchical and structured based on network classes, subnets, and CIDR** (Classless Inter-Domain Routing) notation.
- **Packet Structure**
    - IP organizes data into packets for transmission across networks. Each packet consists of a header and payload.
    - The **header** contains essential information, including the source and destination **IP addresses**, **version number**, time-to-live (**TTL**), and **protocol type**.
- **Fragmentation and Reassembly (MTU)**
    - IP allows for the fragmentation of large packets into smaller fragments when
        traversing networks with varying Maximum Transmission Unit (MTU) sizes.
    - The receiving host reassembles these fragments to reconstruct the original packet.
- **IP Addressing Types**
    - IP addresses can be classified into three types: **unicast** (one-to-one communication), **broadcast** (one-to-all communication within a subnet), and **multicast** (one-to-many communication to a selected group of devices).
- **Subnetting**
    - Subnetting is a technique that divides a large IP network into smaller, more manageable sub-networks. It enhances network efficiency and security.
- **Internet Control Message Protocol (ICMP)**
    - ICMP is closely associated with IP and is **used for error reporting and diagnostics**. Common ICMP messages include **echo request and echo reply**, which are used in the ping utility.
- **Dynamic Host Configuration Protocol (DHCP)**
    - DHCP is often used in conjunction with IP to dynamically assign IP addresses to devices on a network, simplifying the process of network configuration. 

##### Header format

| **Field**                            | **Purpose**                                                                                                                                                                                                                                                                                                |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Version (4 bits)**                 | Indicates the version of the IP protocol being used. For IPv4, the value is 4.                                                                                                                                                                                                                             |
| **Header Length (4 bits)**           | Specifies the length of the IPv4 header in 32-bit words.  <br>The minimum value is 5, indicating a 20-byte header, and the maximum is 15, indicating a 60-byte header.                                                                                                                                     |
| **Type of Service (ToS, 8 bits)**    | Originally designed for specifying the quality of service, it includes fields such as Differentiated Services Code Point (DSCP) and Explicit Congestion Notification (ECN) to manage packet priority and congestion control.                                                                               |
| **Total Length (16 bits)**           | Represents the total size of the IP packet, including both the header and the payload (data). The maximum size is 65,535 bytes.                                                                                                                                                                            |
| **Identification (16 bits)**         | Used for reassembling fragmented packets. Each fragment of a packet is assigned the same identification value.                                                                                                                                                                                             |
| **Flags (3 bits)**                   | Includes three flags related to packet fragmentation:  <br>Reserved (bit 0): Always set to 0.  <br>Don't Fragment (DF, bit 1): If set to 1, indicates that the packet should not be fragmented.  <br>More Fragments (MF, bit 2): If set to 1, indicates that more fragments follow in a fragmented packet. |
| **Time-to-Live (TTL, 8 bits)**       | Represents the maximum number of hops (routers) a packet can traverse before being discarded. It is decremented by one at each hop.                                                                                                                                                                        |
| **Protocol (8 bits)**                | Identifies the higher-layer protocol that will receive the packet after IP processing. Common values include 6 for TCP, 17 for UDP, and 1 for ICMP.                                                                                                                                                        |
| **Source IP Address (32 bits)**      | Specifies the IPv4 address of the sender (source) of the packet.                                                                                                                                                                                                                                           |
| **Destination IP Address (32 bits)** | Specifies the IPv4 address of the intended recipient (destination) of the packet.                                                                                                                                                                                                                          |
![[Screenshot 2024-09-02 at 09.32.49.png]]

##### Reserved
For example, some reserved intervals are:
- 0.0.0.0 – 0.255.255.255 representing "this" network
- 127.0.0.0 – 127.255.255.255 representing the local host (e.g., your computer)
- 192.168.0.0 – 192.168.255.255 is reserved for private networks

Details about the special use of IPv4 addresses in [RFC5735](https://datatracker.ietf.org/doc/html/rfc5735).

## Transport Layer (4)

Facilitating communication between two devices across a network.

Ensures reliable, end-to-end communication, handling tasks such as error detection, flow control, and segmentation of data into smaller units.

The Transport Layer, is responsible for providing end-to-end communication and ensuring the reliable and ordered delivery of data between two devices on a network.

### Protocols
- **TCP** (Transmission Control Protocol): **Connection-oriented** protocol providing reliable and ordered delivery of data.
- **UDP** (User Datagram Protocol): **Connectionless** protocol that is faster but provides no guarantees regarding the order or reliability of data delivery.

#### TCP
Ensures that data sent from one application on a device is received accurately and in the correct order by another application on a different device.

- **Connection-Oriented**
    - TCP establishes a connection between the sender and receiver before any data is exchanged. This connection is a virtual circuit that ensures reliable and ordered data transfer.

- **Reliability**
    - TCP guarantees reliable delivery of data. It achieves this through mechanisms such as acknowledgments (ACK) and retransmission of lost or corrupted packets. If a segment of data is not acknowledged, TCP automatically resends the segment.

- **Ordered Data Transfer**
    - TCP ensures that data is delivered in the correct order. If segments of data arrive out of order, TCP reorders them before passing them to the higher-layer application.

The **TCP three-way handshake** is a process used to establish a reliable connection between two devices before they begin data transmission.
It involves a series of three messages exchanged between the sender (client) and the receiver (server).

- **SYN (Synchronize)**: The process begins with the client sending a TCP segment with the SYN (Synchronize) flag set. This initial message indicates the client's intention to establish a connection and includes an initial sequence number (ISN), which is a randomly chosen value.

- **SYN-ACK (Synchronize-Acknowledge)**: Upon receiving the SYN segment, the server responds with a TCP segment that has both the SYN and ACK (Acknowledge) flags set. The acknowledgment (ACK) number is set to one more than the initial sequence number received in the client's SYN segment. The server also generates its own initial sequence number.

- **ACK (Acknowledge)**: Finally, the client acknowledges the server's response by sending a TCP segment with the ACK flag set. The acknowledgment number is set to one more than the server's initial sequence number.

At this point, the connection is established, and both devices can begin transmitting data.

After the three-way handshake is complete, the devices can exchange data in both directions. The acknowledgment numbers in subsequent segments are used to confirm the receipt of data and to manage the flow of information.

![[Screenshot 2024-09-02 at 13.27.37.png]]

##### Control Flags
TCP (Transmission Control Protocol) uses a set of control flags to manage various aspects of the communication process.
These flags are included in the TCP header and control different features during the establishment, maintenance, and termination of a TCP connection.

- Establishing a Connection:
    - SYN (Set): Initiates a connection request.
    - ACK (Clear): No acknowledgment yet.
    - FIN (Clear): No termination request.

- Establishing a Connection (Response):
    - SYN (Set): Acknowledges the connection request.
    - ACK (Set): Acknowledges the received data.
    - FIN (Clear): No termination request.

- Terminating a Connection:
    - SYN (Clear): No connection request.
    - ACK (Set): Acknowledges the received data.
    - FIN (Set): Initiates connection termination.

##### Port Range
TCP (Transmission Control Protocol) uses port numbers to distinguish between different services or applications on a device.
Port numbers are 16-bit unsigned integers, and they are divided into three ranges.
The maximum port number in the TCP/IP protocol suite is 65,535.

**Well-Known Ports (0-1023)**: Port numbers from 0 to 1023 are reserved for well-known services and protocols. These are standardized by the Internet Assigned Numbers Authority (IANA). 

Examples include:
- 80: HTTP (Hypertext Transfer Protocol)
- 443: HTTPS (HTTP Secure)
- 21: FTP (File Transfer Protocol)
- 22: SSH (Secure Shell)
- 25: SMTP (Simple Mail Transfer Protocol)
- 110: POP3 (Post Office Protocol version 3)

**Registered Ports (1024-49151)**: Port numbers from 1024 to 49151 are registered for specific services or applications. These are typically assigned by the IANA to software vendors or developers for their applications. While they are not standardized, they are often used for well-known services. 

Example include:
- 3389: Remote Desktop Protocol (RDP)
- 3306: MySQL Database
- 8080: HTTP alternative port
- 27017: MongoDB Database

#### UDP

Connectionless and lightweight transport layer protocol that provides a simple and minimalistic way to transmit data between devices on a network.

It does not establish a connection before sending data and does not provide the same level of reliability and ordering guarantees. Instead, it focuses on simplicity and efficiency, making it suitable for certain types of applications.

- **Connectionless:** meaning that it does not establish a connection before sending data. Each UDP packet (datagram) is treated independently, and there is no persistent state maintained between sender and receiver.
- **Unreliable:** it does not provide reliable delivery of data. It does not guarantee that packets will be delivered, and there is no mechanism for retransmission of lost packets. This lack of reliability makes UDP faster but less suitable for applications that require guaranteed delivery.
- **Used for Real-Time Applications:** it’s commonly used in real-time applications where low latency is crucial, such as audio and video streaming, online gaming, and voice-over-IP (VoIP) communication.
- **Simple and Stateless:** UDP is a stateless protocol, meaning that it does not maintain any state information about the communication.

Each UDP packet is independent of previous or future packets.

| **Feature**  | **TCP**                                                                        | **UDP**                                           |
| ------------ | ------------------------------------------------------------------------------ | ------------------------------------------------- |
| Connection   | 3-Way Handshake                                                                | Connectionless                                    |
| Reliability  | Reliable, guarantees delivery and order of packets and supports retransmission | Unreliable, no guaranteed delivery of packets     |
| Header Size  | Larger header size                                                             | Smaller header size, lower overhead               |
| Applications | HTTP, Email                                                                    | VOIP, streaming, gaming                           |
| Examples     | HTTP, HTTPS, FTP, Telnet, SMTP (email).                                        | DNS, DHCP, SNMP, VoIP (e.g., SIP), online gaming. |

#eJPT #cybersecurity 