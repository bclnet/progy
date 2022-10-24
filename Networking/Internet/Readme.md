# Internet

- computer data interchange with scale
- every network interface (NIC) has a MAC address which is like a telephone number
- an addressing system needs to be made
- every home has a street address, but some cities are denser then others, also some addresses are to apartment buildings.
- IP address uses a mask to make flexible subnetworks, and a PORT is added to identify which apt with in an address is trying to be reached.
[IP packet](http://www.laneye.com/network/ethernet-network-packet-holding-an-ip-packet.gif)


### PACKET
data as bytes needs to be sent. its chopped up into smaller chunks of data and wrapped with information. these are called packets.
packets usually hold other packets inside of them. 


### ETHERNET PACKET
Can only send to other devices on its own network. Each device has a MAC address.
Ethernet packet is Receiver MAC, Sender MAC, Number of bytes, then data.


### ARP TABLE
theres a small table of known Mac addresses for IP addresses. If IP address not in table, then broadcast request for anyone who owns IP address is made. owning card replays and ARP table is updated.


### IP PACKET

- IP packet has some flags, a Sender IP, Receiver IP, then data. Sits inside an Ethernet packet.
- three parts required for transport: IP address, Mask, and default gateway.
- IP address is network address that is MASK-ed to find a NetworkID and NodeID.
- example IP: 169.192.1.3 + Mask: xxx.xxx.x.o => Net: 169.192.1 & Node: 3;

Conversation.
- Fake Mask: ROOM-NAME + Fake Address: Kitchen-John, Kitchen-Gretchen, Kitchen-Sam, LivingRoom-George, LivingRoom-Sam, Bathroom-George.
- sender takes mask and apples to receivers address
- Kitchen-Gretchen wants to talk to Kitchen-John.  Masks and both are in kitchen, knows can talk in same room. looks up MAC in ARP table, adding as needed, and sends Packet to John.
- Kitchen-Gretchen wants to talk to Bathroom-George. Masks and George is not in kitchen. sends to gateway. looks up MAC in ARP table, adding as needed, and sends to Gateway.
- Gateway works like a runner who stands at the door of your room. if you are having a conversation you know who is in the room with you, you might not know where someone else is. If you need to talk with them you can make a note and hand it to the guy at the door.  The guy at the door knows about all the rooms on the floor, and will get it to the right room on that floor, unless its on a different floor, then it sends to his floor runner. who will deal with it. etc.


### PORT
once it gets to a destination there might be different reasons for the conversation. a port allows a small subdivision of the address you are trying to reach. just like suites in a corporate building or apartment numbers in an apartment building.


### TCP/UDP
TCP and UDP packets has Send port, Receiver port, some flags, then data.
packets are not guaranteed to arrive, and when they do they will probably be out of order. UDP packets are connectionless, and are the simplest packet, with ports and data, but are unreliable. TCP packets setup a connection, and have guaranteed data constancy by including some window and retry logic to only give you the data once it has been received in order, but at the potential lost of time.
UDP is good for streamed data, where some error is not a problem. Internet radio
TCP is good for full fidelity transmissionstions, required for file transfers for instance.


### HUMAN HELPERS
IP address are numbers and not human friendly.
- DNS is a network service which translates a name to a number, so we as humans don't need to remember the numbers. also adds a layer of abstraction, allowing the numbers to change with out affecting how we reference them.
Every device has to configure an IP, mask, and default gateway. Along with address of DNS servers.
- DHCP is a network service which will hand out leases of address, and auto configure network devices with given information. Auto-registration. 