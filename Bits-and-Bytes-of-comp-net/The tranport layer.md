---
module name: Introduction to the Transport and Application Layers
src: https://www.coursera.org/learn/computer-networking/home/module/3
tags: 
module: "3"
---
# Dissection of a TCP Segment

![[Pasted image 20240818090113.png]]

#### **Structure of a TCP Segment**

1. **Source Port and Destination Port**:
    
    - **Destination Port**: This is the port of the service the traffic is intended for, such as port 80 for web traffic.
    - **Source Port**: A high-numbered port, known as an ephemeral port, is chosen by the sending device to keep multiple outgoing connections separate. The source port ensures that the response from the server is directed back to the correct application on the originating computer. For example, it ensures that a web server's response reaches your web browser and not another application like a word processor.
2. **Sequence Number**:
    
    - This 32-bit number keeps track of the order of TCP segments in a sequence. Since data often exceeds the size limits of an Ethernet frame (typically 1,518 bytes), it's split into multiple segments. The sequence number indicates the position of each segment, ensuring they are reassembled correctly.
3. **Acknowledgment Number**:
    
    - This field, similar to the sequence number, is used for acknowledging received data. It indicates the next expected segment number. For example, if a segment has a sequence number of 1 and an acknowledgment number of 2, it means "This is segment 1; expect segment 2 next."
4. **Data Offset**:
    
    - The data offset is a four-bit field that specifies the length of the TCP header. This information tells the receiving device where the actual data payload begins.
5. **TCP Control Flags**:
    
    - There are six one-bit flags in this section, used for managing control functions such as establishing or terminating a connection.
6. **TCP Window**:
    
    - The TCP window field, a 16-bit number, specifies the range of sequence numbers that can be sent before an acknowledgment is required. TCP relies heavily on acknowledgments to ensure reliable data transmission and prevent sending data that isn't being received.
7. **Checksum**:
    
    - The checksum is a 16-bit field used for error-checking. It operates similarly to checksums at the IP and Ethernet levels. After the entire segment is received, the checksum is recalculated and compared with the checksum in the header to detect any data corruption.
8. **Urgent Pointer**:
    
    - This field is used with one of the TCP control flags to prioritize certain segments. However, this feature is rarely used in modern networking.
9. **Options**:
    
    - The options field is another rarely used section, sometimes employed in more complex flow control protocols.
10. **Padding**:
    
    - The padding field consists of zeros, ensuring that the data payload starts at the expected location in the segment.



#### **TCP Control Flags**

TCP uses a series of control flags to manage the state of a connection. These flags are included in the TCP header and are used in various stages of communication. Here are the six primary TCP control flags:

1. **URG (Urgent) Flag**:
    
    - **Purpose**: Indicates that the segment is urgent.
    - **Details**: A value of 1 in the URG field means that the segment should be prioritized, and the urgent pointer field provides additional information. However, this feature is rarely used in modern networking.
2. **ACK (Acknowledgment) Flag**:
    
    - **Purpose**: Confirms receipt of data.
    - **Details**: When the ACK flag is set to 1, it signifies that the acknowledgment number field should be examined, indicating the next expected sequence number.
3. **PSH (Push) Flag**:
    
    - **Purpose**: Instructs the receiver to push buffered data to the application immediately.
    - **Details**: The PSH flag is used when the transmitting device wants the receiving device to process the data without delay. This is useful when sending small amounts of data that require an immediate response.
4. **RST (Reset) Flag**:
    
    - **Purpose**: Resets the connection.
    - **Details**: If a TCP connection encounters issues, such as missing or malformed segments, the RST flag is used to reset the connection and start over. It's a way for one device to indicate that the current communication cannot be continued.
5. **SYN (Synchronize) Flag**:
    
    - **Purpose**: Initiates a connection.
    - **Details**: The SYN flag is used to initiate a TCP connection. It synchronizes sequence numbers between the two devices, ensuring that they start the conversation from a known point.
6. **FIN (Finish) Flag**:
    
    - **Purpose**: Terminates a connection.
    - **Details**: When a device is ready to close the connection, it sends a FIN flag to indicate that no more data will be sent.



