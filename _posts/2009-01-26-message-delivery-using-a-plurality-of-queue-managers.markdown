---

title: Message delivery using a plurality of queue managers
abstract: A method and system for message delivery in a messaging network are provided for enabling scaling. A messaging network includes a group of a plurality of queue managers, each of which includes means for carrying out a method comprising: receiving a message at a queue manager, removing at least some of the original message data to form a link message, adding a reference to the link message referring to the queue manager, sending the link message to a link message queue, and putting the original message to a local queue on the first queue manager. A link message queue may provided on each of the queue managers in the group, or single link message queue may be provided on one queue manager and accessible by the other queue managers in the group.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07979497&OS=07979497&RS=07979497
owner: International Business Machines Corporation
number: 07979497
owner_city: Armonk
owner_country: US
publication_date: 20090126
---
This invention relates to the field of message delivery. In particular the invention relates to scaling in messaging networks.

Message delivery in messaging networks such as clusters of queue managers have a problem in scaling as when load balancing is used a client has no control over which one of multiple queue managers a message request is put. Load balancing is used to send messages to any one of the queue managers in a messaging network. This has the problem that a request for a specific message by another client must be made to the same queue manager otherwise the client is left hanging.

This problem particularly manifests itself in the environment of HTTP hypertext transfer protocol in messaging. The HTTP environment traditionally relies on horizontal scaling. An HTTP client puts a message onto a queue manager on a first machine. The client had no say as to which machine their put request went to because the HTTP requests were load balanced around the server by an edge server. A second HTTP client then does a request for the message however the edge server may send this request to a different queue manager and so the second HTTP client is left hanging.

According to a first aspect of the present invention there is provided a method for message delivery in a messaging network having a group of a plurality of queue managers the method comprising receiving a message at a first queue manager removing at least some of the original message data to form a link message adding a reference to the link message referring to the first queue manager sending the link message to a link message queue and putting the original message to a local queue on the first queue manager.

The method may also include receiving a request to retrieve a message at a second queue manager in the group checking the local queue of the second queue manager for the message checking the link message queue of the second queue manager and if a link message is found retrieving the message from the queue manager referenced in the link message.

According to a second aspect of the present invention there is provided a computer software product for message delivery the product comprising a computer readable storage medium storing in a computer in which program comprising computer executable instructions are stored which instructions when executed by a computer perform the following steps receiving a message at a first queue manager removing at least some of the original message data to form a link message adding a reference to the link message referring to the first queue manager sending the link message to a link message queue and putting the original message to a local queue on the first queue manager.

According to a third aspect of the present invention there is provided a computer software product for message delivery the product comprising a computer readable storage medium storing in a computer in which program comprising computer executable instructions are stored which instructions when executed by a computer perform the following steps receiving a request to retrieve a message at a queue manager in a group of queue managers checking a local queue of the queue manager for the message checking a link message queue of the queue manager and if a link message is found retrieving the message from a queue manager referenced in the link message.

According to a fourth aspect of the present invention there is provided a system for message delivery comprising a messaging network including a group of a plurality of queue managers that execute on a plurality of processors each queue manager including a local queue each of the queue managers including means for creating a link message by removing at least some of the original message data from a received message and adding a reference to the link message referring to the queue manager at which the message has been received and means for sending the link message to a link message queue accessible by all the queue managers in the group.

The subject matter regarded as the invention is particularly pointed out and distinctly claimed in the concluding portion of the specification.

It will be appreciated that for simplicity and clarity of illustration elements shown in the figures have not necessarily been drawn to scale. For example the dimensions of some of the elements may be exaggerated relative to other elements for clarity. Further where considered appropriate reference numbers may be repeated among the figures to indicate corresponding or analogous features.

In the following detailed description numerous specific details are set forth in order to provide a thorough understanding of the invention. However it will be understood by those skilled in the art that the present invention may be practiced without these specific details. In other instances well known methods procedures and components have not been described in detail so as not to obscure the present invention.

