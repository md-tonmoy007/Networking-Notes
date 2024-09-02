---
module name: The Network Layer
src: https://www.coursera.org/learn/computer-networking/home/module/2
tags:
  - network-layer
module: "2"
---
# The Network Layer

In a Local Area Network (LAN), nodes communicate using physical MAC addresses, which switches quickly learn to manage transmissions. However, MAC addressing doesn't scale well because every network interface has a unique MAC address without a systematic order, making it unsuitable for global communication. ARP (Address Resolution Protocol) helps nodes learn physical addresses but is limited to single network segments. To address this, the network layer and Internet Protocol (IP) are introduced. IP addresses facilitate communication across distances. By the end of the lesson, you'll understand how to identify an IP address, encapsulate IP datagrams in Ethernet frames, and describe the fields of an IP datagram header.

# IPv4 Datagram and Encapsulation
![[Pasted image 20240728103635.png]]

Sure, here are the key points defined based on the provided information about the IP datagram header:

1. **IP Datagram**: A packet at the network layer under the IP protocol, consisting of a header and a payload.

2. **Header Fields**:
   - **Version (4 bits)**: Indicates the IP version (e.g., IPv4 or IPv6).
   - **Header Length (4 bits)**: Specifies the length of the IP header, typically 20 bytes for IPv4.
   - **Service Type (8 bits)**: Used for Quality of Service (QoS) to prioritize certain datagrams.
   - **Total Length (16 bits)**: Indicates the total length of the IP datagram, with a maximum size of 65,535 bytes.
   - **Identification (16 bits)**: Groups related fragments of a datagram for reassembly.
   - **Flags (3 bits)**: Controls or indicates fragmentation.
   - **Fragment Offset (13 bits)**: Used to reassemble fragmented datagrams in the correct order.
   - **Time To Live (TTL) (8 bits)**: Limits the lifespan of a datagram by specifying the maximum number of hops.
   - **Protocol (8 bits)**: Indicates the transport layer protocol (e.g., TCP or UDP).
   - **Header Checksum (16 bits)**: Error-checking code for the header, recalculated at each hop.
   - **Source IP Address (32 bits)**: The originating IP address.
   - **Destination IP Address (32 bits)**: The destination IP address.
   - **Options (variable)**: Optional settings for the datagram, mainly for testing.
   - **Padding (variable)**: Ensures the header is the correct size if options are used.

3. **Payload**: The content carried by the IP datagram, encapsulating the entire TCP or UDP packet.

4. **Encapsulation**: The process where the entire IP datagram becomes the payload of an Ethernet frame, illustrating the layered nature of networking.



>The IP diagram is encapsulated and then becomes the payload of an Ethernet frame. Though the IP diagram has it's own payload encapsulating the entire TCP/UDP packet.


# IPv4 Address Classes

1. **IP Address Structure**:
    
    - IP addresses are divided into two sections: Network ID and Host ID.
    - Example: For IP address 9.100.100.100:
        - Network ID: First octet (9)
        - Host ID: Second, third, and fourth octets (100.100.100)
2. **Address Class System**:
    
    - **Class A**:
        - First octet for Network ID, last three octets for Host ID.
        - Range: 0-127 for the first octet.
        - Total Addresses: 224=16,777,2162^{24} = 16,777,216224=16,777,216
    - **Class B**:
        - First two octets for Network ID, last two octets for Host ID.
        - Range: 128-191 for the first octet.
        - Total Addresses: 216=65,5362^{16} = 65,536216=65,536
    - **Class C**:
        - First three octets for Network ID, last octet for Host ID.
        - Range: 192-223 for the first octet.
        - Total Addresses: 28=2562^8 = 25628=256
3. **Address Class Identification**:
     a way of defining how the global IP address space is split up.
     
    - **Class A**: First bit is 0.
    - **Class B**: First bits are 10.
    - **Class C**: First bits are 110.
    - **Class D**: First bits are 1110 (Used for multicasting; Range: 224-239).
    - **Class E**: First bits are 1111 (Unassigned, used for testing).
      
      ![[Pasted image 20240731182257.png]]
4. **Practical Relevance**:
    
    - The class system is largely replaced by CIDR (Classless Inter-Domain Routing).
    - Understanding the class system is still important for networking education.

### Additional Notes:

- **IBM Ownership**:
    
    - IBM owns IP addresses where the first octet is 9.
      
- **Range of Each Octet**:
    
    - Each octet in an IP address can range from 0 to 255 (8 bits).
    
- **Multicasting (Class D)**:
    
    - Multicasting allows a single IP datagram to be sent to an entire network.
      

By understanding these key points, you will have a solid foundation in the traditional IP address class system, which is essential for a well-rounded networking education.


# Address resolution Protocol (ARP)

1. **Relationship Between MAC and IP Addresses**:
    
    - MAC addresses are used at the Data Link Layer.
    - IP addresses are used at the Network Layer.
    - ARP bridges the gap between these two by resolving IP addresses to their corresponding MAC addresses.
2. **Purpose of ARP**:
    
    - ARP is a protocol used to discover the MAC (hardware) address of a node that corresponds to a specific IP address.
3. **ARP in Action**:
    
    - When sending an IP datagram, the device needs to encapsulate it in an Ethernet frame.
    - To complete the Ethernet frame header, the device needs the destination MAC address.
    - If the destination IP doesn’t have an entry in the ARP table, the device sends a broadcast ARP request to the network.
4. **ARP Broadcast**:
    
    - ARP broadcasts are sent to the MAC broadcast address (all Fs: FF:FF:FF:FF:FF
        
        ).
    - This broadcast is delivered to all devices on the local network.
    - The device with the matching IP address (e.g., 10.20.30.40) will respond with an ARP response containing its MAC address.
5. **ARP Response and ARP Table**:
    
    - The responding device sends its MAC address back to the requesting node.
    - The requesting node then stores this IP-MAC pair in its local ARP table for future use, avoiding the need to send another ARP broadcast for subsequent communications with the same IP.
6. **ARP Table**:
    
    - ARP tables are maintained by network devices to keep a record of IP-to-MAC address mappings.
    - These entries are temporary and generally expire after a short period to account for any changes in the network.
7. **Importance of ARP**:
    
    - ARP is crucial for network communication, allowing devices to communicate with one another over Ethernet by resolving IP addresses to their corresponding MAC addresses.

By understanding ARP, you can see how devices on a network discover and communicate with each other using both IP and MAC addresses, ensuring efficient data transmission within the network.






