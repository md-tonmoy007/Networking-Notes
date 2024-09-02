---
module name: 
src: 
tags: 
module:
---
## Overview of DHCP


- **DHCP Basics**:
    
    - DHCP automates the network configuration process for devices on a TCP/IP network.
    - Essential network settings like IP address, subnet mask, gateway, and DNS are provided by the DHCP server.
- **IP Allocation Methods**:
    
    - **Dynamic Allocation**: IPs are assigned from a pool and may change with each connection.
    - **Automatic Allocation**: The same IP is usually re-assigned to the same device if possible.
    - **Fixed Allocation**: Pre-assigned IPs are given based on a device's MAC address, offering more control and security.
- **DHCP and Network Management**:
    
    - Reduces the need for manual IP configuration, especially useful in large networks.
    - Can assign additional settings like NTP servers for time synchronization.



## DHCP in action

1. **DHCP as an Application Layer Protocol**: Relies on transport, network, data link, and physical layers but helps configure the network layer itself.
    
2. **DHCP Discovery Process**: The sequence by which a client obtains network configuration information:
    
    - **Server Discovery**: Client sends a DHCP discover message as a broadcast since it lacks an IP.
    - **DHCP Offer**: Server responds with a DHCP offer, also as a broadcast, containing potential IP information.
    - **DHCP Request**: Client accepts the offer by sending a DHCP request message.
    - **DHCP Acknowledgment (DHCPACK)**: Server confirms the configuration with a DHCPACK message.
3. **DHCP Messages**:
    
    - Sent via UDP ports 67 (server) and 68 (client).
    - Discover and Offer messages are broadcasted to the entire network.
4. **IP Allocation Types**:
    
    - **Dynamic Allocation**: IPs are assigned from a pool, and the client may get a different IP each time.
    - **Automatic Allocation**: The server attempts to assign the same IP to the same client each time.
    - **Fixed Allocation**: Specific IPs are reserved for specific MAC addresses.
5. **DHCP Lease**: Temporary network configuration assigned to a client with an expiration time; can be renewed or released.