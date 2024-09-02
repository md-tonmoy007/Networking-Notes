---
module name: Introduction to networking
src: https://www.coursera.org/learn/computer-networking/home/module/1
tags: 
module: "1"
---
### 5 layers of TCP/IP network model:
![[Pasted image 20240714162502.png]]

### basic of network device
#### cables:
matierials : coppers and fiber
##### Coppers:
signal is send in two modes (binary data) copper does it with voltage change. Cat5, Cat5e and Cat6
![[Pasted image 20240714163746.png]]
**Crosstalk**: 
![[Pasted image 20240714163825.png]]

##### Fiber: 
uses pulses of light to generate binary signal
Fiber is even sometimes used specifically in environments where there's a lot of electromagnetic interference from outside sources. Because this can impact data being sent across copper wires. Fiber cables can generally transport data quicker than copper cables can, but they're much more expensive and fragile. Fiber can also transport data over much longer distances than copper can without suffering potential data loss. much more expensive and fragile.
#### hubs and switches
 ![[Pasted image 20240714164141.png]]
 A hub is a physical layer device that allows for connections from many computers at once. All the devices connected to a hub will end up talking to all other devices at the same time. It's up to each system connected to the hub to determine if the incoming data was meant for them or to ignore it if it isn't. This causes a lot of noise on the network and creates what's called a collision domain.<mark style="background: #FF5582A6;"> A collision domain</mark> is a network segment where only one device can communicate at a time. If multiple systems try sending data at the same time, the electrical pulses sent across the cable can interfere with each other. This causes these systems to have to wait for a quiet period before they try sending their data again. It really slows down network communications and is the primary reason hubs are fairly rare. 

 ![[Pasted image 20240714164304.png]]
A switch is very similar to a hub, since you can connect many devices to it so they can communicate. The difference is that while a hub is a layer one or physical layer device, a switch is a layer two or data link device. This means that a switch can actually inspect the contents of the ethernet protocol data being sent around the network, determine which system the data is intended for and then only send that data to that one system. This reduces or even completely eliminates the size of collision domains on a network.

<mark style="background: #FF5582A6; color:white;">these devices are used in LAN</mark>
#### routers
![[Pasted image 20240714165201.png]]

<mark class="hltr-red">A core router</mark> usually has many different connections to many other routers. Routers share data with each other via a protocol known as BGP or Border Gateway Protocol. That lets them learn about the most optimal paths to forward traffic.
#### server and clients
- The thing receiving the data is referred to as a client
- he simplest way to think of a server is as something that provides data to something requesting that data.

### Physical Layer
 A bit is the smallest representation of data that a computer can understand. It's a one or a zero.
 A standard copper network cable, once connected to devices on both ends, will carry a constant electrical charge. Ones and zeros are sent across those network cables through a process called modulation. <mark class="hltr-red">Modulation</mark> is a way of varying the voltage of this charge moving across the cable. When used for computer networks, this kind of modulation is more specifically known as line coding.  It allows devices on either end of a link to understand that an electrical charge in a certain state is a zero and another state is a one. Through this seemingly simple technique, modern networks are capable of moving 10 billion ones and zeros across a single network cable every second.

#### Twisted pair cabling and duplexing
 **twisted pair cable**: It's called a twisted pair cable because it features pairs of copper wires that are twisted together. These pairs act as a single conduit for information and their twisted nature helps protect against electromagnetic interference and cross-talk from neighboring pairs.
 A standard<mark class="hltr-red"> Cat six cable </mark>has <mark class="hltr-red">eight wires</mark> consisting of<mark class="hltr-red"> four twisted pairs inside a single jacket.</mark> Exactly how many pairs are actually in use depends on the transmission technology being used. But in all modern forms of networking, it's important to know that these cables allow for duplex communication.
##### Duplex communication:
**simplex:** unidirectional [A -> B (only)]
**Duplex**: bidirectional [A->B, A<-B]
**Full Duplex**: Devices on either side of a networking link can both communicate with each other at the exact same time. This is known as full duplex.
 ![[Pasted image 20240715092010.png]]

