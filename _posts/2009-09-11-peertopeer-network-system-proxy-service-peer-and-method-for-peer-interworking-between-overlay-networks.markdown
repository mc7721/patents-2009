---

title: Peer-to-peer network system, proxy service peer, and method for peer interworking between overlay networks
abstract: The present invention relates to a P2P network system. The P2P network system includes: multiple local overlay networks, each comprising multiple proxy service peers; a global overlay network composed of the proxy service peers of all local overlay networks. The proxy service peer is adapted to respond to the request of the requesting peer, query the local overlay network or global overlay network, and return the address information of the requested peer or the requested proxy service peer to the requesting peer. The present invention also relates to a proxy service peer applicable to the foregoing network system, and a method of peer interworking between P2P overlay networks based on the foregoing system. The present invention relieves the load of the proxy service peer, avoids blindness of the requesting peer in selecting the proxy service peer, and achieves load balance between proxy service peers.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08458254&OS=08458254&RS=08458254
owner: Huawei Technologies Co., Ltd.
number: 08458254
owner_city: Shenzhen
owner_country: CN
publication_date: 20090911
---
This application is a continuation of International Application No. PCT CN2007 071238 filed on Dec. 14 2007 which claims priority to Chinese Patent Application No. 200710086485.0 filed on Mar. 13 2007 both of which are hereby incorporated by reference in their entireties.

The present invention relates to a peer to peer network system a proxy service peer and a method for peer interworking between Peer to Peer overlay networks pertaining to the field of network communication.

The Peer to Peer Session Initiation Protocol P2PSIP is a new series of communication protocols currently being formulated by the Internet Engineering Task Force IETF . The P2PSIP is an extension from the Session Initiation Protocol SIP . In essence the Peer to Peer P2P feature is introduced. The client server C S architecture of traditional SIP communication system is discarded. In the C S architecture a central server is depended on to perform user registration authentication routing and searching. Through a P2P overlay network the P2PSIP implements distributed user registration and route locating namely the user s information such as contact information is stored on overlay network peers in a distributed way . The peers that make up a P2P overlay network are all the terminal peers such as user computers which participate in the communication and have certain processing capabilities. This architecture reduces the deployment and maintenance costs for operators and communication costs for users and improves extensibility and robustness of the system.

With the development and application of future networks many independent P2P overlay networks may come forth. Such overlay networks may be constructed based on the specific service network topology geographic location or common interest. The P2P overlay networks independent of each other may need to interwork for example a basic requirement is searching for the location information of a user namely one user in a P2P overlay network hoping to locate a user in another overlay network and originate a call request. Besides the peers in the overlay network may provide other resource and service capabilities for the system service capabilities may also be regarded as a resource for example Network Address Translation NAT traversal service media relay service gateway and streaming media service. Each overlay network provides plenty of resources. In view of the sharing principles of the P2P network the resources may be shared not only in the local P2P overlay network but also in other overlay networks that use the P2P protocol thus a resource overlay network is constituted in a sense. To sum up interworking between overlay networks is one of the important issues to be tackled by the P2P.

In the prior art the essence of the P2P for implementing interworking between overlay networks is each P2P overlay network called local overlay has a P2P proxy service peer. The P2P proxy service peer is a SIP proxy server responsible for routing messages between the local overlay networks. The P2P proxy service peers of all local overlay networks make up an overlay network of a higher layer called global overlay . Each P2P proxy operates two P2P protocol stacks supposing the lower layer P2P algorithm varies between the overlay networks . One protocol stack is for the local P2P overlay network and the other protocol stack is for the global P2P overlay network.

The local overlay network also maintains a P2P proxy candidate list. The members in the list are inactive as P2P proxy candidates. The P2P proxy candidate peers send a HELLO probe message periodically to the P2P proxy service peer to check whether the P2P proxy service peer is working normally. When detecting that the P2P proxy fails a peer in the proxy candidate list is activated automatically incorporated into the global overlay network and registered to be a P2P proxy. If the P2P proxy leaves actively the P2P proxy needs to select a proxy candidate peer as a P2P proxy service peer.

