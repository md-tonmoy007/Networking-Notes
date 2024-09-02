---
module name: Troubleshooting and the Future of Networking
src: https://www.coursera.org/learn/computer-networking/home/module/6
tags: 
module: "6"
---
# Name resolution tool
### **Key Concepts and Summary**

1. **Name Resolution**:
   - Critical for translating human-readable domain names into IP addresses that computers use to communicate on the internet.
   - Typically handled automatically by the operating system, but manual resolution can be valuable for troubleshooting.

2. **nslookup Command**:
   - A versatile tool available on Linux, Mac, and Windows for performing DNS lookups.
   - **Basic Usage**: 
     - `nslookup <hostname>` returns the IP address associated with the specified hostname.
     - Example: `nslookup twitter.com` retrieves the A record for twitter.com, displaying the IP address.

3. **Interactive Mode**:
   - Activated by running `nslookup` without any hostname.
   - **Features**:
     - **Multiple Queries**: Allows running multiple DNS queries in sequence.
     - **Custom DNS Server**: By typing `server <address>`, you can specify a different DNS server for the queries.
     - **Query Record Types**: Use `set type=<record type>` to query different DNS record types like MX, CNAME, or TXT.
     - **Debug Mode**: `set debug` shows detailed information about the DNS resolution process, including response packets and TTL values.

4. **Advanced Troubleshooting**:
   - **Server Selection**: Useful for diagnosing issues related to specific DNS servers or verifying the consistency of DNS records across servers.
   - **Record Types**: Helps in troubleshooting email delivery (MX records), domain aliasing (CNAME records), and other domain-specific configurations.
   - **Debug Output**: Provides deep insights into the DNS resolution process, helping identify issues like stale cache entries or incorrect DNS settings.

### **Summary**
Understanding and using the `nslookup` command is crucial for IT support specialists, as it allows for direct interrogation of DNS servers to resolve domain names into IP addresses. The tool's interactive mode and advanced features provide significant flexibility and detail for troubleshooting complex DNS issues, making it an essential part of the network troubleshooting toolkit.


# Public DNS Servers
### **Key Concepts and Summary**

1. **Importance of DNS in Networks**:
   - DNS is crucial for translating domain names into IP addresses, enabling devices to communicate over the internet.
   - ISPs typically provide access to recursive name servers, which are sufficient for most internet communications.
   - Businesses often run their own DNS servers to manage internal resources and resolve internal hostnames.

2. **DNS Service Models**:
   - **ISP-Provided DNS**: Most common and typically used for general internet access.
   - **Internal DNS Servers**: Necessary for resolving internal hostnames and managing resources within an organization.
   - **DNS as a Service (DNSaaS)**: Increasingly popular, where third-party providers manage DNS services.

3. **Public DNS Servers**:
   - **Usage**: Can be used for troubleshooting or as a backup DNS option if internal or ISP-provided DNS servers fail.
   - **Examples**:
     - **Level 3 Communications**: Historically popular IPs (4.2.2.1 through 4.2.2.6) are widely used, though not officially acknowledged by the company.
     - **Google Public DNS**: Officially recognized and easy to remember, with IPs 8.8.8.8 and 8.8.4.4.

4. **Testing DNS Functionality**:
   - Using public DNS servers can help diagnose name resolution issues.
   - Public DNS servers are accessible globally and often respond to ICMP echo requests, making them useful for testing general internet connectivity with tools like `ping`.

5. **Security Considerations**:
   - When using public DNS servers, ensure they are operated by reputable organizations to avoid the risk of DNS hijacking and malicious redirection.
   - Prefer using DNS servers provided by your ISP for regular use, reserving public DNS for specific troubleshooting scenarios.

### **Summary**
DNS plays a vital role in network functionality, enabling the translation of domain names to IP addresses. While ISPs generally provide the necessary DNS services, businesses may run internal DNS servers, and DNS as a Service (DNSaaS) is also gaining popularity. Public DNS servers, such as those from Level 3 Communications and Google, offer a reliable option for troubleshooting or as a backup, but users should exercise caution to ensure security. Testing DNS functionality with tools like `ping` can help resolve connectivity issues and ensure the network is running smoothly.


