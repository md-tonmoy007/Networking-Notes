---
module name: Introduction to Connecting to the Internet
src: https://www.coursera.org/learn/computer-networking/home/module/5
tags: 
module: "5"
---
# Introduction to Wireless Networking Technologies
### **1. Introduction to Wireless Networking:**

- **Wireless Networking:** A method of networking that allows devices to connect without the use of physical cables, relying on radio waves to transmit data.
- **Portability:** With the rise of portable devices, wireless networks have become essential in providing mobility and convenience.

### **2. IEEE 802.11 Standards (Wi-Fi):**

- **IEEE 802.11 Standards:** These are a set of specifications that define how wireless networking devices should communicate. Commonly known as Wi-Fi, these standards dictate the technical details of wireless communication.
- **Frequency Bands:** Wi-Fi operates on specific frequency bands, most commonly 2.4 GHz and 5 GHz. These bands are sections of the radio spectrum designated for certain types of communication.
- **Common Standards:** The most widely recognized 802.11 standards include 802.11b, 802.11a, 802.11g, 802.11n, and 802.11ac, each offering improvements in speed, range, and capacity.

### **3. Wireless Network Architecture:**

- **Infrastructure vs. Ad Hoc Networks:**
    - **Infrastructure Networks:** Involve a central access point (AP) that wireless devices connect to. This is the most common setup, especially in home and enterprise networks.
    - **Ad Hoc Networks:** Allow devices to connect directly to each other without the need for a central AP, useful in smaller or temporary setups.
- **Access Points (APs):** Devices that bridge the wireless and wired portions of a network, allowing wireless devices to connect to the wider network and the internet.

### **4. 802.11 Frame Structure:**

- **Frame Control Field:** 16 bits long, it contains sub-fields that determine how the frame should be processed.
- **Duration Field:** Specifies the length of the frame, informing the receiver of the expected listening time.
- **Address Fields:** Four address fields are included in the frame:
    - **Source Address:** The MAC address of the sending device.
    - **Destination Address:** The intended recipient's MAC address.
    - **Receiver Address:** The MAC address of the AP receiving the frame.
    - **Transmitter Address:** The MAC address of the device that transmitted the frame.
- **Sequence Control Field:** Helps in tracking the sequence of frames, ensuring they are processed in the correct order.
- **Data Payload:** Contains the actual data being transmitted.
- **Frame Check Sequence:** Used for error-checking, ensuring the integrity of the transmitted data.

### **5. Wireless Security Protocols:**

- **Wireless Security:** Understanding the basics of wireless security protocols is crucial to protect data and maintain the integrity of the network.

### **Summary:**

Wireless networking, defined by the IEEE 802.11 standards, has become a cornerstone of modern networking, enabling devices to communicate over radio waves rather than physical cables. The use of access points and the structured nature of 802.11 frames ensures efficient data transmission and network management, all while requiring robust security protocols to safeguard the wireless communication.


# Wireless Network Configurations

Wireless networks offer flexibility and scalability in different environments. Here's a quick recap of the types of wireless network configurations:

1. **Ad-Hoc Networks**: 
   - **Direct Communication**: Devices communicate directly with each other without any central infrastructure.
   - **Use Cases**: Ideal for temporary or small-scale scenarios, like sharing files between smartphones or in disaster recovery situations.

2. **Wireless LANs (WLANs)**:
   - **Access Points**: Access points act as intermediaries between wireless devices and the wired network.
   - **Use Cases**: Common in office environments, connecting devices to the Internet via a central router.

3. **Mesh Networks**:
   - **Hybrid Model**: Combines aspects of ad-hoc networks and WLANs, with multiple access points communicating wirelessly and often connected to a wired network.
   - **Use Cases**: Useful for extending the range and performance of a wireless network, especially in large or complex environments.

Each configuration offers unique benefits depending on the network's size, purpose, and the infrastructure available.


# Wireless Channels
![[Pasted image 20240828071007.png]]

### **Understanding Channels**