Referring to a system is provided in a messaging network having multiple horizontal messaging or queue managers for example in a cluster . Queue managers provide a logical container for the message queues and are responsible for transferring data to other queue managers via message channels. However other forms of message managers may be used.

A message put by a messaging client is put to a queue on one of the queue managers . This queue may be selected by a load balancing mechanism .

A message support means is provided coupled to or integral to the queue manager . The support means may take various forms as described further below and may be a one to one relationship between the support means and a queue manager or there may be one support means for multiple queue managers or there may be multiple support means for a single queue manager . The support means generates a link message to the message and sends the link message to a special type of queue for the other horizontal queue managers . The special type of queue may be referred to a cluster queue.

The described system can apply to horizontally scaled messaging networks. Horizontal scaling is provided with one queue manager per machine and IP spraying or name aliasing is carried out at the load balancing mechanism . The described system can also apply to vertically scaled messaging networks in which there is more than one queue manager per vertically scaled machine.

In one embodiment shown in the cluster queues A A for the other queue managers to which the link message is sent are provided on each of the cluster s queue managers . The cluster queue managers also have their own local queues . Similarly the first queue manager may also have a cluster queue A for use if a message is received to one of the other queue managers . A reference is made in the link message as to the queue manager where the message actually resides.

The link message may be sent by the support means to the cluster queues A A by a put request. Alternatively the link message may be sent by the support means to the cluster queues A A by publishing the linked message on a well known topic in a publish subscribe manner. Each queue manager subscribes on the topic and puts the message to its local cluster queue A A.

In another embodiment shown in the cluster queues B B for the queue managers may be provided as a single queue or multiple queues B B on the first queue manager . The support means of the other queue managers have access to the cluster queue or queues B B.

The link message contains only a subset of the original message . It is preferable to reduce the size of the link message in order to reduce network flow. The reference in the link message residing on the cluster queues provides a more optimistic get scenario.

When a client wishes to retrieve a message by a get request the get request is sent to any one of the queue managers in the cluster . The support means for the queue manager to which the get request has been sent checks its local queue for the message . This check may be based on message header properties or on a CorrelationID of the message .

If the local queue on the queue manager does not contain the message the support means then checks the cluster queue of the queue manager to which the get request has been sent. Again this check may be based on message header properties or on a CorrelationID of the message . If a link message to the message is found on a cluster queue the reference in the link message can be followed to retrieve the message from the queue where it is on another queue manager .

The link message may contain sufficient information for queue managers to have message selectors. Message selectors for example in JMS Java Message Service Java is a trade mark of Sun Microsystems Inc. work on certain key attributes of a message and therefore it may be preferable to place at least enough information in the link message on the cluster queues such that queue managers can make selections. This enables a specific message to be retrieved.

The described system can also be extended to non specific gets without a selector where the remote cluster queue s will always be checked for messages if none exist on the local queue. If the link message contains basic information for example that there is a message on a particular queue this would enable the client to simply request any message rather than a specific message indicated by an identifier.

In order to maintain performance it is desirable to reduce the number and size of messages flowing around the messaging system. To reduce the number of messages flowing around the messaging system the function of providing a link message to the cluster queues may be enabled for only particular queues and topics. An administrator may be provided to selectively enable the function of providing a link message after checking the queues and topics.

An embodiment of the system is described in the environment of HTTP messaging networks. Referring to shows a block diagram of an HTTP messaging network and shows the same diagram with a message flow illustrated.

The HTTP messaging network is shown with a first HTTP client which puts a message to the messaging network and a second HTTP client which wishes to get the message put by HTTP client . HTTP servlets act as a communications bridge between the HTTP environment and the messaging environment. If a message has been put to a queue within a cluster of messaging managers by an HTTP client any messaging or queue manager within that cluster should be able to see the message for easy message retrieval by HTTP clients.

