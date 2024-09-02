---
module name: The Network Layer
src: https://www.coursera.org/learn/computer-networking/home/module/2
tags: 
module: "2"
---
# Basic Routing Concepts

**Router:** a router is a network device that forwards traffic depending on the destination address of that traffic.


- **Routing Overview**:
    
    - Routing is the process of forwarding data packets across networks to reach a destination.
    - Routers are network devices that direct traffic based on the destination IP address of the packets.
    - The internet consists of millions of interconnected networks, and routing allows seamless communication between them.
      
- **Basic Routing Steps**:
    ![[Pasted image 20240807083950.png]]
    1. **Receive the Packet**: A router receives a packet on one of its interfaces.
    2. **Examine the Destination IP**: The router checks the destination IP address of the packet.
    3. **Check Routing Table**: The router looks up the destination network in its routing table to determine the best path.
    4. **Forward the Packet**: The router forwards the packet out through the interface closest to the destination network.
       
- **Example of Simple Routing**:
    ![[Pasted image 20240807085722.png]]
    - **Network A**: 192.168.1.0/24 with router IP 192.168.1.1.
    - **Network B**: 10.0.0.0/24 with router IP 10.0.0.254.
    - A computer on Network A with IP 192.168.1.100 sends a packet to IP 10.0.0.10 on Network B.
    - 
      The router's interface on network A receives the packet because it sees that destination MAC address belongs to it. The router then strips away the data link layer encapsulation, leaving the network layer content, the IP datagram. Now, the router can directly inspect the IP datagram header for the destination IP field. It finds the destination IP of 10.0.0.10. The router looks at its routing table and sees that network B or the 10.0.0.0/24, network is the correct network for the destination IP. It also sees that this network is only one hop away in fact, since it's directly connected, the router even has the MAC address for this IP in its ARP table. Next, the router needs to form a new packet to forward along to network B, it takes all of the data from the first IP datagram and duplicates it, but it detriments the TTL field by one and calculates a new checksum. Then, it encapsulates this new IP datagram inside of a new Ethernet frame. This time it sets its own MAC address of the interface on network B as the source MAC address. Since it has the MAC address of 10.0.0.10 in its ARP table, it sets that as the destination MAC address. Lastly, the packet is sent out of its interface on network B and the data finally gets delivered to the node living at 10.0.0.10. 
      
- **Adding Complexity: Multiple Networks**:
    ![[Pasted image 20240807091338.png]]
    - **Network C**: 172.16.1.0/23 connected to Network B through a second router.
    - The second router has IP 10.0.0.1 on Network B and IP 172.16.1.1 on Network C.
    - A computer on Network A wants to send data to a computer on Network C (IP 172.16.1.100).
    - The first router identifies the correct path as via the second router (10.0.0.1) and forwards the packet. In this case, the first router checks the routing table and find the best path.
    - The second router then delivers the packet to the final destination on Network C.
      
- **Routing Table**:
    
    - A routing table is a set of rules stored in a router that determines the best path for forwarding packets to their destinations.
    - Routing tables include information about the connected networks, the next hop (next router in the path), and metrics like hop count or latency.

>   ----------------------------- **If you forgot**---------------------------------------------
> - **TTL (Time to Live)**: The TTL field in a packet is decremented by 1 each time it passes through a router. When TTL reaches 0, the packet is discarded to prevent it from circulating indefinitely.
> -  **Checksum**: A checksum is recalculated at each hop to ensure data integrity during transmission.





- **Structure of a Routing Table**:
    
    - **Destination Network**:
        
        - This column lists networks known to the router, defined by a network ID and subnet mask.
        - The router uses this information to determine which network a packet's destination IP address belongs to.
        - A routing table often includes a "catch-all" entry (default route) for any IP addresses not explicitly listed.
          
    - **Next Hop**:
        
        - This indicates the IP address of the next router (or hop) to which the data should be forwarded.
        - If the destination network is directly connected, this entry will indicate that no further hops are necessary.
          
    - **Total Hops**:
        
        - This column records the number of intermediary routers (hops) between the current router and the destination network.
        - Routers use this information to select the shortest and most efficient path for data transmission, ensuring timely delivery.
        - The number of hops can change due to network conditions like failures, congestion, or new routes.
          
    - **Interface**:
        
        - This specifies which of the router's network interfaces should be used to forward packets to the destination network.
        - A router with multiple interfaces needs to know the correct interface for each outgoing packet.





1. **Introduction to Routing Protocols**:
    
    - **Purpose**: Routing protocols enable routers to dynamically update their routing tables with the best paths to destination networks. They allow routers to communicate and exchange information, which is crucial for efficient data transmission across networks, even over vast distances.
    - **Types of Protocols**: There are two main categories: **Interior Gateway Protocols (IGPs)**, used within a single autonomous system, and **Exterior Gateway Protocols (EGPs)**, used between different autonomous systems.
      ![[Pasted image 20240810160200.png]]
      