#### Ethernet Over Twisted Pair Technologies
An internet connection to a building or home is normally delivered through a coaxial cable and/or fiber-optic cable from an internet service provider (ISP). This connection is fed into a gateway modem located inside the building or home (for home internet customers, this hardware is often provided by the ISP). The modem then passes the internet connection through <mark class="hltr-red">a twisted pair Ethernet cable</mark> to a router or a single computer. The router uses twisted pair Ethernet cables to distribute wired network connections internally to the business or home. These network cables are also called CAT cables. It is possible that you have purchased an Ethernet <mark class="hltr-red">CAT5 or CAT6 </mark>cable for your home internet connection. Some routers also have the capability to provide wireless network connections to the internal network. In addition, Ethernet over twisted pair technologies can also supply <mark class="hltr-red">telephone and television</mark> services to businesses and homes.

#### Twisted pair cables
- telephone and early data cables included two copper wires, one for transmitting data and one for receiving data.This configuration was affected by electromagnetic interference (EMI), radio frequency interference (RFI), and crosstalk between the two copper wires.

**Twisted pair Ethernet cables are commonly used in LANs because:** 
- They offer multiple levels of protection against EMI, RFI, and crosstalk.
- The lower levels of interference protection provide low-cost options, which are generally more accessible to home users and small businesses.  #need-to-know
- The cables are thin, light weight, and malleable enough to install and move easily.
- The transmission range of the cable is suitable for short distance connections inside of buildings and homes. 
- The cable’s frequency range is able to transmit both data and telephone/voice communications.

#####  UTP,  STP, and FTP Ethernet cables
Twisted pair Ethernet cable uses four pairs of color-coded copper wires. Each colored pair, one solid and one striped, are twisted together.

- **Unshielded twisted pair (UTP)** - The most common and least expensive type of Ethernet cable found in business and home networks. UTP cables offer very basic protection against EMI, RFI, and crosstalk interference. 
  
- **Shielded twisted pair (STP)** - Used in environments where electromagnetic interference (EMI), radio frequency interference (RFI), and crosstalk with nearby cables have been identified as a problem for network communications. An STP cable uses a braided aluminum and/or copper shielding to encase the four twisted pairs underneath the outer jacket. 
  
- **Foiled twisted pair (FTP)** - Also used in environments where EMI, RFI, and crosstalk are a problem. An FTP cable uses a thin foil shield that wraps around the bundle of twisted pair wires underneath the outer jacket.


#### Straight-through cable (patch cables)
Straight-through cables can be identified by comparing both ends of the cable with one another. The cable is a straight-through cable if the color and stripe order of the twisted pairs are in the same position on both ends of the cable. In a typical straight-through cable set-up, an orange-striped wire that appears in pin position 1 should also appear at that same position on the other end. This one-to-one pattern is continued for each color in pin positions 2-8. Ethernet cables that use 100Base-T standards (common for home networks) do not use blue and brown cables. Networks using gigabit Ethernet have the option to use blue and brown cables for Power over Ethernet (PoE).

**Straight-through cable key:**

- Computers and routers use:
    
    - Pins 1 & 2 - Orange wires for sending data
        
    - Pins 3 & 6 - Green wires for receiving data 
        
- Hubs and switches use:
    
    - Pins 1 & 2 - Green wires for sending data
        
    - Pins 3 & 6 - Orange wires for receiving data

#### Crossover cables
💡new Enterprise devices have the ability to detect Ethernet connection types and select the correct wires for sending and receiving data using Auto Medium Dependent Interface Crossover (Auto-MDI/MDIX) technology.

Crossover cables are used to connect two computing devices directly to one another. As an IT Support specialist, you might use a short crossover cable to connect an IT administrator laptop directly to an Enterprise machine (e.g., server, switch, router, hub, etc.). This type of connection is normally used to update, repair, and perform other administrative tasks on the Enterprise machine. A crossover cable should be connected between the <mark class="hltr-red">Ethernet port/Network Interface Card (NIC)</mark> on the IT administrative system and the management port of the Enterprise machine. This connection is then used to access the operating system and/or the management interface of the Enterprise machine. Additionally, crossover cables can connect two switches, two hubs, or a switch to a hub, as well as two routers, two PCs, or a router to a PC.

**Crossover cable key:**

- Endpoint 1 of the Ethernet cable:
    
    - Pins 1 & 2 - Green wires for sending data
        
    - Pins 3 & 6 - Orange wires for receiving data 
        