- **Channels** are smaller sections within a frequency band used by wireless networks.
- **Collision Domains**: In a network, a collision domain is where multiple devices can interfere with each other's transmissions. This causes delays as devices must wait and retransmit data.

### **Role of Channels in Wireless Networking**

- **Wireless Collision Domains**: Unlike wired networks, where switches help isolate collision domains, wireless networks can't rely on physical separation. Channels help by separating the frequency space into distinct segments, reducing the chance of collisions.
- **Frequency Bands**: For Wi-Fi, two common frequency bands are 2.4 GHz and 5 GHz. Each band is divided into multiple channels.
    - **2.4 GHz Band**: Typically ranges from 2.4 GHz to 2.5 GHz. Channels are spaced within this range.
    - **Channel Overlap**: Due to the broad signal width, some channels overlap, causing potential interference.

### **Channel Selection and Congestion**

- **Non-Overlapping Channels**: In the 2.4 GHz band (e.g., 802.11b), channels 1, 6, and 11 are non-overlapping, making them ideal choices to minimize interference.
- **Auto-Sensing**: Modern access points can sense channel congestion and adjust accordingly, either at startup or dynamically.
- **Manual Channel Configuration**: IT professionals may manually set channels to avoid congestion, especially in densely populated areas with many overlapping networks.

### **Why This Matters**

- **Troubleshooting**: Understanding how channels work helps in diagnosing wireless connectivity issues and optimizing network performance.
- **Avoiding Collision Domains**: By strategically selecting channels, you can minimize overlap and reduce the likelihood of collisions, leading to smoother network operation.

In IT support, a solid grasp of channel allocation and management is crucial for optimizing wireless networks, especially in environments with multiple access points and nearby networks.


# Wireless Security
Wireless networking introduces unique security challenges because, unlike wired networks, data is transmitted through radio waves that can be intercepted by anyone within range. To mitigate these risks, various encryption technologies have been developed:

### **Wired Equivalent Privacy (WEP)**

- **Purpose**: WEP was designed to provide the same level of security as a wired connection by encrypting data sent over a wireless network.
- **Encryption Weakness**: WEP uses a 40-bit encryption key, which is now considered very weak. With modern computing power, it can be cracked in just a few minutes, making WEP an outdated and insecure option.
- **Historical Context**: WEP was one of the first encryption standards for wireless networks but is no longer recommended due to its vulnerabilities.

### **Wi-Fi Protected Access (WPA)**

- **Improvement Over WEP**: WPA was introduced to address the weaknesses of WEP, using a stronger 128-bit encryption key, making it more secure and harder to crack.
- **Security Mechanism**: WPA provides better encryption and includes additional security measures like the Temporal Key Integrity Protocol (TKIP) to further enhance data protection.

### **WPA2**

- **Current Standard**: WPA2 is an update to WPA and is currently the most widely used encryption standard for wireless networks.
- **Enhanced Security**: WPA2 uses a 256-bit encryption key, providing significantly stronger protection against attacks. It also uses the Advanced Encryption Standard (AES), which is considered highly secure.

### **MAC Filtering**

- **Access Control**: MAC filtering is a method of securing a wireless network by allowing only devices with specific MAC addresses to connect.
- **Limitations**: While MAC filtering can prevent unauthorized devices from accessing the network, it doesn't encrypt the data being transmitted. This means that someone could still intercept and read the data if they manage to get within range.

### **Key Takeaways**

- **WEP**: Weak and outdated; no longer considered secure.
- **WPA**: A significant improvement over WEP, with stronger encryption.
- **WPA2**: The most secure and commonly used encryption standard today.
- **MAC Filtering**: Adds an extra layer of access control but doesn't protect the data itself.

When securing a wireless network, using WPA2 with a strong password is the best practice, combined with other measures like MAC filtering to enhance overall security.

# WPA3 Protocols & Encryption 

Protocols and encryption are vital components in cybersecurity. Network security continues to evolve along with technological innovations and ever-increasing computing power. You have learned about WPA2 and how it improved the security of the Wi-Fi Protected Access (WPA) protocol. In this reading, you will explore WPA3, the third iteration of WPA wireless security. You will also learn about various internet connectivity technologies, as well as the basics of wireless and cellular networking.