In the prior art of peer interworking between P2P overlay networks the local overlay network has only one P2P proxy service peer. However the P2P network is dynamic enormous peers may access the network anytime and the resources are shared which leads to a heavy load of request tasks to be processed by the proxy service peer. In the local overlay network when the P2P proxy service peer is overloaded other peers serve as only proxy candidates. Therefore the prior art does not make the best of all proxy service resources in the network to balance the load of the proxy service peer.

The objective of the present invention is to overcome the defect of the prior art of peer interworking between P2P overlay networks namely overload of the P2P proxy service peer.

To achieve the foregoing objective a P2P network is provided in an embodiment of the present invention and includes 

The proxy service peer is adapted to respond to a request of the requesting peer query the local overlay network or global overlay network and return the address information of the requested peer or the selected requested proxy service peer to the requesting peer.

To achieve the foregoing objective a proxy service peer is provided in an embodiment of the present invention and includes 

a request responding module adapted to receive a query request from the requesting peer in the P2P network system and send the query request to the proxy selecting module 

the proxy selecting module adapted to determine the address information of the requested peer according to the query request or select a requested proxy service peer and

an information sending module adapted to return the address information of the requested peer or the selected requested proxy service peer to the requesting peer.

To achieve the foregoing objective a method of peer interworking between P2P overlay networks is provided in an embodiment of the present invention and includes the following steps 

by the requesting peer selecting a proxy service peer in the proxy service peer list and sending a query request to the proxy service peer 

sending by the requesting peer after receiving a query response a call request message to the requested proxy service peer selected by the requesting proxy service peer and

setting up by the requesting peer communication according to the address information of the requested peer returned by the requested proxy service peer.

According to the embodiments of the present invention multiple P2P proxy service peers are set in the local overlay network thus the load of the proxy service peer is relieved the response speed of the proxy service peer is increased and the efficiency of utilizing the P2P service peer resources is improved.

The technical solution of the present invention is hereinafter described in detail with reference to accompanying drawings and preferred embodiments.

As shown in a network system in an embodiment of the present invention includes multiple local overlay networks. As shown in each local overlay network includes more than one P2P proxy service peer. In and the proxy service peers are illustrated in black. In the non proxy service peers are illustrated in white. As shown in the network system also includes a global overlay network composed of proxy service peers of all local overlay networks. The proxy service peers are adapted to respond to the request of the requesting peer query the local overlay network or global overlay network and return the address information of the requested peer or the selected requested proxy service peer to the requesting peer.

The local overlay network in this embodiment includes multiple proxy service peers which share the load of a proxy service peer in the prior art. Therefore this embodiment overcomes the defect of overload of the P2P proxy service peer in the prior art of peer interworking between P2P overlay networks.

Moreover the proxy service peer in this embodiment includes the following modules in addition to the functional modules available from the prior art 

a load information calculating module adapted to count the current transactions and calculate the load information and

a load information releasing module adapted to release the load information to the local overlay network and global overlay network where the proxy service peer resides.

In this embodiment the load information is represented by a load factor. The formula for calculating the load factor is load factor quantity of current transactions maximum quantity of processible transactions.

Therefore the requesting peer may select the proxy service peer with a lighter load for providing services according to the load information thus balancing the load between the proxy service peers in the network system. Accordingly each peer in the network system includes 

a service selecting module adapted to select the proxy service peer with the lightest load for providing services according to the load information in the P2P network system.

In this embodiment multiple P2P proxy service peers are set in the local overlay network thus relieving the load of the proxy service peer increasing the response speed of the proxy service peer and improving the efficiency of utilizing the P2P service peer resources. Moreover the proxy service peer may calculate the load factor through a load information calculating module and release the load factor to the local overlay network and global overlay network through a load information releasing module. Therefore when selecting a proxy service peer for providing proxy services the proxy service peer with a lighter load may be selected for providing proxy services by referring to the load information thus further balancing the load between the proxy service peers.