2. **Interior Gateway Protocols (IGPs)**:
    
	    - **Autonomous System (AS)**: An AS is a collection of networks under a single administrative domain, such as a corporation's internal network or an Internet Service Provider's (ISP) network.
    - **Types of IGPs**:
        - **Distance Vector Protocols**: Share information about the distance to destination networks with directly connected neighboring routers.
        - **Link State Protocols**: Share detailed information about the state of links within the AS, allowing routers to have a complete view of the network's topology.
          
3. **Distance Vector Protocols**:
    
    - **Function**: A router using a distance vector protocol sends its routing table, which lists known networks and the number of hops to reach them, to its neighboring routers.
    - **Example**:
        - **Router A** knows that Network X (10.1.1.0/24) is four hops away via **Router C**. **Router B** knows that Network X is only two hops away. When **Router B** shares this information with **Router A**, **Router A** updates its routing table to route traffic to Network X through **Router B** instead of **Router C**, reducing the hop count to three.
    - **Limitations**:
        - **Limited View**: Routers only have knowledge about their immediate neighbors and do not have a complete view of the network, leading to slower responses to changes in the network topology.
4. **Link State Protocols**:
    
    - **Function**: Routers using link state protocols share information about the state of their links with all routers in the AS. This allows every router to build a complete map of the network's topology.
    - **Comprehensive View**:
        - All routers in the AS know the status of all other routers and links, which enables them to calculate the best path to any destination network.
    - **Algorithms**:
        - Routers use algorithms like Dijkstra's Shortest Path First (SPF) to determine the optimal routes based on the comprehensive network map.
    - **Resource Requirements**:
        - Link state protocols require more memory to store the detailed network information and more processing power to run the necessary algorithms.
    - **Modern Networking**:
        - As computer hardware has improved, link state protocols have largely replaced distance vector protocols due to their efficiency and faster response to network changes.
5. **Comparison of Distance Vector and Link State Protocols**:
    
    - **Distance Vector**:
        - **Pros**: Simpler, requires less processing power.
        - **Cons**: Limited network view, slower to adapt to changes.
    - **Link State**:
        - **Pros**: Comprehensive network view, faster response to changes, more efficient routing.
        - **Cons**: Requires more memory and processing power.



- **Introduction to Exterior Gateway Protocols (EGPs)**:
    
    - **Purpose**: EGPs are used to manage data exchange between different autonomous systems (AS), which are networks under different administrative domains. Unlike Interior Gateway Protocols (IGPs) that manage routing within a single AS, EGPs operate across the broader Internet, connecting various ASs.
    - **Importance**: EGPs are crucial for the functioning of the global Internet, enabling data to traverse the complex mesh of interconnected networks that form the Internet.
- **The Role of Autonomous Systems (AS)**:
    
    - **Definition**: An AS is a collection of IP networks and routers under the control of a single organization or entity. Each AS is identified by a unique Autonomous System Number (ASN).
    - **Core Internet Routers**: At the highest levels of the Internet, core routers are responsible for directing traffic between ASs. Their primary goal is to get data to the edge router of the destination AS as efficiently as possible.
- **Autonomous System Numbers (ASNs)**:
    
    - **Management by IANA**: The Internet Assigned Numbers Authority (IANA) is responsible for allocating ASNs, similar to how it manages IP address allocation. This central management prevents conflicts and chaos on the Internet by ensuring that each ASN is unique.
    - **Format**: ASNs are 32-bit numbers but are usually represented as single decimal numbers (e.g., AS19604). Unlike IP addresses, which are divided into network and host portions, ASNs are simpler and static, representing entire autonomous systems.
    - **Human Interaction**: ASNs are less frequently referenced by humans compared to IP addresses. However, knowing the ASN associated with an organization (like IBM's AS19604) can be useful for network administration and troubleshooting.
- **Why EGPs Matter**:
    
    - **Inter-AS Communication**: EGPs allow different ASs to exchange routing information, enabling data to flow across the Internet. Without EGPs, the global routing of data between networks managed by different organizations would be impossible.
    - **Key Protocol - BGP**: The most well-known EGP is the Border Gateway Protocol (BGP), which is responsible for routing data between ASs on the Internet. BGP is critical for maintaining the stability and reachability of the global Internet.
- **Practical Understanding of EGPs**:
    
    - **Relevance for IT Professionals**: While the intricacies of EGPs and BGP are typically relevant for network engineers working at ISPs or large organizations, a basic understanding is beneficial for all IT professionals. This knowledge helps in understanding how the Internet functions and how data is routed across the globe.


![[Pasted image 20240810155653.png]]

**See also :**
1. [practical networking youtube video](https://www.youtube.com/watch?v=KjNYEzEBRD8)
2. [rfc2453](https://datatracker.ietf.org/doc/html/rfc2453) => about the RIP protocol
3. [wikipedia](https://en.wikipedia.org/wiki/Routing_Information_Protocol) => same as before
4. [cisco eigrp](https://www.cisco.com/c/en/us/support/docs/ip/enhanced-interior-gateway-routing-protocol-eigrp/16406-eigrp-toc.html)
5. [wikipedia ospf](https://www.cisco.com/c/en/us/support/docs/ip/enhanced-interior-gateway-routing-protocol-eigrp/16406-eigrp-toc.html)
6. 

