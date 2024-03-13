# Network Devices
## Hubs
Hubs are basic networking devices that function as multiport physical repeaters for connecting end-user workstations.  

- <b>Operation</b>: They rebroadcast incoming frames out of all other ports except the one it was received on.
- <b>Collision Domain</b>: Hubs do not segregate collision domains; all connected devices share the same bandwidth, leading to possible collisions when multiple devices transmit simultaneously.
- <b>Addressing</b>: No forwarding decisions are made based on MAC or IP addresses.
- <b>Collision Mitigation</b>: Uses Carrier Sense Multiple Access with Collision Detection (CSMA/CD) to manage collisions, necessitating devices to operate in half-duplex mode to avoid simultaneous transmission and reception.

## Bridges
Bridges are networking devices that connect endpoint devices, using MAC addresses to deliver frames.  

- <b>Operation</b>: <u>Records sender’s MAC address upon receiving a packet</u>; if recipient’s MAC is known, forwards directly; otherwise, floods packet to all ports except the arrival port.
- <b>Forwarding Database</b>: Maintains a database of MAC addresses of connected hosts to direct packets efficiently.
- <b>Collision Domains</b>: Increases the number of collision domains, with each port creating a separate collision domain.
- <b>Broadcast Domains</b>: Does not create separate broadcast domains; all connected devices remain in the same broadcast domain.

## Switches
Switches are networking devices providing connectivity to endpoint devices, capable of operating at both Layer 2 and Layer 3 of the OSI model. 

- <b>Layer 2 Operation</b>: Functions similarly to bridges, using MAC addresses for switching frames, and performs microsegmentation to create a dedicated network segment for each port, effectively increasing collision domains.
- <b>Layer 3 Operation</b>: Adds routing functionality, enabling direct communication between VLANs without needing an external router.
- <b>Content Addressable Memory (CAM) Table</b>: Utilizes a CAM table to store and associate MAC addresses with physical ports, facilitating efficient frame forwarding based on the destination MAC address.
- <b>Traffic Flow</b>: Improves traffic flow, reduces collisions, and enhances network performance by forwarding packets to the correct ports.
- <b>Broadcast Domains</b>: All devices connected to a Layer 2 switch reside in a single broadcast domain.
  - VLANs are used to separate multiple broadcast domains, requiring a Layer 3 device for inter-VLAN communication. 
  - Layer 3 Switches integrate routing to allow direct VLAN communication.  

### Switching Steps Example:
1. **Frame Reception**
   - The switch receives a frame on one of its ports.

2. **Update Switching Table**
   - Check if the source MAC address of the received frame exists in the switching table.
     - If not, add the source MAC address along with the receiving port to the switching table.

3. **Determine Frame Forwarding Path**
   - Check the switching table for the destination MAC address of the received frame.
     - If the destination MAC address is found, proceed to step 4.
     - If the destination MAC address is not found, proceed to step 5.

4. **Direct Frame to Specific Port**
   - Send the frame directly to the port associated with the destination MAC address.

5. **Flood Frame**
   - Flood the frame out of all ports, except the port from which the frame was received.
## Routers
Routers are devices used to forward packets between different computer networks, operating at Layer 3 of the OSI model.  
- **Broadcast Domains**: Create separate broadcast domains for connected devices, preventing broadcasts from being forwarded to other network segments.
- **Logical Addressing**: Makes forwarding decisions based on logical (IP) addresses, using a routing table for this purpose.
- **Routing Table**: Stored in TCAM (Ternary Content Addressable Memory) for efficient, high-speed data queries, supporting both exact and non-exact matching.
  - Exact Match: This is when the TCAM table finds an entry that exactly matches the query, such as a specific IP address.
  - Non-Exact (Wildcard) Match: TCAM supports non-exact or wildcard matches, allowing it to match entries based on patterns or portions of an address. This is useful for matching a range of IP addresses or subnet masks.