The proxy service peer in this embodiment includes a request responding module a proxy selecting module and an information sending module wherein the request responding module is adapted to receive the query request from the requesting peer in the P2P network system and send the query request to the proxy selecting module the proxy selecting module is adapted to determine the address information of the requested peer according to the query request or select a requested proxy service peer and the information sending module is adapted to return the address information of the requested peer or the selected requested proxy service peer to the requesting peer.

In this embodiment a proxy selecting module for selecting the requested proxy service peer is added in proxy service peer. Therefore for a proxy service peer in a P2P network the requested proxy service peer may be selected to provide services for the requesting peer. Compared with the prior art where a fixed proxy service peer is requested to provide proxy services in this embodiment the load of the proxy service peer is relieved effectively.

a load information calculating module adapted to count the current transactions and calculate the load information and

a load information releasing module adapted to release the load information to the local overlay network where the proxy service peer resides and global overlay network.

a service selecting module adapted to select the proxy service peer with the lightest load for providing services according to the load information in the P2P network system.

Therefore when the proxy service peer selects the requested proxy service peer for providing proxy services the requested proxy service peer with a lighter load may be selected with reference to the load information thus further balancing the load between the requested proxy service peers.

As shown in the method of peer interworking between P2P overlay networks in an embodiment of the present invention includes the following steps 

Step 2 The requesting peer selects a proxy service peer in the proxy service peer list and sends a query request to this proxy service peer 

Step 3 After receiving a query response the requesting peer sends a call request message to the requested proxy service peer selected by the requesting proxy service peer and

Step 4 The requesting peer sets up communication according to the address information of the requested peer returned by the requested proxy service peer.

In this embodiment the proxy service peer list in the local overlay network provides address information which may be IP address information of all proxy service peers and the requesting peer may send a query request such as a Distributed Hash Table DHT query request to obtain the address information of each proxy service peer in the list. Among the proxy service peers in the local overlay network the requesting peer selects one peer as a requesting proxy service peer to provide proxy services. In the global overlay network the requesting proxy service peer queries for the proxy service peer list of the local overlay network where the requested peer resides and selects one proxy service peer as a requested proxy service peer and returns the address information of the requested proxy service peer to the requesting peer. The requesting peer contacts the requested proxy service peer to obtain the address information of the requested peer. Subsequently the requesting peer sets up communication with the requested peer according to the normal session setup process to implement resource sharing or network services for example NAT traversal service media relay service and streaming media service.

The foregoing method is applicable to peers between different local overlay networks. For the peers located in the same overlay network the requesting peer may send a DHT query request directly to obtain the address information of the requested peer and set up a connection without use of any proxy service peer thus eliminating the unnecessary load of the proxy service peer.

Therefore in this embodiment the operations before step 1 include the requesting peer judges whether the requested peer is in the same local overlay network according to the requested peer identifier if the requested peer is in the same local overlay network the requesting peer sends a session request to the requested peer directly otherwise the requesting peer performs step 1.

In this embodiment a DHT algorithm is used as a structured P2P routing algorithm to construct a lower layer P2P overlay network. All proxy service peers included in a local overlay network are registered by using the same public identifier name. In this embodiment the proxy service peers are registered by using the same public Uniform Resource Identifier URI name. For example as shown in all proxy service peers in the local overlay network P2P.org.Pastry are registered by using the public URI name proxy P2P.org.Pastry in the embodiment shown in the time of registration and update of one proxy service peer is independent of that of another . When a client peer needs to search for the proxy service peer this public URI name may be used as a key to search the DHT for the information such as location and load about the registered proxy service peer.

For ease of understanding the process of registration and update of the P2P service peer in this embodiment is described briefly in this way peers P P and P in the local overlay network P2P.org.Pastry are consecutively registered and declared as proxy service peers of the overlay network. The key value pair indicative of the location information URI IP of each peer is stored into the DHT system and updated periodically. The requesting peer queries the DHT by using the URI as a key to obtain the address information of the three proxy service peers and selects one of them as a proxy service peer.

