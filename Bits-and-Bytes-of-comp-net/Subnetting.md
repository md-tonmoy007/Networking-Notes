---
module name: The Network Layer
src: https://www.coursera.org/learn/computer-networking/home/module/2
tags: 
module: "2"
---
# Subnetting

#### what is subnetting?

Subnetting is the process of dividing a large network into smaller, more manageable subnetworks or subnets.


# Subnet mask
- **Network, Host, and Subnet IDs**:
    
    - **Network ID**: Identifies the network.
    - **Host ID**: Identifies individual hosts within a network.
    - **Subnet ID**: Further divides a network, using bits that would normally be part of the host ID.
      
- **IP Address Structure**:
    
    - IP addresses are 32-bit numbers.
    - Without subnets, bits are split between network ID and host ID.
    - With subnets, some host ID bits are used for the subnet ID, allowing a single 32-bit IP address to function across different networks.
      
- **Routing Process**:
    
    - **Core Routers**: Use the network ID to route datagrams to the appropriate gateway router.
    - **Gateway Routers**: Use additional information to forward the datagram to the destination machine or the next router.
    - **Final Router**: Uses the host ID to deliver the datagram to the intended recipient machine.
      
- **Subnet Masks**:
    
    - **Definition**: 32-bit numbers, like IP addresses, written as four octets in decimal.
    - **Purpose**: Used to calculate subnet IDs.
    - **Common Misunderstanding**: Subnet masks are often memorized as "magic numbers" without understanding their function.
      
- **Binary Representation**:
    
    - IP address components are converted into binary with padding if necessary (e.g., 9 becomes 0000 1001 in binary for the first octet).
      
- **Binary Representation of IP and Subnet Mask**:
    
    - The IP address 9.100.100.100 has a binary representation with a mix of ones and zeros.
    - A subnet mask consists of two parts: a string of ones (the mask) followed by zeros.
      
- **Subnet Mask Purpose**:
    
    - The ones in the subnet mask define the subnet ID, while the zeros indicate the host ID.
    - Example: Subnet mask 255.255.255.0 has 24 ones followed by 8 zeros, identifying the first 24 bits as the subnet ID and the last 8 bits as the host ID.
      
- **Subnet Size**:
    
    - The size of a subnet is determined by its subnet mask.
    - Example: 255.255.255.0 leaves 8 bits for host IDs, providing 256 possible addresses (0-255).
    - However, usually, only 254 addresses are assignable since 0 is not used and 255 is reserved for broadcasting.
      
- **Shorthand Notation**:
    
    - Subnet masks can be represented using a shorthand notation that indicates the number of ones.
    - Example: 255.255.255.224 translates to /27, meaning 27 ones followed by 5 zeros.
    - The entire IP address and subnet mask can be written as 9.100.100.100/27.
      
- **Understanding Both Notations**:
    
    - It's important to understand both the full subnet mask notation (e.g., 255.255.255.224) and the shorthand notation (e.g., /27), as both are commonly used.


**Example**
![[Pasted image 20240803083040.png]]
this can be written as 9.100.100.100/27
number of host are $2^5$


# CIDR
- **Address Classes and Subnetting**:
    
    - Initially, the Internet IP space was divided using address classes (A, B, C), with fixed network ID sizes: 8 bits for Class A, 16 bits for Class B, and 24 bits for Class C.
    - This system led to inefficiencies, such as too many Class C networks (over 2 million) and inappropriate network sizes for business needs.
- **Problems with Traditional Subnetting**:
    
    - Class C networks (254 hosts) were often too small, while Class B networks (65,534 hosts) were too large.
    - Companies often had to use multiple Class C networks, complicating routing tables.
- **Introduction of CIDR (Classless Inter-Domain Routing)**:
    
    - CIDR eliminates the concept of fixed address classes, allowing more flexible and efficient IP address allocation.
    - CIDR uses subnet masks to combine the network ID and subnet ID into one, simplifying network management.
    - CIDR notation uses a slash (e.g., /24) to indicate the number of bits used for the network portion of the address.
- **Benefits of CIDR**:
    
    - **Flexible Network Sizes**: CIDR allows for networks of varying sizes, not limited to the rigid Class A, B, or C structure.
    - **Simplified Routing**: Combining smaller networks into one larger network reduces the number of routing table entries.
    - **Increased Host Capacity**: By merging networks (e.g., using a /23 netmask), CIDR provides more available host IPs (510 in a /23 network versus 508 in two /24 networks).
- **Memory Lock Point**:
    
    - Remember that a /24 network has 254 usable IP addresses (256 minus 2), while a /23 network has 510 usable IP addresses (512 minus 2).
      ![[Pasted image 20240803083702.png]]
