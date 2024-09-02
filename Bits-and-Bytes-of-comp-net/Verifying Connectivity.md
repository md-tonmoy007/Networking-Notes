---
module name: The Bits and Bytes of Computer Networking
src: https://www.coursera.org/learn/computer-networking/home/module/6
tags: 
module: "6"
---
# Ping: Internet Control Message Protocol

### **Key Concepts and Summary**

1. **Network Connectivity Issues**:
   - The most common network problem is the inability to establish a connection, whether to a server, website, or external resources. Diagnosing these issues is a crucial part of network troubleshooting.

2. **ICMP (Internet Control Message Protocol)**:
   - ICMP is used by routers or remote hosts to communicate network errors back to the source of problematic traffic.
   - ICMP packets consist of a header with type, code, and checksum fields, along with a data payload that helps identify the transmission that caused the error.

3. **Ping Tool**:
   - Ping is a command-line tool that uses ICMP to check if a destination is reachable on the network by sending echo request messages and receiving echo replies.
   - The tool provides output on the round-trip time, TTL (Time to Live), and packet size, and is available on all major operating systems.

4. **Usage of Ping**:
   - On Linux and macOS, ping runs continuously until interrupted, while on Windows, it sends four echo requests by default.
   - Various command-line flags can be used to modify ping's behavior, such as the number of requests, packet size, and timing.

### **Summary**
This lesson covers the importance of diagnosing network connectivity issues, introducing ICMP as a protocol used to report network errors. The **ping** tool, which utilizes ICMP, is explained as a fundamental tool for checking network reachability and diagnosing issues. Understanding these concepts and tools is essential for effective network troubleshooting.



# Traceroute
### **Key Concepts and Summary**

1. **Ping vs. Traceroute**:
   - While **Ping** determines if a specific computer can be reached and provides information on the connection quality, **Traceroute** helps identify the specific points (hops) where issues occur in the communication path.

2. **Traceroute Utility**:
   - **Traceroute** identifies the path between two network nodes by manipulating the TTL (Time to Live) field in IP packets.
   - It sends multiple packets with incrementing TTL values, forcing each router in the path to return an ICMP time-exceeded message, thereby revealing its position in the chain.

3. **Traceroute Output**:
   - The output includes the hop number, round-trip time for three packets, and the IP address or hostname of each router along the path.
   - On Linux and macOS, Traceroute uses UDP packets, while on Windows, it uses ICMP echo requests (under the command `tracert`).

4. **Advanced Tools: mtr and pathping**:
   - **mtr** (Linux/macOS) and **pathping** (Windows) are advanced tools that provide real-time and aggregate data, respectively, about the Traceroute process over time. 
   - mtr updates the output continuously, while pathping runs for a set period and then displays the results.

### **Summary**
This lesson introduces Traceroute, a powerful tool for diagnosing network path issues by revealing each hop between two nodes. The lesson also covers how Traceroute differs from Ping and introduces mtr and pathping as enhanced tools for monitoring network paths over time. Understanding these tools is crucial for effective network troubleshooting, especially in identifying specific network segments causing connectivity issues.


# Testing port connectivity
### **Key Concepts and Summary**

1. **Testing Connectivity at the Transport Layer**:
   - While network layer tools like Ping and Traceroute are essential, sometimes it's necessary to check if services at the transport layer (e.g., TCP/UDP ports) are functioning correctly.

2. **Netcat (Linux/MacOS)**:
   - **Command**: `nc <host> <port>`
   - **Basic Functionality**: Attempts to establish a connection to a specified port on a host.
   - **Usage**:
     - **Interactive Mode**: If the connection succeeds, it allows you to manually send application layer data.
     - **Zero Input/Output Mode (`-z`)**: Used for simple port status checks.
     - **Verbose Mode (`-v`)**: Provides human-readable output, showing whether the port is open or closed.

3. **Test-NetConnection (Windows)**:
   - **Command**: `Test-NetConnection -ComputerName <host> -Port <port>`
   - **Basic Functionality**: Tests connectivity to a specified port on a host, similar to Netcat but with additional features.
   - **ICMP Echo Request**: If only the host is specified, it performs a ping-like test but provides more detailed output, including data link layer information.

4. **Advanced Usage**:
   - Both **Netcat** and **Test-NetConnection** are versatile tools with many advanced features beyond simple port checking. They can be used for scripting, network troubleshooting, and even as lightweight servers.

### **Summary**
This lesson introduces powerful tools for testing connectivity at the transport layer: **Netcat** for Linux/macOS and **Test-NetConnection** for Windows. These tools help you verify whether specific ports on remote hosts are accessible, and they offer additional functionality for deeper network troubleshooting. While the lesson covers basic usage, both tools have extensive capabilities worth exploring for advanced network diagnostics.