- **Path Decisions and Forwarding**: Routes packets to destination networks based on routing table entries. Drops packets and sends ICMP error messages if no route is found and no default route is configured.
- **Layer 3 Operations**: Supports ACLs, QoS policies, and other Layer 3 functionalities through the use of multiple TCAM tables.

## Servers
Servers are either hardware devices or software programs designed to provide specific services to client computers on a network.  

- **Functionality**: Offer a centralized platform for controlling, managing, and distributing various technologies including data files, applications, security policies, and network addresses.
- **Versatility**: Capable of performing a wide range of functions, serving different roles based on the services they provide (e.g., file servers, application servers, web servers).
## Endpoints
Endpoints, also known as hosts, are computing devices that access network services.  
- **Variety**: Can be PCs, PDAs, laptops, thin clients, or terminals.
- **Function**: Serve as the user interface for accessing data and network services.
## NGFWs and IPS Devices
### Firewalls
Devices that filter inbound packets from untrusted networks.  
- **Next-Generation Firewall**
  - Cisco Adaptive Security Appliances (ASAs) offer advanced functionalities including firewall, VPN, intrusion prevention, and content security services.
### Intrusion Prevention Systems (IPS)
Devices designed to detect and automatically mitigate network intrusion attempts.  
- **Functionality**: Analyzes packets to determine potential malicious intent and takes actions to mitigate threats based on analysis.

## Wireless Access Points
Devices that allow wireless clients to connect to a WLAN using RF communication.  
- **Band Types**: Available as single-band or dual-band, with modern versions typically being dual-band.
- **Frequency Bands**: Operate on 2.4 GHz and 5 GHz frequencies, aligning with modern IEEE 802.11 standards.
## Wireless Controllers
Devices or software that manage other network devices, including examples like the Cisco DNA Controller and Wireless LAN Controllers (WLCs).
- Cisco DNA Controller:

  - Utilizes a software-centric architecture for network management.
  - Employs APIs and a GUI for simplifying network operations.
  - Acts as a central component in Cisco Software-Defined Access (SDA) networks, facilitating LAN construction through policies and automation.  
- Wireless LAN Controllers (WLCs):

  - Centralize security configurations and manage mobility services for Access Points (APs) across the network.
  - Offer features like user authentication, RF management, security/policy enforcement, and Quality of Service (QoS) to Lightweight Access Points (LAPs).
  - Utilize IEEE 802.1Q trunk ports for physical connections to other network devices.
  - Require LAPs to function; LAPs must reboot and drop client associations if the WLC is unavailable.
  
# Glossary
## Broadcast Domain

A broadcast domain is a network segment within which a broadcast packet sent from any device is received by all other devices in the segment. Broadcast domains are typically bounded by routers because routers do not forward broadcast packets, effectively limiting the spread of broadcast traffic within a single segment. The primary purpose of a broadcast domain is to facilitate communication between devices on the same local network through the use of broadcast messages, which are sent to all nodes in the domain.  
## Wireless Access Points
### Lightweight Access Points (LAPs)
- Management: LAPs are managed centrally by a Wireless LAN Controller (WLC). They rely on the WLC for network configuration, management, and data processing.
- Functionality: LAPs primarily focus on transmitting and receiving wireless traffic. Advanced functions, such as security protocols, network configurations, and radio frequency (RF) management, are handled by the WLC.
- Deployment: Ideal for larger, complex networks where centralized management can significantly reduce the complexity and overhead of managing individual access points.  

### Access Points (Traditional APs)
- Autonomous APs (Traditional APs): These are standalone devices that function independently. Each AP handles its own configuration and management, including security settings, network configurations, and RF management.
- Functionality: Autonomous APs contain built-in software allowing them to handle all aspects of wireless communication, including client authentication, data forwarding, and network security, without the need for external control.
- Deployment: Suitable for smaller networks or situations where individual APs operate independently without the need for centralized management.