#### **Establishing a TCP Connection: The Three-Way Handshake**

![[Pasted image 20240818090523.png]]

To establish a TCP connection, the following steps occur between two devices (let's call them Computer A and Computer B):

1. **Step 1: SYN**:
    
    - **Action**: Computer A sends a TCP segment with the SYN flag set.
    - **Purpose**: This is Computer A's way of saying, "Let's establish a connection, and here’s my sequence number."
2. **Step 2: SYN/ACK**:
    
    - **Action**: Computer B responds with a TCP segment that has both the SYN and ACK flags set.
    - **Purpose**: Computer B acknowledges Computer A's sequence number and synchronizes its own sequence number for the connection.
3. **Step 3: ACK**:
    
    - **Action**: Computer A responds with a TCP segment that has only the ACK flag set.
    - **Purpose**: This is Computer A's acknowledgment of Computer B's sequence number. The connection is now established, and data transmission can begin.

This exchange of segments with SYN, SYN/ACK, and ACK flags is known as the **Three-Way Handshake**, a fundamental process for establishing TCP connections. Once this handshake is complete, the connection operates in **full duplex** mode, allowing both devices to send and receive data simultaneously.



#### **Closing a TCP Connection: The Four-Way Handshake**
![[Pasted image 20240818090549.png]]

When a device is ready to close a TCP connection, the following steps take place:

1. **Step 1: FIN**:
    
    - **Action**: The device ready to close the connection sends a TCP segment with the FIN flag set.
    - **Purpose**: This indicates that the device has finished sending data.
2. **Step 2: ACK**:
    
    - **Action**: The other device acknowledges the FIN request by sending a TCP segment with the ACK flag set.
3. **Step 3: FIN**:
    
    - **Action**: The second device, if it is also ready to close the connection, sends a FIN flag.
    - **Purpose**: This indicates that the second device is also finished sending data.
4. **Step 4: ACK**:
    
    - **Action**: The first device sends a final ACK, confirming the closure of the connection.

This process is known as the **Four-Way Handshake**, and it ensures that both devices properly close the connection.



# TCP ports and sockets

Ports are used in the Transport Layer of the TCP/IP Five-Layer Network Model. At this layer, the TCP is used to establish a network connection and deliver data. A TCP "segment" is the code that specifies ports used to establish a network connection. It does this on the service side of the connection by telling a specific service to listen for data requests coming into a specific port. Once a TCP segment tells a service to listen for requests through a port, that listening port becomes a "socket." In other words, a socket is an active port used by a service. Once a socket is activated, a client can send and receive data through it. 

## Three categories of ports

Since a 16-bit number identifies ports, there can be 65,535 of them. Given the number of ports available, they have been divided into three categories by the Internet Assigned Numbers Authority ([IANA](https://www.iana.org/)): System Ports, User Ports, and Ephemeral Ports.

- **System Ports** are identified as ports 1 through 1023. System ports are reserved for common applications like FTP (port 21) and Telnet over TLS/SSL (port 992). Many still are not assigned. Note: Modern operating systems do not use system ports for [outbound traffic ](outbound%20traffic%20and%20inbound%20traffic.md).
    
- **User Ports** are identified as ports 1024 through 49151. Vendors register user ports for their specific server applications. The IANA has officially registered some but not all of them.
    
- **Ephemeral Ports (Dynamic or Private Ports)** are identified as ports 49152 through 65535. Ephemeral ports are used as temporary ports for private transfers. Only clients use ephemeral ports.
    

Not all operating systems follow the port recommendations of the IANA, but the IANA registry of assigned port numbers is the most reliable for determining how a specific port is being used. You can access the [IANA Service Name and Transport Protocol Port Number Registry here](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) or check out this [helpful list of commonly used ports](https://packetlife.net/media/library/23/common_ports.pdf).


#### **Common TCP Socket States**

1. **LISTEN**:
    
    - **Description**: The socket is ready and waiting for incoming connections.
    - **Context**: This state is only seen on the server side, where the socket is actively listening for connection requests from clients.
2. **SYN_SENT**:
    
    - **Description**: A synchronization (SYN) request has been sent, but the connection has not yet been established.
    - **Context**: This state is only seen on the client side, indicating that the client is trying to establish a connection with the server.
3. **SYN_RECEIVED**:
    
    - **Description**: The socket, previously in the LISTEN state, has received a synchronization request and sent a SYN/ACK response but hasn't received the final acknowledgment (ACK) from the client.
    - **Context**: This state is seen only on the server side.
4. **ESTABLISHED**:
    
    - **Description**: The TCP connection is fully established and in working order, allowing both sides to send data to each other.
    - **Context**: This state is present on both the client and server sides once the three-way handshake is complete and communication can occur.
5. **FIN_WAIT**:
    
    - **Description**: A FIN (finish) request has been sent, but the corresponding ACK from the other end has not yet been received.
    - **Context**: This state indicates that one side of the connection wants to close the communication channel.
6. **CLOSE_WAIT**:
    
    - **Description**: The connection has been closed at the TCP layer, but the application that opened the socket has not yet released it.
    - **Context**: This state suggests that the TCP connection has ended, but the program that created the socket has not yet closed it.
7. **CLOSED**:
    
    - **Description**: The connection has been fully terminated, and no further communication is possible.
    - **Context**: This state indicates that the socket is no longer in use, and all resources associated with the connection have been released.

#### **Variations in Socket States**

Different operating systems may have slightly different names and definitions for socket states, as these states exist outside the scope of the TCP protocol itself. While TCP as a protocol is universal, ensuring consistent communication across devices, the description of socket states at the operating system level may vary.

When troubleshooting TCP layer issues, it's essential to understand the specific socket state definitions for the systems you are working with, as these can influence how you diagnose and resolve network problems.

### TCP vs. UDP: Connection-Oriented and Connectionless Protocols

#### **TCP: The Connection-Oriented Protocol**

TCP, or Transmission Control Protocol, is a **connection-oriented** protocol, meaning it establishes a connection before any data is transmitted and maintains that connection to ensure all data is properly delivered. Here's how it works:

- **Connection Establishment**: TCP begins by establishing a connection between the sender and the receiver using a process known as the **three-way handshake**.
- **Data Transmission**: Once the connection is established, TCP ensures that every segment of data sent is acknowledged by the receiving end. This acknowledgment guarantees that both sides are aware of which data has been successfully delivered.
- **Error Handling**: TCP handles errors by resending any segments that were lost or corrupted during transmission. This is possible because of the sequence numbers assigned to each segment, allowing them to be reordered correctly even if they arrive out of sequence.
- **Connection Termination**: After all data has been transmitted, the connection is properly closed, ensuring that no further communication occurs unintentionally.

**Advantages**:
- **Reliability**: TCP's acknowledgment and retransmission mechanisms ensure that all data reaches its destination, making it ideal for applications where accuracy is critical, such as file transfers and web browsing.
- **Error Recovery**: By detecting and correcting errors, TCP provides a robust method for data transmission over unreliable networks.

**Disadvantages**:
- **Overhead**: The processes of establishing a connection, sending acknowledgments, and managing sequence numbers add significant overhead to the communication process. This can consume a considerable amount of bandwidth and increase latency.
- **Slower Transmission**: Due to its reliability mechanisms, TCP can be slower compared to connectionless protocols, especially in environments where speed is more critical than accuracy.

#### **UDP: The Connectionless Protocol**

In contrast, UDP, or User Datagram Protocol, is a **connectionless** protocol. It doesn't establish a connection before sending data, nor does it ensure that the data arrives at its destination.

- **No Connection Establishment**: With UDP, data is sent directly to the destination without the need for a connection or any kind of handshake.
- **No Acknowledgments**: UDP does not require the receiving end to acknowledge the receipt of data. This means there is no way to know if the data has been successfully delivered.
- **No Error Handling**: Since UDP does not manage sequence numbers or retransmissions, if any data is lost during transmission, it is simply gone.

**Advantages**:
- **Speed**: Without the need for connection establishment, acknowledgments, or error recovery, UDP can transmit data much faster than TCP. This makes it suitable for applications where speed is more important than reliability, such as live video streaming or online gaming.
- **Low Overhead**: UDP's minimal overhead allows for more efficient use of available bandwidth, making it ideal for applications that need to send large amounts of data quickly.

**Disadvantages**:
- **Unreliable**: The lack of error handling and acknowledgments means that data sent via UDP may not reach its destination, and if it does, it may arrive out of order or corrupted.
- **No Built-In Data Integrity**: Unlike TCP, which ensures that all data is transmitted correctly, UDP provides no guarantees, so it is not suitable for applications where data integrity is essential.

#### **Choosing Between TCP and UDP**

- **When to Use TCP**: TCP is the protocol of choice for applications where reliability is paramount, such as web browsing, email, and file transfers. In these scenarios, the overhead and potential latency introduced by TCP are justified by the need for accurate data transmission.
- **When to Use UDP**: UDP is preferred for applications where speed and efficiency are more important than reliability, such as live video streaming, VoIP, and online gaming. In these cases, the loss of some data packets may be acceptable, as the primary goal is to maintain real-time communication.

![[Pasted image 20240821081757.png]]
### Understanding Firewalls: The Guardians of Network Security

A **firewall** is a crucial component of network security that acts as a barrier between your internal network and external threats. It monitors and controls incoming and outgoing network traffic based on predetermined security rules. Here's how firewalls work and why they are vital:

#### **What is a Firewall?**

A firewall is essentially a device or program designed to block or allow network traffic based on a set of security criteria. By filtering traffic, firewalls protect networks from unauthorized access, attacks, and other security threats. They can operate at various layers of the network stack, making them versatile tools in securing network environments.

#### **Firewall Operation at Different Layers**

1. **Application Layer Firewalls**: These firewalls operate at the highest layer of the OSI model, inspecting the data being transmitted. They can block or allow traffic based on specific application-level rules, such as filtering HTTP requests or blocking specific types of files from being downloaded.
    
2. **Network Layer Firewalls**: These firewalls focus on the source and destination IP addresses and the protocols being used. They might block entire ranges of IP addresses or allow traffic only from trusted networks.
    
3. **Transport Layer Firewalls**: These are the most common types of firewalls, operating at the transport layer (Layer 4) of the OSI model. They are configured to block or allow traffic based on port numbers. For example, a transport layer firewall could allow web traffic on port 80 (HTTP) while blocking traffic on port 21 (FTP).
    

#### **How Firewalls Are Used in a Network**

Imagine a small business network where a server hosts multiple services, such as a public website and an internal file server. A firewall placed at the network's perimeter could be configured as follows:

- **Allow Traffic on Port 80**: The firewall would allow traffic to port 80, enabling external users to access the company's website.
- **Block All Other Ports**: To protect sensitive data, the firewall could block access to all other ports from external IP addresses, ensuring that the internal file server remains inaccessible to unauthorized users.

This configuration ensures that only the intended service (the website) is accessible from outside the network, while all other services are protected.

#### **Firewall Deployment: Network Devices vs. Host-Based Firewalls**

- **Network-Based Firewalls**: These are typically standalone devices or software running on a dedicated server that protects the entire network. They are often placed at the network's edge, acting as a gatekeeper for all incoming and outgoing traffic.
    
- **Host-Based Firewalls**: Modern operating systems, such as Windows, macOS, and Linux, come with built-in firewall functionality. These firewalls protect individual hosts by controlling traffic to and from specific services on that machine. For example, a host-based firewall might allow traffic to a web browser while blocking traffic to a potentially malicious application.
    

#### **Routers with Built-In Firewalls**

For many small businesses and home users, the firewall functionality is integrated into the router. This dual-purpose device not only routes traffic between the internal network and the internet but also provides basic firewall protection. This setup is cost-effective and simplifies network management by consolidating multiple functions into a single device.



# All the Layers Working in Unison
[More](https://www.coursera.org/learn/computer-networking/lecture/BqSRb/all-the-layers-working-in-unison)