- Endpoint 2 of the Ethernet cable:
    
    - Pins 1 & 2 - Orange wires for sending data
        
    - Pins 3 & 6 - Green wires for receiving data
#### Network Ports and Patch Panels
![[Pasted image 20240715100003.png]]
![[Pasted image 20240715100024.png]]
A <mark class="hltr-red">patch panel</mark> is a device containing many network ports, but it does no other work. It's just a container for the endpoints of many runs of cable. Additional cables are then generally ran from a patch panel, to switches or routers to provide network access to the computers at the other end of those links.

#### Cabling tools
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/RFTwIFuWSWW6RQ-7NRtshw_e99f1e919b8d41deba6a2065a580a3f1_image.png?expiry=1721174400000&hmac=YzUsxXEDHJ-LZ7lC3uQwVBvAgZxRPdxNKe8G5mYuqTg)

## Crimper

 A crimper is a hand-held tool that looks like a set of pliers. It is used to squeeze down or crimp wires.
   
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/7Te8SaZRREaaRB9cijed8A_ad3d5af4f2fc47fb885282f7114835f1_image.png?expiry=1721174400000&hmac=g3_w62jxXOQ-9b5CY3tz1h80WO1SUh1makgVVF2N84A)

## Cable Stripper

 A cable stripper is another handheld device that also looks like pliers. It's purpose is to remove the protective rubber coating from cables.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/ZCLMQxR-Scuq8TFqB3_tGQ_c94b6a4336a143179e0814d32b2846f1_image.png?expiry=1721174400000&hmac=SZpdQ32RGSRyI31yREWeG5i4Lnjbg0Skjx-C6_Ul_cI)

## Wi-Fi Analyzer

 A WiFi analyzer is a scanner that analyzes the power and quality of the WiFi in an area. It also collects data about the WiFi and its circumstances.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/3f7qWhG7Rkqv9c0nLEfTvA_986ab5ec6dfc45c6be4ba606d299faf1_image.png?expiry=1721174400000&hmac=I2v-033TU9RkUI6x9e3BtU0YzzJUx5KYCTdnvJNwgj8)

## Toner Probe

 A toner probe is a part of a set of devices that are used for finding ethernet and other internet connectors. One device plugs into a cable, while the other device, the tone probe, uses a tone which gets louder as it gets closer to the device plugged into the cable. (Meyers, 2022). 

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Dqi4CCl9RX6mUkvBE_Nvgg_1fb1f003e3424d07ba7dfadc754938f1_image.png?expiry=1721174400000&hmac=xjc-qkO7Ec-a50sE5E2MBkBoOGvIEHOP66HqqMV4wIc)

## Punch Down Tool

A Punch Down Tool or Krone Tool is used for punching down wires into punch down panels or jacks. First the protective covering is taken off the wires, then the wires are punched into place.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/p9_MR7iES_-No0TcGj5chQ_bfed17df9e39418f8e64e5268c471bf1_image.png?expiry=1721174400000&hmac=RBSFlP_9z0vXh9D5Rtk47ei-5OiFmCtMJWyNSC4tynI)

## Cable Tester

 A cable tester digitally measures integrity of the cable for compliance with developed cabling standards. They measure several parameters:

- Attenuation
    
- Impedance
    
- Noise
    
- Near-End Crosstalk
    
- Attenuation to Crosstalk Ratio (ACR)
    
- PowerSum NEXT (Network Encyclopedia, 2022).
    

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/tRZTR2KRRj2QevserlvNpQ_def846c3c0e648409849f75482df6cf1_image.png?expiry=1721174400000&hmac=Rn2uTK5ulvduv39_D0sm2h7e4jDI0r4A0ibqhs8IpuI)

## Loopback Plug

A loopback plug is a device that tests ports. Wires are connected in a loop that sends traffic back to the port after it receives it.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/PJXCGDqoS92AioOqSl360A_f8a2553e62184114b9d7f496385ec5f1_image.png?expiry=1721174400000&hmac=Kcrj_-Xz1EPOM6mxD0UznBC4kq-6ixzzO0xI8_NVtN0)

## Network Tap

 A network tap is a device that copies traffic information for use in monitoring devices. It is an external device.