An edge or proxy server load balances the HTTP requests made by clients to the HTTP servlets which are connected to the queue managers to distribute requests across multiple machines . A client has no option as to which machine the put request goes to.

Each machine in the HTTP messaging network hosts a queue manager which provide a logical container for the message queues and are responsible for transferring data to other queue managers via message channels.

The described system can apply to horizontally scaled HTTP messaging networks. In an HTTP messaging network horizontal scaling is provided with one HTTP server per machine and IP spraying or name aliasing is carried out at the edge server. The described system can also apply to vertically scaled HTTP messaging networks in which there is more than one server per machine. For example two HTTP servers may be provided on a machine with for example two processors and name aliasing is done by the edge server.

The HTTP messaging network function relies on all HTTP client requests passing through an instance of a HTTP servlet where the support is implemented sitting on an HTTP server in front of a queue manager . A link message is generated to a message put onto its local queue . The link message contains a subset of the information contained in the message including a reference to the location of the message. The link message may be generated by the HTTP servlet or the queue manager .

The queue managers in addition to their regular queues have special queues for holding the link messages to messages on other queue manager s queues . As described in relation to the special queues for holding the link messages may be provided on the queue manager in which the message is put with access from the other queue manager or on the other queue manager itself.

When a message is put to a queue of a queue manager a corresponding link message is placed on all other queue managers that are taking part in the horizontal cluster. The link message is put or published to a special queue for example named HTTP.CLUSTER.QUEUE.

When a message is requested using HTTP the HTTP request goes to any HTTP servlet and thus through to a queue manager connected to the HTTP servlet. Thus the request is received at any queue manager within the cluster according to whatever selection method is being used workload balancing round robin etc . The HTTP servlet that has the request firstly looks on its local queue for the message. If it is not there then it attempts to find the message on the special queue HTTP.CLUSTER.QUEUE .

If the link message is found on the special queue the reference in the link message is followed to retrieve the full message from its queue on a different queue manager .

Using this system means that no changes need be made to the queue managers as the logic is all held within the HTTP servlets. It is a non invasive way of addressing a potentially very invasive problem. It does not rely on any kind of client to queue manager affinity.

Referring to an example of this process is illustrated by numbered arrows in the figure. A message arrives on a first queue manager QM destined for a queue on QM via HTTP server . QM is part of a two queue manager cluster with a second queue manager QM .

Upon receiving the message HTTP support residing on HTTP server strips out the original data and replaces it with a reference to its local queue manager QM . For example an XML message that reads . This shortened link message is put on to all the HTTP.CLUSTER.QUEUES in the cluster. In this case it is put to the HTTP.CLUSTER.QUEUE on QM . The original message is then placed onto the queue on QM .

A request comes into QM for a message for example with message header properties or with a specified CorrelationID from a different client. The local queue on QM is checked by HTTP support on HTTP server . The message is not found. The HTTP server support then checks its local or remote HTTP.CLUSTER.QUEUE for the message link which it finds. The message link is read and HTTP server makes a remote request to QM for the message.

If another client request has come into QM and picked the message from the queue before the message get request to QM happens then the message will not be available on QM for the request to pick up. The request will simply fail as normal.

In another embodiment the system is described in a non HTTP messaging network. In a non HTTP messaging network a support means such as the HTTP servlet is not provided for each messaging or queue manager. Instead API crossing exits are used to intercept messages and replicate the message key information.

Messaging networks for example WebSphere MQ WebSphere MQ is a trade mark of International Business Machines Corporation provide a means for transforming data between different architectures and protocols such as Big Endian to Little Endian Endian is a trade mark of Endian S.R.L or EBCDIC Extended Binary Coded Decimal Interchange Code to ASCII American Standard Code for Information Interchange . This is accomplished through the use of message data exits. Exits are compiled applications which run on the queue manager host and are executed by the WebSphere MQ software at the time data transformation is needed.

Referring to a messaging network is shown in a non HTTP environment. A first client puts a message to the messaging network and a second client which wishes to get the message put by the first client .