the requesting peer sends a DHT query request by using the Hash value of the public identifier name of the proxy service peer in the local overlay network as a query parameter and

the requesting peer obtains a proxy service peer list of the local overlay network according to the received response.

To further balance the load between all proxy service peers the requesting peer should select the proxy service peer with the lightest load for providing proxy services.

Step 2 includes the requesting peer selects a proxy service peer with the lightest load in the proxy service peer list and sends a query request to this proxy service peer.

Likewise when selecting a requested proxy service peer for the requesting peer the requesting proxy service peer should select the proxy service peer with the lightest load in the P2P proxy service peer list in the local overlay network where the requested peer resides for providing proxy services. Therefore operations included between step 2 and step 3 are as follows 

After receiving the query request from the requesting peer according to the query request the requesting proxy service peer searches for the P2P proxy service peer list in the local overlay network where the requested peer resides 

the requesting proxy service peer selects a proxy service peer with the lightest load in this list as a requested proxy service peer and

the requesting proxy service peer returns the address information of the requested proxy service peer to the requesting peer that sends the query request.

In this embodiment the DHT algorithm is used to construct a lower layer P2P overlay network. Therefore operations included between step 3 and step 4 are as follows 

After receiving the call request message from the requesting peer the requested proxy service peer starts DHT query in the local overlay network where the requested proxy service peer resides and returns the found address information of the requested peer to the requesting peer.

This embodiment is described below taking the call session setup process of a P2P overlay network peer as an example. As shown in supposing peer B sip Bob P2P.org.Pastry in the local overlay network P2P.org.Pastry intends to send a call request to peer A sip Alice pku.edu.kademlia in another local overlay network pku.edu.kademlia before sending the formal call request peer B must obtain the contact address information of peer A first. This information is obtained through a SIP REGISTER message. When the proxy service peer works in the redirection mode the basic message interaction process includes 

First according to the URI of the requested peer A the requesting peer B confirms that it is not in the same P2P overlay network where peer A resides. The User Agent UA of peer B sends a DHT query request through the peer B bound to the UA querying for the proxy service peer list in the local overlay network P2P.org.Pastry a series of SIP messages are included and the query keyword is a Hash value with the input of proxy P2P.org.Pastry . The query result is returned through a SIP response message. The contact field in the response message includes a list of all peers that have registered to provide proxy services in the overlay network. According to the returned query result the proxy service peer with the lightest load is selected for example proxy P in .

Peer B sends a REGISTER query request to proxy P. Through the request URI sip Alice pku.edu.kademlia in the SIP message proxy P determines that peer A is a user of the overlay network pku.edu.kademlia . Proxy P queries for the list of P2P proxy service peers registered by the destination overlay network in the global overlay network. After obtaining the list proxy P selects the proxy service peer with the lightest load value in the overlay network pku.edu.kademlia for example the proxy service peer P in and returns the address information of proxy P to peer B through a SIP redirection message.

Subsequently Peer B sends a REGISTER request message to proxy P. After receiving the message proxy P starts DHT query in the local overlay network pku.edu.kademlia to obtain the address information of user A and returns the address information to B through a SIP message.

Finally peer B sets up communication with peer A directly according to the normal SIP INVITE session process.

It is evident that in the foregoing method of peer interworking between P2P overlay networks in order to balance the load between the proxy service peers selecting a proxy service peer for a call may be based on the load state of each proxy service peer. Blindness in selecting the proxy service peer is avoided. The response speed of the proxy service peer increases. The efficiency of utilizing the P2P service peers and other resources is improved.

Obviously to implement the foregoing functions each P2P proxy service peer needs to release load information regularly or irregularly so that other peers in the overlay network can be aware of its resource load state which serves as a basis for the requesting peer to select a proxy service peer in the future.