# Ethernet and MAC Addresses

One of the primary purposes of this layer is to essentially abstract away the need for any other layers to care about the physical layer and what hardware is in use. By dumping this responsibility on the data link layer, the internet transport and application layers can all operate the same no matter how the device they're running on is connected.

If two computers were to send data across the wire at the same time, this would result in literal collisions of the electrical current representing our ones and zeros, leaving the end result unintelligible. Ethernet as a protocol solve this problem by using a technique known as carrier sense multiple access with collision detection. Doesn't exactly roll off the tongue. We generally abbreviate this to CSMA CD. CSMA CD is used to determine when the communications channels are clear and when the device is free to transmit data. The way CSMA CD works is actually pretty simple. If there's no data currently being transmitted on the network segment, a node will feel free to send data. If it turns out that two or more computers end up trying to send data at the same time, the computers detect this collision and stop sending data. Each device involved with the collision then waits a random interval of time before trying to send data again. This random interval, helps to prevent all the computers involved in the collision from colliding again the next time they try to transmit anything. 

When a network segment is a collision domain, it means that all devices on that segment receive all communication across the entire segment. This means we need a way to identify which node the transmission was actually meant for. This is where something known as a media access control address or MAC address comes into play.

A MAC address is a globally unique identifier attached to an individual network interface. It's a 48-bit number normally represented by six groupings of two hexadecimal numbers.

 A MAC address is split into two sections. The first three octets of a MAC address are known as the organizationally unique identifier or OUI. These are assigned to individual hardware manufacturers by the IEEE or the Institute of Electrical and Electronics Engineers.
 ![[Pasted image 20240716090916.png]]
 **Ethernet uses MAC addresses to ensure that the data it sends has both an address for the machine that sent the transmission, as well as, the one that the transmission was intended for.** 

# Unicast, Multicast, and Broadcast

**Unicast**: one to one device,
```
If the least significant bit in the first octet of a destination address is set to zero, it means that ethernet frame is intended for only the destination address.
```

**Multicast:**
 If the least significant bit in the first octet of a destination address is set to one, it means you're dealing with a multicast frame. A multicast frame is similarly set to all devices on the local network segment. What's different is that it will be accepted or discarded by each device depending on criteria aside from their own hardware MAC address. Network interfaces can be configured to accept lists of configured multicast addresses for these sorts of communications
 
**Broadcast:**
In ethernet, broadcast is sent to every single device on a LAN. This is accomplished by using a special destination known as a broadcast address. The ethernet broadcast address is all F's. Ethernet broadcasts are used so that devices can learn more about each other.

# Dissecting an Ethernet Frame
![[Pasted image 20240716091610.png]]

Data packets at the Ethernet level are known as <mark class="hltr-red">Ethernet frames</mark>. An Ethernet frame is a highly structured collection of information presented in a specific order.

![[Pasted image 20240726101747.png]]
**Preamble:** A preamble is eight bytes or 64 bits long, and can itself be split into two sections. The first seven bytes are a series of alternating ones and zeros. These act partially as a buffer between frames and can also be used by the network interfaces to synchronize internal clocks they use to regulate the speed at which they send data. This last byte in the preamble is known as the **SFD**, or **start frame delimiter**. This signals to a receiving device that the preamble is over and that the actual frame contents will now follow.

After the SFD comes the **Destination mac address** (This is the hardware address of the intended recipient)

**Ether-type:** this are used to describe protocols.

**VLAN:** VLAN stands for virtual LAN. It's a technique that lets you have multiple logical LANs operating on the same physical equipment.

**Payload:** A payload in networking terms is the actual data being transported, which is everything that isn't a header.

**Checksum:** This is a four-byte or 32-bit number that represents a checksum value for the entire frame. This checksum value is calculated by performing what's known as a cyclical redundancy check against the frame. A cyclical redundancy check, or CRC, is an important concept for data integrity and is used all over computing, not just network transmissions. A CRC is basically a mathematical transformation that uses polynomial division to create a number that represents a larger set of data. Anytime you perform a CRC against a set of data, you should end up with the same checksum number. The reason it's included in an Ethernet frame is so that the receiving network interface can infer if it received uncorrupted data.