WPA3 is built upon the WPA2 protocol and is intended to replace WPA2. The WPA3 protocol introduces new features and methods to repair the security weaknesses of WPA2. The benefits of this advancement in Wi-Fi security include:

- Simplified wireless security
    
- Stronger authentication 
    
- Powerful encryption 
    
- Stable business continuity
    
- Enhanced security methods
    
- Replacement for legacy protocols
    
- Protected Management Frames (PMF) requirement for enterprise networks
    

WPA3 offers two versions, a personal and an enterprise version.

## WPA3-Personal 

WPA3-Personal is intended for individual users and personal/home Wi-Fi networks. This protocol addresses common cybersecurity weaknesses that affect consumers’ wireless devices. It also simplifies Wi-Fi security for users. The improvements to WPA3-Personal include:

- **Natural password selection:** Gives users the ability to set passwords that are easier for the user to remember. 
    
- **Increased ease of use:** Users do not need to change the way they connect to Wi-Fi to benefit from WPA3’s improved security. 
    
- **Forward secrecy:** If a password is stolen, WPA3 can continue to protect data that is transmitted. 
    
- **Simultaneous Authentication of Equals (SAE)**: WPA3-Personal improves upon the WPA2-Personal Pre-Shared Key (PSK) handshake protocol. SAE uses PSK to generate a Pairwise Master Key (PMK). The PMK uses password-based authentication and is shared between a Wi-Fi access point and a wireless device. The pair use a complex, multi-stage process for proving to one another that they each possess the PMK. This complex handshake makes it extremely difficult for cybercriminals to intercept packets in order to extract an identifiable authentication key. If the SAE transaction is successful, the wireless device will pass the authentication stage and gain access to the secured Wi-Fi network. 
    

The SAE authentication also reduces the probability of successful dictionary and brute force attacks, in which cybercriminals try to crack short, weak, and commonly used passwords. Additionally, SAE corrects a weakness exploited by cybercriminals who could perform key reinstallation attacks (KRACKs) when in close proximity to a Wi-Fi user. This type of attack could decrypt data and expose passwords, credit card information, photos, chats, emails, and more.  

## WPA3-Enterprise

WPA3-Enterprise is intended for business networks with multiple users. This protocol addresses the WPA2-Enterprise weaknesses that cybercriminals have been able to exploit. In addition to the WPA3-Personal SAE improvements, the WPA3-Enterprise security improvements and options include: 

- **Galois/Counter Mode Protocol (GCMP-256):** The Advanced Encryption Standard (AES) with GCMP-256-bit encryption replaces the WPA2 128-bit AES-Counter Mode Protocol (CCMP) Cipher Block Chaining Message Authentication Code (CBC-MAC). GCMP provides data integrity and confidentiality. The GCMP-256-bit encryption strength takes significantly more computing power for cybercriminals to crack than 128-bit encryption. The average person would not have access to that level of computing power. GCMP-256-bit encryption provides a stronger security protocol and makes it harder for cybercriminals to perform Meddler-in-the-Middle attacks. 
    
- **Opportunistic Wireless Encryption (OWE):** OWE improves upon the WPA2 wireless encryption standard of 802.1x Open Authentication and Extensible Authentication Protocol (EAP). In WPA2, EAP required additional support to help it encrypt and authenticate login credentials. In the WPA3 protocol, OWE replaces EAP with a solution that encrypts and authenticates all wireless traffic. It also replaces Wi-Fi passwords by assigning a unique key to each device that has permission to access the network. This technology repairs a weakness Wi-Fi users experience in open networks, which are often found in restaurants, coffee shops, hotels, airports, malls, and more. 
    
- **Wi-Fi Device Provisioning Protocol (DPP):** DPP improves upon the WPA2 Wi-Fi Protected Setup (WPS) encryption technology between wireless devices and routers. WPA3’s DPP uses QR codes or NFC tags to grant passwordless Wi-Fi access to wireless devices.
    