An edge or proxy server load balances the message requests made by clients to the queues distributed across multiple machines . A client does not specify to which machine the put request goes to.

Conventionally a client can specify the particular queue manager even in a scaled environment HTTP and non HTTP . The described system works on the basis that the client does not specify the queue manager but just the queue name in order to allow scaling to be effective. The scaling may be horizontal or vertical.

Each machine in the messaging network hosts a queue manager which provide a logical container for the message queues .

The messaging network function uses exits which are logic implemented in a queue manager where the support is implemented. The exits provide support to generate a link message to a message put onto its local queue . The exits intercept messages and replicate the message key information in a link message. The link message contains a subset of the information contained in the message including a reference to the location of the message.

The queue managers in addition to their regular queues have special queues for holding the link messages to messages on other queue manager s queues . As described in relation to the special queues for holding the link messages may be provided on the queue manager in which the message is put with access from the other queue manager or on the other queue manager itself.

When a message is put to a queue of a queue manager a corresponding link message is generated by an exit and placed on all other queue managers that are taking part in the horizontal cluster. The link message is put to a special queue or published by the first queue manger with a topic and received at the second queue manager by that queue manager subscribing to the topic using an exit or built in to the queue manager mechanism.

When a message is requested the request can be sent to any queue manager within the cluster according to whatever selection method is being used workload balancing round robin etc . The exit of the queue manager that has the request firstly looks on its local queue for the message. If it is not there then it attempts to find the message on the special queue .

If the link message is found on the special queue the reference in the link message is followed to retrieve the full message from its queue on a different queue manager .

The HTTP servlets and the exits providing the link message support may be provided in the form of a support pack for existing messaging networks.

Messaging networks may be adapted for use with HTTP messages and a bridge may be provided including the described functions for message delivery and retrieval.

The non HTTP embodiment of using exits may be provided as subsequently installable code or in the product itself.

There may be messaging networks including both HTTP clients and other non HTTP clients. The first embodiment described in relation to solves the problem of affinity when both clients are HTTP clients. There may be a scenario in which a third party for example an external application takes the original message from the queue and places a reply onto another queue. The external application uses the same sort of logic encapsulated into an exit on each queue manager. Such that each put to a machine from the external application is registered with the entire cluster as before.

The servlet logic is contained within the client connection logic the Java Enterprise Edition JEE connector architecture JCA in a JEE connection scenario or the client connection if just a standard connection rather than the application that uses the client connection. This enables modification to be implemented in a non invasive manner.

Management of the link messages on the special queues also has to be considered. This queue could very easily get filled up with link messages because it has a synopsis of every message delivery on every clustered queue in the HTTP cluster. Various standard timeout and clean up policies can be employed to ensure that this is not a problem.

The clean up is standard practice for messaging network administrators. It could be left to administrators to ensure that the queues get cleaned up as and when they desired for example when a queue was too big.

The clean up needs to take into account the fact that messages might not have actually expired yet. A solution to this problem is that the queue manager that holds the actual message publishes a delete this message reference to the messaging network and all the local queue managers act this out so that they clean out their copy of the reference message. This also means that each queue manager ensures that this clean up is done when each individual queue manager is not too busy.

There may also be occasions when the original message times out in which case the queue manager needs to understand that the message was a clustered message and then publish the delete this message reference to all the other queue managers. The cluster message may alternatively have the same timeout as the original message.

Scalability of this special queue can also be considered such that a shadow queue mechanism is provided for example for every local Q there is a Q.CLUSTER.QUEUE. A single cluster queue may alternatively be used for multiple local or remote queues.

Referring to an exemplary system for implementing the invention includes a data processing system suitable for storing and or executing program code including at least one processor coupled directly or indirectly to memory elements through a bus system . The memory elements can include local memory employed during actual execution of the program code bulk storage and cache memories which provide temporary storage of at least some program code in order to reduce the number of times code must be retrieved from bulk storage during execution.

