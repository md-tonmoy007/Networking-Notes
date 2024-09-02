---
module name: Introduction to Connecting to the Internet
src: https://www.coursera.org/learn/computer-networking/home/module/5
tags: 
module: "5"
---
# What is broadband
### Key Concepts:

1. **Broadband Definition**: Refers to any internet connectivity technology that is faster than dial-up and offers always-on connections.
2. **Impact of Broadband**: Revolutionized both business and home internet use, enabling the full potential of the internet to be realized.
3. **Business Adoption**: Businesses were early adopters of broadband, often using T-carrier technologies due to the need for higher bandwidth.
4. **Home Use Expansion**: As the internet grew more complex, home broadband use became necessary to handle larger data transfers, like images and multimedia.
5. **Technological Evolution**: Without broadband, modern internet activities like streaming, sharing media, and online education would not be feasible.
6. **T-carrier and Other Broadband Solutions**: T-carrier technologies are still used in businesses due to their reliability, though other broadband options are available for both business and consumer use.

### Summary:
Broadband, encompassing any non-dial-up internet technology, offers faster and always-on connections, transforming how businesses and home users interact with the internet. Initially adopted by businesses due to their higher bandwidth needs, broadband later became essential for home users as the internet evolved to include more complex content. This shift allowed for activities like streaming and online education, which would be impossible with dial-up. While T-carrier technologies remain in use for their reliability, a variety of broadband solutions now cater to both business and consumer demands.