- **384-bit Hashed Message Authentication Mode (HMAC) with Secure Hash Algorithm (SHA):** HMAC creates hash code from a secret key. This hash code is sent with each message passed between a Wi-Fi access point and a user’s device. The hash code from the origin of the message is compared to the hash code from the receiver of the message to determine if the hash codes match. A discrepancy between the two hashes would indicate that the message was compromised or corrupted during transmission.   
    
- **Elliptic Curve Diffie-Hellman Exchange (ECDHE) and Elliptic Curve Digital Signature Algorithm (ECDSA):** In WPA3, key management and authentication use the ECDHE protocol and ECDSA encryption for faster performance. The protocol is supported by most browsers. This key management technology replaces the WPA2 4-way handshake.
    

## Key takeaways

As the tech industry develops more powerful computers, cybercriminals will use them to crack older encryption standards. The need to create more complex encryption algorithms will always be present in order to stay ahead of the evolving tools used by cybercriminals.

For **WPA3-Personal**, some of the new features include:

- Natural password selection
    
- Increased ease of use
    
- Forward secrecy
    
- Simultaneous Authentication of Equals (SAE)
    

For **WPA3-Enterprise**, some of the new features include:

- Galois/Counter Mode Protocol (GCMP-256)
    
- Opportunistic Wireless Encryption (OWE)
    
- Wi-Fi Device Provisioning Protocol (DPP)
    
- 384-bit Hashed Message Authentication Mode (HMAC) with Secure Hash Algorithm (SHA) 
    
- Elliptic Curve Diffie-Hellman Exchange (ECDHE) and Elliptic Curve Digital Signature Algorithm (ECDSA)


# Cellular Networking

Cellular networking, also known as mobile networking, has become an integral part of global communication, providing widespread Internet access and enabling various devices to stay connected on the go. Here's an overview of how cellular networks function and how they compare to other wireless networking technologies:

### **Basics of Cellular Networking**
- **Similarities to Wi-Fi**: Like Wi-Fi (which operates under the 802.11 standards), cellular networks also use radio waves to transmit data. Both have different specifications and operate within specific frequency bands reserved for their use.
- **Frequency Bands**: Cellular networks use radio frequencies that are capable of traveling over longer distances compared to Wi-Fi, often covering many kilometers or miles. This makes cellular networks ideal for broad coverage, especially in areas where wired or Wi-Fi connections are not feasible.

### **Cellular Network Structure**
- **Cells and Cell Towers**: The term "cellular" comes from the network's structure, which is divided into "cells." Each cell is a geographic area served by a cell tower, which handles communications within that cell.
  - **Cell Towers**: These can be thought of as large-scale access points with much greater range than Wi-Fi access points. They broadcast and receive cellular transmissions, facilitating communication between devices within their cell.
  - **Frequency Management**: To avoid interference, each cell is assigned a specific frequency band. Neighboring cells use different, non-overlapping frequency bands, similar to how Wi-Fi channels are managed to prevent overlap and reduce interference.

### **Devices Using Cellular Networks**
- **Diverse Applications**: Initially designed for mobile phones, cellular networks now support a wide range of devices:
  - **Smartphones**: The most common devices on cellular networks, allowing voice calls, texting, and mobile data.
  - **Tablets and Laptops**: Many modern tablets and laptops come with built-in cellular antennas, allowing them to connect to the Internet without relying on Wi-Fi.
  - **Automobiles**: High-end cars often include built-in cellular access for navigation, emergency services, and Internet-based infotainment systems.

### **Differences from Wi-Fi**
- **Range**: Cellular networks cover much larger areas than Wi-Fi networks, which are typically limited to the range of an access point within a building or small outdoor area.
- **Mobility**: Cellular networks are designed to provide seamless connectivity as users move across different cells, maintaining connections over long distances and at high speeds (e.g., while driving).
- **Infrastructure**: Cellular networks require extensive infrastructure, including cell towers, backhaul connections, and sophisticated frequency management, compared to the relatively simple setup of Wi-Fi networks.