In this embodiment the SIP transaction quantity of the proxy service peer is used to reflect the load state. Once receiving a new request message the proxy service peer generates a User Agent Server UAS transaction for it and invokes the DHT query routine. The specific DHT query may be implemented by a corresponding SIP User Agent Client UAC transaction. Finally the DHT query result is returned through the UAC transaction. Although the SIP transaction quantity is not exactly equal to the load it well reflects the load state of the peer and is easily available.

This embodiment uses the load factor to measure the load state of the proxy service peer. Higher values of the load factor of a proxy service peer indicate heavier loads of the proxy service peer. The proxy service peer calculates its load factor periodically and releases it into the network. Therefore the releasing of the load information of the proxy service peer includes the following steps 

calculating the load factor according to this formula load factor quantity of current transactions maximum quantity of processible transactions and

The quantity of current transactions Current Transactions is the quantity of transactions that exist at the reporting time of the proxy service peer and may be obtained through the Application Programming Interface API provided by the SIP protocol stack. The maximum quantity of processible transactions Load High is the maximum quantity of transactions processible by the proxy service peer. Considering the heterogeneousness and difference of the peers in the overlay network the value of Load High varies between different proxy service peers. The Load High of the proxy service peer may be calculated with reference to multiple resources of the peer for example CPU processing capability or network bandwidth. That is the Load High is a output value of a function whose input includes CPU processing capability network bandwidth and other parameters.

In this embodiment the DHT algorithm is used to construct a lower layer P2P overlay network. Therefore the proxy service peer needs to be registered and updated periodically. To improve the network efficiency in this embodiment the proxy service peer releases its load information at the same time of registration and update. The load information may be carried by a new contact parameter such as Load factor and is reported through registration and periodical update of the proxy service peer. It is worthy of emphasis that even if no load information is released the registration and update process is necessary and the load release may be regarded as an incidental process. Compared with the prior art this embodiment does not bring extra network communication pressure.

The process of the proxy service peer releasing its load information at the same time of registering and updating the proxy service peer list in this embodiment includes 

the proxy service peer locates the peer that stores the proxy registration list through the P2P routing algorithm and sends the REGISTER request and load factor to the peer that stores the proxy registration list 

the peer that stores the proxy registration list judges whether itself is responsible for storing the information corresponding to the Hash key of the proxy service peer if yes the peer stores such information otherwise the peer searches the routing table for information about the peer responsible for storing and returns the information to the proxy service peer 

according to the information about the peer responsible for storing the proxy service peer sends a REGISTER request and a load factor to the peer responsible for storing and

the peer responsible for storing accepts the REGISTER request and stores the Hash key of the proxy service peer and the load factor.

Through the foregoing steps in this embodiment the proxy service peer releases its load information at the same time of registration and update.

The proxy service peer needs to synchronize the registration update and load information between the local overlay network and the global overlay network. The registration update and release of load information in the local overlay network are similar to those in the global overlay network except the different overlay network parameter the overlay network parameter is used to describe the identifier of the overlay network and or DHT parameter the DHT parameter is used to describe the P2P algorithm used by the overlay network .

using the public identifier name of the proxy service peer in the local overlay network where the proxy service peer resides as the identifier name of the proxy service peer and

performing Hash calculation for the identifier name of the proxy service peer and using the calculation result as the Hash key of the proxy service peer.

For example in if peer is a proxy service peer in the local overlay network P2P.org.Pastry or this peer is triggered for its own reasons or system reasons and expects to become a proxy service peer the peer stores the key value pair proxy P2P.org.Pastry sip 5 10.0.0.5 into the DHT system where proxy P2P.org.Pastry is the public URI name of the proxy service peer in the overlay network P2P.org.Pastry and sip 5 10.0.0.5 is the address information of peer . While performing registration and update the proxy service peer sip 5 10.0.0.5 stores the load factor as the information corresponding to the Hash key proxy P2P.org.Pastry sip 5 10.0.0.5 into the DHT system.

