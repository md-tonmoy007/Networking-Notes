---
module name: Network Services
src: https://www.coursera.org/learn/computer-networking/home/module/4
tags: 
module: "4"
---


# What is DNS?
The Domain Name System (DNS) is a global, distributed network service that translates human-readable domain names (like `www.weather.com`) into machine-readable IP addresses (like `184.29.131.121`). This process is known as **DNS resolution**. Without DNS, users would need to remember and input numerical IP addresses for every website they visit, a task that's far more cumbersome than using easily memorable domain names.

#### **The Role of DNS in Website Management**

One of the powerful features of DNS is its ability to handle changes in IP addresses behind the scenes. For example, if a website like `weather.com` moves its web server to a new data center, the DNS records can be updated to point the domain name to the new IP address. This change is seamless to the end-user, who can continue using the same domain name without interruption.

#### **Global DNS and Geographic Routing**

DNS also plays a crucial role in optimizing web traffic by routing users to servers that are geographically close to them. This is important because, although internet data travels extremely fast, the physical distance between the user and the server can affect speed and latency. To enhance user experience, especially for global websites, DNS can be configured to direct users to the nearest data center.

For instance:

- A user in **New York** visiting a website may be directed to a server located in New York or nearby.
- A user in **New Delhi** may be directed to a server located in or near New Delhi.


# Deep Dive into DNS: How Domain Name Resolution Works

#### **The Role of DNS Servers**

DNS servers are essential components in a network's configuration. For a computer (or any device) to function effectively on a network, several configurations need to be set up, including:

- **IP Address**: The unique address of the device on the network.
- **Subnet Mask**: Defines the network's range and helps in routing traffic.
- **Gateway**: The access point that routes traffic from the local network to other networks.
- **DNS Server**: The server responsible for resolving domain names into IP addresses.


#### **Types of DNS Servers**

There are five primary types of DNS servers, each playing a specific role in the name resolution process:

1. **Caching Name Servers**: These servers temporarily store DNS query results to speed up future queries.
2. **Recursive Name Servers**: These servers perform the full DNS resolution process by querying other DNS servers on behalf of the client.
3. **Root Name Servers**: The starting point for DNS queries, directing them to the appropriate Top-Level Domain (TLD) servers.
4. **TLD Name Servers**: These handle the top-level domains (e.g., `.com`, `.org`) and direct queries to the correct authoritative name servers.
5. **Authoritative Name Servers**: These servers provide the final answer to a DNS query, giving the IP address associated with a domain name.

#### **How DNS Resolution Works** (caching and recursive name servers)

Let’s break down the DNS resolution process using an example where two friends on the same network both want to visit `www.facebook.com`:

1. **Initial Request**: When your friend enters `www.facebook.com` into their browser, their computer needs to know the IP address associated with that domain. The computer sends a query to the local DNS server (configured as a recursive name server) on the network.
    
2. **Recursive Query**: Since the local DNS server doesn’t have the IP address in its cache, it performs a recursive resolution. This process involves contacting several DNS servers to retrieve the correct IP address.
    
3. **Caching**: Once the local DNS server obtains the IP address, it stores it in its cache and sends it back to your friend’s computer.
    
4. **Subsequent Request**: A few minutes later, when you enter `www.facebook.com` into your browser, your computer queries the same local DNS server. Since the server already has the IP address cached, it immediately returns the IP address without performing a full lookup.


#### **Time to Live (TTL)**

DNS records come with a **Time to Live (TTL)** value, which dictates how long a DNS server can cache a record before discarding it and performing a new resolution. TTLs vary widely:

- **Short TTLs (few minutes to hours)**: Common today due to faster internet speeds and more frequent changes in IP addresses.
- **Long TTLs (up to a day or more)**: Were more common in the past when bandwidth was limited, and minimizing DNS traffic was essential.





#### **Full Recursive Resolution**

When a local recursive server needs to perform a full DNS resolution, the process involves several key steps:

1. **Contacting Root Name Servers**: The recursive server first queries one of the 13 root name servers. These root servers are not just 13 physical servers but rather 13 authoritative services distributed globally via [Anycast](https://cloudflare.com/learning/cdn/glossary/anycast-network/)—a technique that routes traffic to the nearest available server based on location, congestion, or link health.
    
2. **Querying TLD Name Servers**: The root server responds by directing the query to the appropriate TLD name server (e.g., `.com` for `www.facebook.com`). The TLD server then provides the address of the authoritative name server for the specific domain.
    
3. **Querying Authoritative Name Servers**: The recursive server finally contacts the authoritative name server, which provides the exact IP address of the domain.
    
4. **Returning the Result**: The IP address is returned to the local DNS server and then to the original client, completing the resolution process.


#### **Local DNS Caching**

To further optimize performance, most devices, from smartphones to desktop computers, maintain a local DNS cache. This local cache stores the IP addresses of recently queried domain names, reducing the need to contact the local DNS server for every new connection.


## More about DNS
- [howdnsworks ep 1](https://howdns.works/ep1/)
- [cloudflare dns blog](https://www.cloudflare.com/learning/dns/what-is-dns/)
- [a medium blog on dns](https://medium.com/@a-dem/how-dns-works-cd1d3a587a31)
- [youtube video on dns](https://www.youtube.com/watch?v=Ah7fYex6Ups)


# DNS vs UDP

this [video](https://www.coursera.org/learn/computer-networking/lecture/81nwU/dns-and-udp) explains this really good. watch this. 

# Name Resolution in Practice
## Resource Record Types
Understanding DNS in detail is crucial for troubleshooting and managing network issues effectively. A key aspect of DNS is its use of **resource record types**. These records define the data structure within DNS and are used to translate domain names into IP addresses, route email, and even handle various services. Let’s dive into some of the most commonly used DNS resource record types.

#### **1. A Record (Address Record)**

- **Purpose**: The A record is the most fundamental DNS record, used to map a domain name to an IPv4 address.
- **Example**: If `www.microsoft.com` has an A record pointing to `192.0.2.1`, entering `www.microsoft.com` into a browser will direct the user to that IP address.
- **Multiple A Records**: A domain can have multiple A records, which is often used for **DNS Round Robin** load balancing. For example, `www.microsoft.com` might have A records for `10.1.1.1`, `10.1.1.2`, `10.1.1.3`, and `10.1.1.4`. When a DNS resolver queries this domain, it cycles through these IPs to distribute traffic.

#### **2. AAAA Record (Quad A Record)**

- **Purpose**: Similar to the A record but used for IPv6 addresses.
- **Example**: `www.example.com` might have an AAAA record that points to `2001:0db8:85a3:0000:0000:8a2e:0370:7334`, which is an IPv6 address.

#### **3. CNAME Record (Canonical Name Record)**

- **Purpose**: A CNAME record is used to alias one domain name to another. This is useful for redirecting traffic or simplifying DNS management.
- **Example**: If `microsoft.com` has a CNAME record pointing to `www.microsoft.com`, any request to `microsoft.com` will automatically be redirected to `www.microsoft.com`.
- **Advantage**: The primary benefit of using a CNAME is that it centralizes the management of IP addresses. If the IP address changes, only the A record for the canonical name (`www.microsoft.com`) needs to be updated.

#### **4. MX Record (Mail Exchange Record)**

- **Purpose**: The MX record specifies the mail servers responsible for receiving email on behalf of a domain.
- **Example**: `example.com` might have an MX record pointing to `mail.example.com`, which is the domain's mail server.
- **Priority**: MX records often include a priority value, determining the order in which mail servers should be contacted. Lower numbers indicate higher priority.

#### **5. SRV Record (Service Record)**

- **Purpose**: SRV records are used to define the location (hostname and port number) of servers for specific services.
- **Example**: An SRV record might be used to define the location of a `CalDAV` service for calendaring, directing traffic to `caldav.example.com:8008`.

#### **6. TXT Record (Text Record)**

- **Purpose**: Initially intended to store human-readable text, TXT records are now often used to convey machine-readable data. This includes verification data for email services, domain ownership, and security configurations.
- **Example**: A TXT record might be used to store an SPF (Sender Policy Framework) entry for a domain, helping to prevent email spoofing.

#### **7. NS Record (Name Server Record)**

- **Purpose**: NS records indicate which name servers are authoritative for a domain. They are essential for the delegation of DNS zones.
- **Example**: `example.com` might have NS records pointing to `ns1.example.com` and `ns2.example.com`, indicating these servers are responsible for handling DNS queries for the domain.

#### **8. SOA Record (Start of Authority Record)**

- **Purpose**: The SOA record provides information about the DNS zone, including the primary name server, the email of the domain administrator, the domain serial number, and timers for refreshing the zone.
- **Example**: The SOA record for `example.com` might include details like the primary name server (`ns1.example.com`) and contact information for the administrator (`admin@example.com`).

## Anatomy of a Domain Name
#### **1. Top-Level Domain (TLD)**

- **Definition**: The TLD is the last part of a domain name. In `www.google.com`, the TLD is `.com`.
- **Purpose**: TLDs categorize domains into various types and are the highest level in the DNS hierarchy.
    - **Common TLDs**: These include `.com`, `.net`, `.edu`, and others that you're likely familiar with.
    - **Country-Specific TLDs**: These are associated with specific countries, like `.de` for Germany or `.cn` for China.
    - **Vanity TLDs**: As the internet has expanded, so has the variety of TLDs, including niche ones like `.museum` and `.pizza`.
- **Governance**: TLDs are administered by **ICANN** (Internet Corporation for Assigned Names and Numbers), a non-profit organization that also oversees the global DNS system in partnership with the **IANA** (Internet Assigned Numbers Authority).

#### **2. Domain**

- **Definition**: The domain is the second part of the domain name, right before the TLD. In our example, `google` is the domain.
- **Purpose**: The domain name represents the specific name under the TLD, typically chosen by an individual or organization. It is where control moves from the TLD name server to an authoritative name server.
    - **Registration**: Domains can be registered through a registrar, a company authorized by ICANN to sell unregistered domain names.
    - **Example**: In `www.google.com`, `google` is the domain name registered under the `.com` TLD.

#### **3. Subdomain**

- **Definition**: The subdomain is the part before the domain name, like `www` in `www.google.com`.
- **Purpose**: Subdomains are used to organize different sections of a domain and can refer to specific services, like `mail.google.com` for Google's email service.
    - **Flexibility**: Subdomains can be freely chosen by the domain owner and do not need to be registered separately.
    - **Structure**: You can have multiple levels of subdomains, such as `subdomain.domain.com`, though it's rare to see more than a few levels.

#### **Fully Qualified Domain Name (FQDN)**

- **Definition**: An FQDN includes the complete domain name, consisting of the subdomain, domain, and TLD. For example, `www.google.com` is an FQDN.
- **Purpose**: The FQDN uniquely identifies a specific location in the DNS hierarchy.
- **Technical Limits**: DNS can support up to 127 levels of domain names within a single FQDN, with each section limited to 63 characters, and the entire FQDN not exceeding 255 characters in length.
### Summary

Together, these components—TLD, domain, and subdomain—make up the full structure of a domain name. The FQDN is a complete address that guides internet traffic to the correct destination, whether it's a website, email server, or other services. Understanding this hierarchy is crucial for anyone working in IT, as it underpins much of the functionality of the modern internet.


# DNS Zones

#### **1. DNS Zones**

- **Definition**: A DNS zone is a portion of the DNS namespace for which an authoritative name server is responsible. Each zone contains information about a specific portion of the DNS structure, including resource records that map domain names to IP addresses or other data.
- **Hierarchy**: DNS zones are hierarchical, with different levels of authority:
    - **Root Zone**: Managed by root name servers, the root zone is at the top of the hierarchy and oversees the entire DNS namespace.
    - **TLD Zones**: These are managed by TLD name servers, responsible for specific top-level domains (e.g., `.com`, `.net`).
    - **Domain-Level Zones**: These are managed by authoritative name servers for individual domains, like `google.com`.
- **No Overlap**: Zones do not overlap; each is independently managed. For example, the `.com` TLD zone doesn't include the `google.com` domain; its authority stops at the `google.com` authoritative name server.

#### **2. Purpose of DNS Zones**

- **Ease of Management**: As domains grow, managing a large number of DNS records within a single zone can become complex and error-prone. Zones allow network administrators to break down domain configurations into smaller, more manageable pieces.
    - **Example**: A large company with the domain `largecompany.com` could create separate zones for different offices (e.g., `la.largecompany.com`, `pa.largecompany.com`, and `sh.largecompany.com`). This segmentation reduces complexity and allows for more localized management of DNS records.

#### **3. Zone Files**

- **Definition**: Zone files are configuration files that define the contents of a DNS zone. They include all the necessary resource records for that zone.
- **Key Components**:
    - **SOA Record (Start of Authority)**: Every zone file must contain an SOA record, which declares the zone's authority and identifies the primary authoritative name server for that zone.
    - **NS Records**: These records specify additional name servers that can also serve the zone. This ensures redundancy and reliability.
    - **Resource Records**: The zone file includes various resource records like A, Quad A, CNAME, MX, and others, each serving different purposes in DNS resolution.
    - **TTL (Time to Live)**: The default TTL value in a zone file determines how long DNS records are cached by resolvers.

#### **4. Multiple Servers and Redundancy**

- **Redundancy**: It's common to have multiple physical servers (with different FQDNs and IP addresses) responsible for the same DNS zone. This ensures that if one server fails, others can continue to handle DNS queries without interruption.

#### **5. Deep Hierarchies**

- **Subdomains and Zones**: Just as subdomains can be nested several levels deep, DNS zones can also be configured in a multi-level hierarchy. However, in practice, it's rare to see zones with more than a few levels of depth.

#### **6. Reverse Lookup Zones**

- **Purpose**: Reverse lookup zones allow DNS resolvers to query an IP address and receive the corresponding FQDN in return. This is the opposite of the usual DNS query, which resolves a domain name to an IP address.
- **PTR Records**: The primary record type in reverse lookup zone files is the PTR (Pointer) record. PTR records map an IP address back to a domain name.

### Summary

DNS zones are an essential aspect of the DNS infrastructure, enabling efficient management of DNS records at various levels of the DNS hierarchy. By breaking down DNS configurations into zones, administrators can better manage and maintain large networks, ensuring the reliability and scalability of domain name resolution. Understanding how zones and zone files work is crucial for anyone involved in network management and DNS administration.