### **Key Takeaways**
- **Cellular vs. Wi-Fi**: While Wi-Fi is great for short-range, high-speed communication within a limited area, cellular networks excel in providing wide-area coverage, supporting mobility, and enabling Internet access over large distances.
- **Versatility of Cellular Networks**: From smartphones to cars, cellular networks are becoming increasingly embedded in our daily lives, supporting a wide range of devices and applications. 

Understanding the distinctions between cellular and Wi-Fi networks is crucial for IT professionals who need to design and manage networks that meet diverse connectivity needs.



# Mobile Device Networks


When it comes to mobile devices, there are several types of wireless networks that can be used for communication, each with its specific use cases and potential issues that might arise. As an IT support specialist, understanding these networks and being able to troubleshoot them effectively is crucial. Here's an overview of key points related to wireless networking for mobile devices:

### **Types of Wireless Networks**
1. **Cellular Networks**: 
   - **Use**: Connects mobile devices to the Internet over long distances, typically through 3G, 4G, or 5G networks.
   - **Troubleshooting**: Ensure the cellular radio is enabled. Check signal strength and consider location if connectivity is poor.

2. **Wi-Fi Networks**: 
   - **Use**: Connects devices to the Internet over short distances, typically within a building or public hotspot.
   - **Troubleshooting**: Ensure Wi-Fi is enabled, check for signal strength, and verify the device is connected to the correct network. Be aware of possible Wi-Fi restrictions, like in a coffee shop with limited access.

3. **Bluetooth**:
   - **Use**: Connects devices to peripherals (e.g., headphones, keyboards) over short distances.
   - **Troubleshooting**: Ensure Bluetooth is enabled, check if the devices are paired correctly, and if issues persist, try unpairing and re-pairing the devices.

4. **IoT Network Protocols**:
   - **Use**: Specialized networks for Internet of Things (IoT) devices, often using protocols like Zigbee or Z-Wave.
   - **Troubleshooting**: Ensure the IoT device is within range of the network and correctly configured.

### **Common Troubleshooting Steps**
1. **Check Network Radios**: 
   - Many connectivity issues are due to network radios (e.g., Wi-Fi, Bluetooth) being turned off, often to save battery. Always check that the necessary radios are enabled in the device settings.

2. **Airplane Mode**:
   - **Use**: Disables all wireless communications.
   - **Troubleshooting**: Ensure that Airplane Mode is off if the user wants to connect to any wireless network.

3. **Multiple Connections**:
   - Devices often switch between Wi-Fi and cellular networks based on signal strength, reliability, and cost (e.g., metered cellular data). 
   - **Troubleshooting**: You can manually toggle Wi-Fi and cellular connections to force the device to use a specific network, which might be necessary when dealing with connectivity issues or restricted networks.

4. **Signal Strength and Interference**:
   - Wireless signals weaken with distance and can be affected by physical obstacles or interference.
   - **Troubleshooting**: Ensure the device is within range of the Wi-Fi router or cell tower, and try repositioning the device to improve signal strength.

5. **Bluetooth Pairing**:
   - **Use**: Pairing allows devices to connect and remember each other for future connections.
   - **Troubleshooting**: If pairing fails, ensure both devices are in pairing mode and that Bluetooth is enabled. If problems persist, unpair and re-pair the devices.

### **Key Points to Remember**
- **Network Radios**: The most common cause of connection issues is that network radios (Wi-Fi, Bluetooth, Cellular) are accidentally turned off.
- **Signal Strength**: Wireless performance depends on signal strength and can be influenced by the environment, distance, and interference.
- **Device Settings**: Always check the device settings to ensure proper configuration for the desired network connection.
- **Manual Network Selection**: For troubleshooting, sometimes you need to manually select the network (e.g., switching from Wi-Fi to cellular) to resolve issues.

This knowledge will help you effectively support users who face connectivity issues with their mobile devices, ensuring they can stay connected, whether it's for work or personal use.