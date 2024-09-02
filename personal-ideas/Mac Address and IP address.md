In this blog we will try to understand mac addresses and IP address and how they help us in networking. OK first of all it will be a tip of the ice-berg. I tried to make it as simple as possible for the general people to understand how mac and ip addresses work. Let us first understand what is mac address and what is IP address.

**Mac address:** A MAC address is a globally unique identifier attached to an individual network interface. It's a 48-bit number normally represented by six groupings of two hexadecimal numbers.

**IP address:** An IP address is a string of numbers separated by periods. IP addresses are expressed as a set of four numbers — an example address might be 192.158.1.38. Each number in the set can range from 0 to 255. So, the full IP addressing range goes from 0.0.0.0 to 255.255.255.255.

In simple terms, every networking device has a ID that helps us to identify them globally. This ID is permanent and in every part of the world/network this ID remains the same. This is mac address. On the other hand when we connect to a network using a device, that device is given an ID so that it can be identified from that network. This address isn't permanent and is dependent on the the network we are connected to. 

Another thing to understand to go further is Ethernet frame. To make it simple the data we send using computer networks it goes as a ethernet frame. For example, we can think that of like photon of light (photon as a unit of light, no other characteristics are compared between photon and ethernet frame). IP address and mac address is encapsulated in Ethernet frame so the data knows where to start and where it's destination is.

mac address is  a part of data link layer where IP address is a part of Network layer in networking  (if you don't know protocol layer like data link or network layer you can still go through this blog) . So we need to bridge this two addresses. Here comes the Address Resolution Protocol (ARP). 

**ARP** is a protocol used to discover the MAC (hardware) address of a node that corresponds to a specific IP address. 

So the internet is network of network. To send data we need the ip address of both Start and Destination device. But finding the IP address isn't enough. For example, if you are using a wifi-router for your home network and your mobile and pc/laptop is connected to the same router than try [this website](https://whatismyipaddress.com) to get the IP address of the both devices. 

....did that. Ok, If you did what I said that you will notice that both IP addresses are the same. I can't show my addresses for obvious reason (don't post your public IP addresses online). So in the same Local Network, all the device has same IP address. So we need more information about the device we want to send information/data.  So after finding the IP address we find the mac-address in that network using ARP. Thus finding the device.


``` mermaid
graph TB;
	A;
	B;
```

So if we want to take a anlogy. Think of sending data over the internet as sending a mail. Let us think there are 26 building in a city$B$. Both building has 10 floors. Every floor has some rooms. The room number starts as the floor number. For example a room in 4th floor will start with "4" for example 401, 402 etc. Now  

