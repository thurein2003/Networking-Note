|| **MAC and IP** ||
Usually a host send a message to the devices when that know that IP address and Mac address of that devices. But sometimes a host must send a message in it only know the IP address of the destination device.

***
There are 2 types of primary address assigned to a device on the Ethernet LAN;
1. Physical address (The Mac address)
2. Logical address (The IP address)
***
**The Layer 2 Ethernet frame contains the following:**

Destination MAC address – This is the simplified MAC address of PC2, 55-55-55.
Source MAC address – This is the simplified MAC address of the Ethernet NIC on PC1, aa-aa-aa.
The Layer 3 IP packet contains the following:

Source IPv4 address – This is the IPv4 address of PC1, 192.168.10.10.
Destination IPv4 address – This is the IPv4 address of PC2, 192.168.10.11.
***
**Summary**
***
MAC and IP
Sometimes a host must send a message, but it only knows the IP address of the destination device. The host needs to know the MAC address of that device. The MAC address can be discovered using address resolution. There are two primary addresses assigned to a device on an Ethernet LAN:

		- Physical address (the MAC address) – Used for NIC-to-NIC communications on the same Ethernet network.
		- Logical address (the IP address) – Used to send the packet from the source device to the destination device. The destination IP address may be on the same IP network as the source, or it may be on a remote network.
When the destination IP address (IPv4 or IPv6) is on a remote network, the destination MAC address will be the address of the host default gateway (i.e., the router interface). Routers examine the destination IPv4 address to determine the best path to forward the IPv4 packet. When the router receives the Ethernet frame, it de-encapsulates the Layer 2 information. Using the destination IPv4 address, it determines the next-hop device, and then encapsulates the IPv4 packet in a new data link frame for the outgoing interface. Along each link in a path, an IP packet is encapsulated in a frame. The frame is specific to the data link technology that is associated with that link, such as Ethernet. If the next-hop device is the final destination, the destination MAC address will be that of the device Ethernet NIC.

***
Broadcast Containment
A message can only contain one destination MAC address. Address resolution lets a host send a broadcast message to a unique MAC address that is recognized by all hosts. The broadcast MAC address is a 48-bit address made up of all ones. MAC addresses are usually represented in hexadecimal notation. The broadcast MAC address in hexadecimal notation is FFFF.FFFF.FFFF. Each F in the hexadecimal notation represents four ones in the binary address.

When a host sends a broadcast message, switches forward the message to every connected host within the same local network. For this reason, a local area network, a network with one or more Ethernet switches, is also referred to as a broadcast domain.

If too many hosts are connected to the same broadcast domain, broadcast traffic can become excessive. The number of hosts and the amount of network traffic that can be supported on the local network is limited by the capabilities of the switches used to connect them. To improve performance, you may need to divide one local network into multiple networks, or broadcast domains. Routers are used to divide the network into multiple broadcast domains.

On a local Ethernet network, a NIC only accepts a frame if the destination address is either the broadcast MAC address, or else corresponds to the MAC address of the NIC. Most network applications rely on the logical destination IP address to identify the location of the servers and clients. How does the sending host determine what destination MAC address to place within the frame? The sending host can ARP to discover the MAC address of any host on the same local network.

ARP uses a three-step process to discover and store the MAC address of a host on the local network when only the IPv4 address of the host is known:

The sending host creates and sends a frame addressed to a broadcast MAC address. Contained in the frame is a message with the IPv4 address of the intended destination host.
Each host on the network receives the broadcast frame and compares the IPv4 address inside the message with its configured IPv4 address. The host with the matching IPv4 address sends its MAC address back to the original sending host.
The sending host receives the message and stores the MAC address and IPv4 address information in a table called an ARP table.
IPv6 uses a similar method known as Neighbor Discovery.

***