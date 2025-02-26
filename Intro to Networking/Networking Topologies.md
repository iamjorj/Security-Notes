- An arrangement of physical and or logical connection of devices in a network
- computers are hosts, such as clients and servers that use this network
- transmission medium layout used to connect devices is the physical topology part of the network
	- cabling plan
	- node position
	- connections between nodes and cabling 
- logical topology is how the signals will act on the network media, or how data will be transmitted 


Network topology can be divided into 3 areas


# 1. Connections

| Wired connections    | Wireless connections |
| -------------------- | -------------------- |
| Coaxial cabling      | Wifi                 |
| Glass fiber cabling  | Cellular             |
| Twisted pair cabling | Satellite            |
| and more             |                      |
# 2. Nodes - Network Interface Controllers (NIC)
- Repeaters
- Hubs
- Bridges
- Switches
- Router
- Modem
- Gateways 
- Firewall

# 3. Classifications

- topology is like the structure of a network
- form does not have to correspond to the actual physical arrangement of devices in the network
- therefore topologies can be either physical or logical


### Types
- Point-to-point
- Bus
- Star
- Mesh
- Ring
- Tree
- Hybrid
- Daisy Chain
more complex types can be built by combining the topologies above

## Point to Point

![point to point](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_p2p.png)
- physical link exists between 2 hosts
- therefore these 2 devices can communicate
- basic model of traditional telephony
- must not be confused with peer to peer (p2p) architecture
## Bus
![bus](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_bus.png)

- all hosts are connected via a transmission medium (e.g. coaxial cable)
- no central network component
- only one host can send, everyone else can only receive and determine whether the data is intended for them
## Star
![star](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_star.png)

- network component maintains a connection to all hosts
- host connected to central network component with a separate link (router, switch, hub)
- data traffic of the central network component is very high since all data goes through it

## Ring
![ring](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_ring.png)
- for the physical ring topology, hosts are connected to the ring with 2 cables, one for incoming signals, one for outgoing signals
- does not require an active network component
- control and access to transmission medium are regulated by a protocol

- for the logical ring topology, a distributor at the node simulates the ring by forwarding from one port to the next, and it's quite similar to the star topology
- information is transmitted in one direction around the ring
- transmission medium is accessed using a token from the retrieval system

## Mesh

![mesh](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_mesh.png)
(partially meshed)
- connections are done on a physical level, routing is done on a logical level
- two types: fully meshed and partially meshed
- fully meshed
	- every host is connected to every other host
	- primarily used in WAN to ensure high reliability and bandwidth
	- if one router fails, the other routers are connected to everything else anyway so it can pick up the slack
- partially meshed
	- endpoints connected by one connection
	- some nodes are connected by only one connection, while others are connected to two or more other nodes using point to point

## Tree
![tree](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_tree.png)

- extended star topology
- has local networks, useful for when multiple topologies are combined
- often used by businesses
- both logical and physical tree topologies exist
- used for broadband networks and MAN (municipal)

## Hybrid
![hybrid](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_hybrid.png)
- combines multiple topologies
- formed when the connection of topologies do not create any standard topologies
- tree connected to tree is still tree (exception)

## Daisy Chain
![daisy](https://academy.hackthebox.com/storage/modules/34/redesigned/topo_daisy-chain.png)

- it's a chain of connections wow
- often found in automation tech