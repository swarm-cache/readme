# Concept
A distributed caching mechanism of type key=>value which uses asynchronous websocket connections for delivery. Such system is useful if your intranet setup does not allow connections to a custom caching server from some address pools and you need to extend it to those as well.

Have the following scenario: client C1 can connect to caching server N1, but C2 cannot due to intranet limitations.
![alt text](https://github.com/swarm-cache/readme/blob/main/ss/1.png?raw=true)

With swarm cache you can setup another caching server N2 from an address pool accessible to C2, and connect it to N1. Now N1 and N2 are forming a caching swarm and both C1 and C2 have acces to the same cached key(s)=>value(s)

![alt text](https://github.com/swarm-cache/readme/blob/main/ss/2.png?raw=true)

Ring/celium connections are also supported! Not sure how useful they are but nice to have. A perk of being decentralized :)

![alt text](https://github.com/swarm-cache/readme/blob/main/ss/3.png?raw=true)
![alt text](https://github.com/swarm-cache/readme/blob/main/ss/4.png?raw=true)