The memory elements may include system memory in the form of read only memory ROM and random access memory RAM . A basic input output system BIOS may be stored in ROM . System software may be stored in RAM including operating system software . Software applications may also be stored in RAM .

The system may also include a primary storage means such as a magnetic hard disk drive and secondary storage means such as a magnetic disc drive and an optical disc drive. The drives and their associated computer readable media provide non volatile storage of computer executable instructions data structures program modules and other data for the system . Software applications may be stored on the primary and secondary storage means as well as the system memory .

The computing system may operate in a networked environment using logical connections to one or more remote computers via a network adapter .

Input output devices can be coupled to the system either directly or through intervening I O controllers. A user may enter commands and information into the system through input devices such as a keyboard pointing device or other input devices for example microphone joy stick game pad satellite dish scanner or the like . Output devices may include speakers printers etc. A display device is also connected to system bus via an interface such as video adapter .

Referring to a flow diagram is shown illustrating a message put process of the described system. A put message is received at a first queue manager. The original data is striped out of the message and replaced with a shortened message including a reference to the first queue manager. The shortened message may optionally include sufficient information for message selections to be made. The shortened message is put to a cluster queue either on each queue manager in a cluster or on a joint cluster queue at one of the queue managers. The original message is put onto the local queue of the queue manager.

Referring to a flow diagram is shown illustrating a message get process of the described system. A get request for a message is received at a second queue manager. The local queue at the second queue manager is checked . It is determined if the message is found . If the message is found the message is returned .

If the message is not found the process proceeds to check in the cluster queue for a shortened message. The cluster queue may be local at the second queue manager or may be remote on another queue manager. This check may include using message selectors to look for a specific message using information in the shortened message. It is determined if the shortened message is found . If a shortened message relating to the requested message is not found on the cluster queue the request fails . If it is found on the cluster queue the reference in the shortened message is followed to the queue manager on which the full message is held. A remote request is made to the queue manager where the full message is held. The full message is returned from the local queue of the queue manager where the message is held.

Referring to a flow diagram is shown illustrating a clean up process of the described system. The queue manager to which a remote request is made for a message on its local queue publishes a delete message for the retrieved message to all queue managers in the cluster. All the queue managers in the cluster delete the shortened message relating to the retrieved message from their cluster queue.

Referring to a flow diagram is shown illustrating a further clean up process of the described system. The queue manager holding a message in its local queue checks a message duration on the queue. It is determined if the message has timed out. If a message has not timed out the process loops to continue checking the message. If a message has timed out it is determined if the message was a clustered message. If not the message is just deleted . If the message was a clustered message the queue manager publishes a delete message to all queue managers in the cluster. All the queue managers in the cluster delete the shortened message relating to the message from their cluster queue. The queue manager also deletes the full message from its local queue.

A support server alone or as part of a messaging system providing the link message functionality may be provided as a service to a customer over a network.

Embodiments of the invention can take the form of an entirely hardware embodiment an entirely software embodiment or an embodiment containing both hardware and software elements. In one embodiment the invention is implemented in software which includes but is not limited to firmware resident software microcode etc.

The invention can take the form of a computer program product accessible from a computer usable or computer readable medium providing program code for use by or in connection with a computer or any instruction execution system. For the purposes of this description a computer usable or computer readable medium can be any apparatus that can contain store communicate propagate or transport the program for use by or in connection with the instruction execution system apparatus or device.

The medium can be an electronic magnetic optical electromagnetic infrared or semiconductor system or apparatus or device or a propagation medium. Examples of a computer readable medium include a semiconductor or solid state memory magnetic tape a removable computer diskette a random access memory RAM a read only memory ROM a rigid magnetic disk and an optical disk. Current examples of optical disks include compact disk read only memory CD ROM compact disk read write CD R W and DVD. Improvements and modifications can be made to the foregoing without departing from the scope of the present invention.