At the beginning peer does not know onto which exact peer the key value pair should be stored and needs to locate the specific peer responsible for storing namely the peer which stores the key value data actually according to the P2P routing algorithm Pastry . That is in this embodiment peer sends a REGISTER request to peer in the overlay network P2P.org.Pastry according to the routing table defined in the P2P algorithm. According to the Hash proxy P2P.org.Pastry value peer determines that it is not responsible for storing the information corresponding to the Hash key. Therefore peer queries its own routing table and finds that the peer closest to the Hash proxy P2P.org.Pastry value in the Hash space is another peer peer . Peer returns a redirection message to peer telling that the request should be sent to peer . The registration and update request finally arrives at peer responsible for storing. The detailed message is as follows 

When a proxy service is required the requesting peer obtains a proxy service peer list in the specified overlay network through DHT query. The basic process is similar to the process of registration and update of peer except that the initial REGISTER message does not contain contact field. In the final response message peer returns all proxy service peers corresponding to the public service URI which is proxy P2P.org.Pastry in this example through a contact field. For example the final response message of a DHT proxy query request in the overlay network P2P.org.Pastry is as follows 

The contact field includes the details of each proxy service peer including address information time information and load information. The expires parameter indicates the remaining time before expiry of the registration information and the load facor parameter indicates the load information reported by each proxy service peer at the time of the previous registration and update. The requesting peer or proxy service peer selects the proxy service peer with the lightest load namely the proxy service peer expries 100 load facor 0.4 in this embodiment as the next hop peer on the route of the message.

This embodiment releases the load information by using the feature of periodical registration and update of the proxy service peer. It is evident that the load information obtained by the requesting peer through query is not real time and cannot reflect the actual load state at the call request time completely. Specific to this problem as shown in the method for releasing the load information of the proxy service peer in this embodiment may include the following steps additionally for the purpose of optimization 

Step a The proxy service peer updates the quantity of current transactions according to the received query request 

Step b The proxy service peer judges whether the quantity of current transactions reaches the upper threshold or lower threshold if yes the proxy service peer proceeds to step c otherwise to step e 

Step c The proxy service peer judges whether the quantity of current transactions reaches the upper threshold if yes the load factor is set to the maximum factor value otherwise the load factor is set to the minimum factor value 

Step e The query request or call request is processed and the quantity of current transactions is updated.

In this embodiment the upper threshold value may substitute for the maximum quantity of transactions processible by the proxy service peer Load High . Similarly a lower threshold Load Low is defined. Load Low is also represented by the quantity of transactions of the proxy service peer and serves as a reference. Load Low may be a percentage of Load High for example Load Low Load High 40 in this embodiment.

That is before processing the assigned new requests the proxy service peer checks the actual quantity of current transactions first. If the actual quantity of current transactions exceeds Load High the load factor is set to the maximum factor value. For example in this embodiment the value range of the load factor is 0 1 namely the maximum factor value is 1. If the actual quantity of current transactions is less than Load Low the load factor is set to the minimum factor value for example 0.4 in this embodiment a new register and update request and load information are sent immediately and then the request is processed.

In the method of peer interworking between P2P overlay networks in an embodiment of the present invention multiple P2P proxy service peers are set in the local overlay network and one peer is selected for providing proxy services. Compared with the prior art which requests a single proxy service peer to provide proxy services the embodiment of the present invention relieves the load of each proxy service peer increases the response speed of the proxy service peer and improves the efficiency of utilizing the P2P service peer resources. Moreover in this embodiment the load factor of the proxy service peer is calculated and released. Therefore at the time of selecting a proxy service peer for providing proxy services the proxy service peer with a lighter load may be selected with reference to the load factor thus further balancing the load between all proxy service peers. In addition a method for optimizing the load factor is provided in an embodiment of the present invention to make the load factor reflect the load information of the proxy service peer in real time.

The embodiments described above are only preferred embodiments which are not intended to limit the scope of protection of the present invention. It is apparent that those skilled in the art can make various modifications and variations to the invention without departing from the spirit and scope of the invention. The invention is intended to cover the modifications and variations provided that they fall in the scope of protection defined by the following claims or their equivalents.

