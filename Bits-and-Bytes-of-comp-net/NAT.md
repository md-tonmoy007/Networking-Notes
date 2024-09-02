---
module name: Network Services
src: https://www.coursera.org/learn/computer-networking/home/module/4
tags: 
module: "4"
---
#  Basics of NAT

1. **NAT Overview**:
   - Network Address Translation (NAT) is a technique, not a protocol, used to translate one IP address into another.
   - It's implemented differently across various operating systems and network hardware but serves consistent purposes.

2. **Functions of NAT**:
   ![[Pasted image 20240825072024.png]]
   - **IP Translation**: NAT allows a gateway (router or firewall) to rewrite the source IP of outgoing packets and rewrite the destination IP for incoming responses.
   - **Security and IPv4 Conservation**: NAT helps preserve IPv4 addresses and provides a security layer by masking internal IP addresses.

3. **NAT Example**:
   - **Basic Setup**: Two networks (A: 10.1.1.0/24 and B: 192.168.1.0/24) with a router between them.
   - **IP Masquerading**: When a computer on Network A sends data to Network B, NAT rewrites the source IP to the router’s IP on Network B. The response from Network B is rewritten to send the data back to the correct computer on Network A.

4. **IP Masquerading**:
   - **Hiding Internal IPs**: NAT hides internal IP addresses, making them invisible to the outside network, enhancing security.
   - **One-to-Many NAT**: Multiple computers on a local network share a single external IP address, commonly used in LANs.

### Summary:

Network Address Translation (NAT) is a technique used in networking to translate IP addresses for purposes such as conserving IPv4 addresses and enhancing security. By rewriting IP addresses in outgoing and incoming data packets, NAT can mask internal network structures from the outside world. This process, known as IP masquerading, helps protect networks by preventing external entities from directly accessing internal devices. One-to-many NAT, where many internal IPs are translated to a single external IP, is widely used in local area networks (LANs).




# NAT and the Transport Layer

1. **NAT at the Transport Layer**:
    
    - **Complexity**: While NAT is straightforward at the network layer (IP translation), it gets more complicated at the transport layer, especially with one-to-many NAT where multiple devices share a single IP.
2. **Port Preservation**:
    
    - **Function**: Ensures that the source port chosen by a client is preserved by the NAT device (router), allowing the router to direct return traffic to the correct device.
    - **Mechanism**: The router keeps track of the source port and uses it to match incoming traffic with the correct internal IP address.
3. **Handling Port Conflicts**:
    
    - **Conflict Resolution**: If two devices choose the same source port, the router selects an unused port to avoid conflicts.
4. **Port Forwarding**:
    
    - **Purpose**: Allows specific destination ports to be mapped to specific internal devices, enabling IP masquerading while allowing external traffic to reach the correct internal service.
    - **Example**: Traffic aimed at port 80 on an external IP can be forwarded to an internal web server, while other ports can be mapped to different services (e.g., mail server).
5. **Simplifying External Interactions**:
    
    - **Unified Access**: Port forwarding allows multiple services with different internal IPs to be accessible through the same external IP and DNS name, simplifying how external users interact with these services.

### Summary:

NAT becomes more complex at the transport layer, especially in one-to-many scenarios where multiple devices share a single external IP. Port preservation is a key technique that allows NAT devices to direct return traffic to the correct internal device by keeping track of the source port. In cases of port conflicts, the router assigns a different, unused port. Port forwarding is another critical technique, enabling specific external ports to be mapped to internal devices, allowing IP masquerading while still making internal services accessible to the outside world. This also simplifies the interaction with multiple services hosted by the same organization using a single external IP and DNS name.



# IPv4 Address Exhaustion
## IPv4 Address Exhaustion

IT professionals are responsible for troubleshooting network connections. If a device cannot connect to the network, the IP address is used as a part of a command line to test if the device is the issue. The [](https://www.iana.org/)Internet Assigned Numbers Authority (IANA) distributes IP addresses, so unique addresses are used when connecting to the internet. Since 1988 IANA has assigned IP addresses, but the internet has expanded drastically, requiring billions of IP addresses. The possible combinations of numbers (4.2 billion) have almost run out. This reading will explain the structure for the distribution of IP addresses and how IPv6 is being used to solve the limited number of IP addresses available. 

## Regional internet registries (RIRs)

IANA assigns IP address blocks to the five regional internet registries (RIRs). An RIR is an organization that manages internet number resources within a geographical region. IANA is responsible for assigning address blocks to five Regional Internet Registries (RIRs):

- AFRINIC - Africa
    
- ARIN - USA, Canada, and parts of the Caribbean
    
- APNIC - Most of Asia, Australia, New Zealand, and Pacific Island nations
    
- LACNIC - Central America, South America, and the remaining parts of the Caribbean not covered by ARIN
    
- RIPE - Europe, Russia, Middle East, and portions of Central Asia
    

Your computer gets its IP address directly from an RIR, not the IANA.

![Geographical map showing the regions covered by each of the Regional Internet Registries.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/PctLazF7SY2LS2sxe-mNkg_0ae37b45f9da4560b3c2ed720f431bf1_IPv4-Address-Exhaustion--C2M4-.png?expiry=1724716800000&hmac=j6wapRRAWCKpSE2nZyvaiiU69gtWzfcKoCIwd5OaA8M)

### Timeline for IPv4 address exhaustion

On February 3, 2011, IATA assigned the last unallocated /8 of the 4.2 billion possible combinations of IPv4 addresses. In some regions, you use a recycled number as a new IP address due to reaching IP exhaustion. The RIRs exhausted the following blocks by date:

- APNIC reached its final /8 addresses in April 2011.
    
- RIPE reached its final /8 addresses in September 2012. 
    
- LACNIC reached its final /10 addresses in June 2014.
    
- ARIN exhausted its list of free IPv4 addresses in September 2015.
    
- AFRINIC entered IPv4 Exhaustion Phase 2 in January 2020.
    

## IPv6

IPv6 will replace IPv4, using 128-bit addresses. IPv6 provides an identification and location system for computers on networks and routes traffic across the internet. The 128-bit addresses used by IPv6 provide a practically inexhaustible number of addresses. While IPv6 will solve many IPv4 address exhaustion issues, 99% of the devices in use today still use IPv4. IT professionals should be aware of IPv6 as it begins to take effect over the coming years and the structure of IP addresses changes.