### See more
[more](https://investopedia.com/terms/b/broadband.asp)



# T-Carrier Technologies
 
1. **T-carrier Technology Origins**: Invented by AT&T to carry multiple phone calls over a single cable using the T1 specification.
2. **T1 Specification**: Allows up to 24 phone calls or data channels over twisted pair copper, each channel at 64 kbps, summing up to 1.544 Mbps.
3. **Repurposing for Data**: Initially for phone calls, T1 technology was later used for data transfer, evolving to represent any 1.544 Mbps connection.
4. **Usage Evolution**: Initially used for telecom company interconnections, T1 lines became popular in the 1990s for business internet connectivity.
5. **Multiplexing and T3 Lines**: Multiple T1 lines can be multiplexed to form a T3 line, which has a throughput of 44.736 Mbps.
6. **Current Use**: T-carrier technologies have been largely replaced by cable broadband, fiber connections, and other modern broadband solutions for both businesses and ISP communications.

### Summary:

T-carrier technologies, developed by AT&T, were designed to transmit multiple phone calls over a single copper line using the T1 specification. This technology, which originally supported 24 channels each at 64 kbps (totaling 1.544 Mbps), was later adapted for data transfer. While T1 lines were once prevalent for connecting telecom sites and businesses, they have largely been replaced by more cost-effective and faster broadband technologies like cable and fiber optics. Multiplexing T1 lines to form T3 lines provided higher throughput, but modern broadband solutions have superseded these older technologies.


# Digital Subscriber Lines
### Key Concepts:

1. **Public Telephone Network for Internet Access**: Initially used for dial-up connections, leveraging existing infrastructure.
2. **Digital Subscriber Line (DSL)**: Enhanced technology allowing simultaneous voice calls and data transfer by using different frequency ranges.
3. **DSL Modems (DSLAMs)**: Digital Subscriber Line Access Multiplexers used to establish and maintain data connections over phone lines.
4. **ADSL (Asymmetric Digital Subscriber Line)**: Offers different speeds for download and upload, typically faster downloads suited for home users.
5. **SDSL (Symmetric Digital Subscriber Line)**: Provides equal speeds for both upload and download, formerly used by businesses but now also for home users.
6. **High-bitrate DSL (HDSL)**: An advanced DSL technology providing speeds above 1.544 Mbps.
7. **DSL Variations**: Numerous minor variations exist, with specifics best obtained from ISPs.

### Summary:
The public telephone network, initially used for dial-up Internet connections, was optimized with DSL technology to allow simultaneous voice and data transmission. DSL operates on different frequency ranges than voice calls, with DSLAMs managing long-running connections. Two main types of DSL are ADSL, which offers faster download speeds and slower uploads (ideal for home users), and SDSL, which provides equal speeds for both uploads and downloads (more common among businesses but increasingly used by home users). Advancements include HDSL, which exceeds the speed of traditional DSL. Various DSL technologies offer different bandwidths and operational ranges, with detailed information often provided by ISPs.

# Cable Broadband
### Key Concepts:

1. **Communication Evolution**: Initially, all communications were wired, but recent trends favor wireless traffic. Conversely, television started with wireless broadcasts and transitioned to wired (cable) delivery.
2. **Cable Television Origins**: Developed in the late 1940s to extend TV access to remote areas, leading to widespread adoption after the 1984 Cable Communications Policy Act.
3. **Cable Broadband Development**: Leveraging existing coaxial cables, originally used for TV, cable companies began offering high-speed internet by using frequencies that didn't interfere with TV broadcasts.
4. **Shared Bandwidth Model**: Cable internet uses a shared bandwidth model, where multiple users share the same bandwidth until the signal reaches the ISP's core network, which can result in slower speeds during peak usage times.
5. **Central Office (CO) vs. Cable Modem**: DSL and dial-up connect directly to a CO, guaranteeing bandwidth, while cable internet uses a cable modem that connects to a Cable Modem Termination System (CMTS), which manages multiple connections to the ISP's core network.
6. **Network Upgrades**: Most cable operators have upgraded networks to reduce the impact of shared bandwidth, but congestion can still occur during high usage periods.

### Summary:

Communication technologies have evolved from wired to increasingly wireless systems, while television has followed the opposite path, transitioning from wireless broadcasts to wired cable. Cable television, initially developed to extend TV access to remote areas, expanded rapidly after deregulation in 1984. This same infrastructure was later adapted to provide high-speed internet through cable broadband, which operates on a shared bandwidth model. Unlike point-to-point connections like DSL, cable internet's shared nature can lead to slower speeds during peak times. Cable internet connections are managed by cable modems that link to a Cable Modem Termination System (CMTS), which connects to the ISP's core network. Despite network upgrades, bandwidth sharing remains a characteristic of cable internet.



# Fiber

### Key Concepts:

1. **Fiber Optics in Internet Core**: Fiber is the preferred technology in the core of the Internet due to its high speeds and ability to transmit data over long distances without signal degradation.
2. **Fiber vs. Copper**: Fiber uses light for data transmission, allowing it to cover greater distances than copper, which relies on electrical signals.
3. **FTTX (Fiber to the X)**: A general term for various fiber deployments closer to end-users, where "X" represents different points of termination.
   - **FTTN (Fiber to the Neighborhood)**: Fiber reaches a neighborhood cabinet, with copper or coaxial cable covering the last leg to homes.
   - **FTTB (Fiber to the Building/Business/Basement)**: Fiber reaches a building or business, with internal connections typically using copper.
   - **FTTH (Fiber to the Home)**: Fiber is run directly to individual residences.
   - **FTTP (Fiber to the Premises)**: A broader term encompassing both FTTH and FTTB.
4. **Optical Network Terminator (ONT)**: The device that serves as the demarcation point in fiber networks, converting fiber network data to formats compatible with traditional twisted pair copper networks.

### Summary:

Fiber optic technology, essential for the high-speed backbone of the Internet, uses light to transmit data over long distances without degradation, making it superior to copper cables, which are limited by electrical signal range. Although fiber was initially used only in ISP core networks and data centers due to cost, it's increasingly being deployed closer to end-users. This trend is captured by the term FTTX, where "X" indicates various points of fiber termination, such as the neighborhood (FTTN), building (FTTB), or home (FTTH). The Optical Network Terminator (ONT) is the key device in fiber setups, translating fiber-optic data for use over traditional copper networks.