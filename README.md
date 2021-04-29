## Concept
A distributed caching mechanism of type key=>value which uses asynchronous websocket connections for delivery. Such system is useful if your intranet setup does not allow connections to a custom caching server from some address pools and you need to extend it to those as well.

Have the following scenario: client C1 can connect to caching server N1, but C2 cannot due to intranet limitations.
![alt text](https://github.com/swarm-cache/readme/blob/main/ss/1.png?raw=true)

With swarm cache you can setup another caching server N2 from an address pool accessible by C2, and connect it to N1. Now N1 and N2 are forming a caching swarm and both C1 and C2 have acces to the same cached key(s)=>value(s)

![alt text](https://github.com/swarm-cache/readme/blob/main/ss/2.png?raw=true)

Ring/tree connections are also supported! Not sure how useful they are but nice to have. A perk of being decentralized :)

![alt text](https://github.com/swarm-cache/readme/blob/main/ss/3.png?raw=true)
![alt text](https://github.com/swarm-cache/readme/blob/main/ss/4.png?raw=true)

## The Node
Nodes are the core of swarm cache. They receive, store, transmit, sync data.
Amid other nodes/clients a node can do 3 things:
- Act as server for clients, meaning listening for incoming client connections and messages. Clients communicate asynchronously with nodes and can send commands to access/modify data.
- Act as server for other nodes, meaning listening for incoming node connections and messages. Nodes communicate asynchronously with each other to access/modify data.
- Connect to other nodes and do the above point.

2 or more connected nodes form a "swarm". A swarm shares the data (key=>value) present across all nodes without it being duplicated. That is: data remains stored in one node, but is accessible by all the others regardless of node's position in the network (linear, tree, ring, etc)

## The Client
Clients are modules which get/set/delete data upon swarm. Can be any software/hardware application which supports standard websocket connections. They only connect to nodes.
