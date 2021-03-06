---

title: Integration gateway
abstract: A message oriented middleware server application executable by at least one processor implements a message oriented middleware message provider that mediates messaging operations with a plurality of heterogeneous applications including a number of casino gaming applications, where instances of the heterogeneous applications which execute on the plurality of networked processor-based client devices including the networked processor-based casino gaming devices.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08412768&OS=08412768&RS=08412768
owner: Ball Gaming, Inc.
number: 08412768
owner_city: Las Vegas
owner_country: US
publication_date: 20090709
---
This application claims the benefit under 35 U.S.C. 119 e of U.S. Provisional Patent Application No. 61 080 165 filed Jul. 11 2008 where this provisional application is incorporated herein by reference in its entirety.

This description generally relates to the field of communications networks and more particularly to middleware for facilitating communication in heterogeneous communications networks.

Many gaming properties are attempting to integrate and leverage the information and capabilities provided by all of the computing devices located on their property. This would provide players with a more seamless experience as they would have access to greater functionality at every computing device they interact with. Moreover the gaming properties will also be able to better track players activities and better determine what service appeal to which players.

Unfortunately gaming properties typically include a variety of different gaming devices gaming servers and gaming software. Often these gaming devices gaming servers and gaming software have been distributed by different gaming suppliers and may be associated with proprietary protocols developed by each of those different gaming suppliers. Indeed many gaming properties have legacy gaming devices and software on their gaming floors that use protocols that are no longer supported. Thus the task of interoperability and communication has been made much more difficult by these heterogeneous components. Although there are communication standards that have been developed by groups such as the Gaming Standards Association many gaming suppliers expand upon or even ignore these standards in order to improve the functionality they can offer.

It would therefore be desirable to enable improved communication between heterogeneous components in a gaming property.

In the drawings identical reference numbers identify similar elements or acts. The sizes and relative positions of elements in the drawings are not necessarily drawn to scale. For example the shapes of various elements and angles are not drawn to scale and some of these elements are arbitrarily enlarged and positioned to improve drawing legibility. Further the particular shapes of the elements as drawn are not intended to convey any information regarding the actual shape of the particular elements and have been solely selected for ease of recognition in the drawings.

In the following description certain specific details are set forth in order to provide a thorough understanding of various disclosed embodiments. However one skilled in the relevant art will recognize that embodiments may be practiced without one or more of these specific details or with other methods components materials etc. In other instances well known structures associated with servers networks displays and or with computer type devices have not been shown or described in detail to avoid unnecessarily obscuring descriptions of the embodiments.

Unless the context requires otherwise throughout the specification and claims which follow the word comprise and variations thereof such as comprises and comprising are to be construed in an open inclusive sense that is as including but not limited to. 

Reference throughout this specification to one embodiment or an embodiment means that a particular feature structure or characteristic described in connection with the embodiment is included in at least one embodiment. Thus the appearances of the phrases in one embodiment or in an embodiment in various places throughout this specification are not necessarily all referring to the same embodiment. Furthermore the particular features structures or characteristics may be combined in any suitable manner in one or more embodiments.

As used in this specification and the appended claims the singular forms a an and the include plural referents unless the content clearly dictates otherwise. It should also be noted that the term or is generally employed in its sense including and or unless the content clearly dictates otherwise.

The headings and Abstract of the Disclosure provided herein are for convenience only and do not interpret the scope or meaning of the embodiments.

Any process descriptions or blocks in flowcharts described below may be understood as representing modules segments or portions of code which include one or more executable instructions for implementing specific logical functions. In alternative embodiments various logical functions or acts may be executed out of order from that shown or discussed including substantially concurrently or in reverse order and or manually depending on the functionality involved as would be understood by those reasonably skilled in the art.

Acknowledgement Control messages exchanged between clients and broker to ensure reliable delivery. There are two general types of acknowledgement client acknowledgements and broker acknowledgements.

Administered Objects A pre configured object a connection factory or a destination that encapsulates provider specific implementation details and is created by an administrator for use by one or more JMS clients. The use of administered objects allows JMS clients to be provider independent. Administered objects are placed in a JNDI name space by and are accessed by JMS clients using JNDI lookups.

Asynchronous Messaging An exchange of messages in which the sending of a message does not depend upon the readiness of the consumer to receive it. In other words the sender of a message need not wait for the sending method to return before it continues with other work. If a message consumer is busy or offline the message is sent and subsequently received when the consumer is ready.

Authentication The process by which only verified users are allowed to set up a connection to a broker.

Authorization The process by which a message service determines whether a user can access message service resources such as connection services or destinations to perform specific operations supported by the message service.

Broker The Message Queue entity that may manage inter alia message routing delivery persistence security and logging and that provides an interface for monitoring and tuning performance and resource use.

Client An application or software component that interacts with other clients using a message service to exchange messages. The client can be a producing client a consuming client or both.

Connection A communication channel between a client and a broker used to pass both payload messages and controls.

Messages Connection Factory The administered object the client uses to create a connection to a broker. This can be a Connection Factory object a Queue Connection Factory object or a Topic Connection Factory object.

Consumer An object Message Consumer created by a session that is used for receiving messages sent from a destination. In the point to point delivery model the consumer is a receiver or browser Queue Receiver or Queue Browser in the publish subscribe delivery model the consumer is a subscriber Topic Subscriber .

Data store A database where information e.g. durable subscriptions data about destinations persistent messages auditing data needed by the broker is permanently stored.

Delivery mode An indicator of the reliability of messaging whether messages are guaranteed to be delivered and successfully consumed once and only once persistent delivery mode or guaranteed to be delivered at most once non persistent delivery mode .

Delivery model The model by which messages are delivered either point to point or publish subscribe. In JMS there are separate programming domains for each using specific client runtime objects and specific destination types queue or topic as well as a unified programming domain.

Destination The physical destination in a Message Queue broker to which produced messages are delivered for routing and subsequent delivery to consumers. This physical destination is identified and encapsulated by an administered object that a client uses to specify the destination for which it is producing messages and or from which it is consuming messages.

Encryption A mechanism for protecting messages from being tampered with during delivery over a connection.

Group The group to which the user of a Message Queue client belongs for purposes of authorizing access to connections destinations and specific operations.

Message service A middleware service that may provide asynchronous reliable exchange of messages between distributed components or applications. It may include a broker the client runtime the several data stores needed by the broker to carry out its functions and the administrative tools needed to configure and monitor the broker and to tune performance.

Messages Asynchronous requests reports or events that are consumed by messaging clients. A message may have a header to which additional fields can be added and a body. The message header specifies standard fields and optional properties. The message body contains the data that is being transmitted.

Messaging A system of asynchronous requests reports or events used by applications that may allow loosely coupled applications to transfer information reliably and securely.

Producer An object Message Producer created by a session that is used for sending messages to a destination. In the point to point delivery model a producer is a sender Queue Sender in the publish subscribe delivery model a producer is a publisher Topic Publisher .

Queue An object created by an administrator to implement the point to point delivery model. A queue is available to hold messages even when the client that consumes its messages is inactive. A queue may be used as an intermediary holding place between producers and consumers.

Selector A message header property used to sort and route messages. A message service may perform message filtering and routing based on criteria placed in message selectors.

Session A single threaded context for sending and receiving messages. This can be a queue session or a topic session.

Topic An object created by an administrator to implement the publish subscribe delivery model. A topic may be viewed as a node in a content hierarchy that is responsible for gathering and distributing messages addressed to it. By using a topic as an intermediary message publishers may be kept separate from message subscribers.

As illustrated the heterogeneous components within the network include applications other software components and a number of servers collectively . The applications and other software components may communicate with the integration gateway via an application programming interface API while the servers communicate via their respective server interfaces collectively . In one embodiment the servers may comprise a plurality of different platforms and may communicate via their respective platform interfaces.

As illustrated the integration gateway module may be accessible via a computing system . As would be well understood by those skilled in the art the computing system may comprise any of a variety of computers servers. In one embodiment the computing system may enable administration and configuration of the integration gateway .

The integration gateway allows the components of the network to communicate despite their differences. Thus these heterogeneous components do not need to be recreated as homogeneous elements. The integration gateway sometimes referred to as middleware may enable the software components e.g. applications enterprise java beans servlets and other components that have been developed independently and that run on different networked platforms to interact with one another. In some embodiments the integration gateway resides between the application layer and the platform layer i.e. the operating system and underlying network services .

Applications distributed on different network nodes e.g. applications executing on the servers may use the integration gateway to communicate without having to be concerned neither with the details of the operating environments that host other applications nor with the services that connect them to these applications. In addition an administrative interface may be provided on the computing system . This administrative interface may enable personnel working on the network to keep this virtual system of interconnected applications reliable and secure. The performance of the network can also be measured and tuned and the network may even be scaled without losing function.

In one embodiment the integration gateway may serve as a single implementation communication point to communicate with various enterprise products. Each of these various enterprise products e.g. each of the servers may use industry specific protocols like the System to System S2S Protocol promulgated by the Gaming Standard Association in order to communicate with the integration gateway . Indeed a variety of different protocols including proprietary and standard protocols may be used to communicate via the integration gateway . The integration gateway may also facilitate real time information access among disparate systems within the network thereby helping to streamline business processes and improve organizational efficiency.

Middleware can be generally grouped into the following categories which may each be supported by or integrated into the integration gateway 

Remote Procedure Call or RPC based middleware Such middleware may allow procedures in one application to call procedures in remote applications as if they were local calls. The middleware can implement a linking mechanism that locates remote procedures and makes these transparently available to a caller. This type of middleware may be handled by procedure based or object based programs or components.

Object Request Broker or ORB based middleware Such middleware may enable an application s objects to be distributed and shared across heterogeneous networks.

Message Oriented Middleware or MOM based middleware Such middleware may allow distributed applications to communicate and exchange data by sending and receiving messages.

Each of these categories makes it possible for one software component to affect the behavior of another component over the network . They are different in that RPC and ORB based middleware may create systems of tightly coupled components whereas MOM based systems may allow for a looser coupling of components. In an RPC or ORB based system when one procedure calls another the procedure may wait for the called procedure to return before it can do anything else. As mentioned before in each of these categories the middleware i.e. the integration gateway in one embodiment functions partly as a super linker locating the called procedure on the network and using network services to pass function or method parameters to the procedure and then to return results.

In general MOM based systems may make use of a messaging provider to mediate messaging operations. The basic elements of a MOM based system are Clients messages and the MOM messaging provider which may include an API and administrative tools. The MOM provider may use a variety of different architectures to route and deliver messages it can use a centralized message server or it can distribute routing and delivery functions to each Client machine. Some MOM based systems combine these two approaches.

Using a MOM based system in one embodiment a Client makes an API call to send a message to a destination managed by the MOM provider. The call invokes provider services to route and deliver the message. Once it has sent the message the Client can continue to do other work while the MOM provider retains the message until a receiving Client retrieves it. The message based model coupled with the mediation of the MOM provider makes it possible to create a system of loosely coupled components. The MOM based system may therefore be able to continue to function reliably without downtime even when individual components or connections fail.

The MOM provider may also include an administrative interface using which an administrator can monitor and tune performance. Client applications are thus effectively relieved of messaging related tasks except those of sending receiving and processing messages. The MOM based system and the administrator can work to resolve issues like interoperability reliability security scalability and performance without modifying the client applications.

The integration gateway may comprise a Java based MOM solution that allows client applications to create send receive and read messages in a distributed enterprise system such as network . Of course in other embodiments the integration gateway may be written in other programming languages and may run on a variety of platforms. The integration gateway may reduce the complexity of embedding diverse communication protocols within the client applications making it faster and easier to integrate third party host legacy applications with newer products. The integration gateway may also improve the reliability flexibility and scalability of messaging. The heterogeneous nature of the network may arise from both the technology on which the products in the network are based and or the protocols that they support to communicate with the other systems.

The integration gateway can play a variety of roles within the network it may comprise a stand alone product or may be used as an embedded component in a larger distributed runtime system. As a standalone product the integration gateway may define the backbone of an enterprise application integration system. Embedded in an application server the integration gateway may support inter component messaging. For example J2EE uses a JMS provider to implement message driven beans and to allow EJB components to send and receive messages. In one embodiment message mapping conversion according to the destination requirements may be implemented as a pluggable component. This may enable various channels and products to exchange messages without being concerned about potential incompatibilities.

The integration gateway may provide a number of features advantages within the network the integration gateway may be flexible scalable reliable and may provide synchronous and asynchronous messaging across various platforms the integration gateway may provide fast guaranteed message delivery receipt notification transaction control and a data persistence mechanism for multiple products and platforms the integration gateway may eliminate complexity of embedding communication protocols in business logic the integration gateway may provide support for cross platform Clients and servers the integration gateway may support platform dependent communication protocols data formats and encoding the integration gateway may also support for the following messaging models Publish Subscribe Messaging Point to Point Messaging and or Request Reply Messaging the integration gateway may also provide a stand alone GUI for setup and maintenance and may support common message formats such as stream text and byte.

In one embodiment the integration gateway may provide a flexible MOM solution which may be easily customized according to the needs of internal products which differ in technology and in the interfaces used for communication. In another embodiment the integration gateway may allow legacy systems to communicate e.g. indirectly via the integration gateway with newer products based on evolving technologies.

Each of these services comprising the integration gateway is detailed in greater detail in the following sections.

The local configuration cache services represent the services configuration folder structure in the integration gateway . This services configuration folder structure may be created during the installation process of the integration gateway and may be used to manage the configurations for each service provided by the integration gateway . In one embodiment the integration gateway does not include a database. Although in other embodiments of course the integration gateway may include one or more databases.

The common services layer acts as a common services layer. That is the common services layer may represent and provide access to the common functions used by the integration gateway such as logging configuration database access and other foundation classes.

The data transformation layer may include code that forms the outlet for custom or platform specific data manipulation and formatting. This layer may be used for data in both inbound and outbound message Queues. The business logic execution may be based on the message types used. Example Responding with an ACK message in the S2S protocol for incoming messages. 

In one embodiment the data transformation layer supports the following data types Simple Strings XML Complex Files Images Bitmaps Byte Streams and Serializable Objects Marshal By Value . In other embodiments of course other data types may be supported.

The data transformation layer may also support the following data encoding options ASCII EBCDIC and UTF 8. Again in other embodiments other data encoding options may be supported.

In one embodiment the messaging layer acts as a central layer for the integration gateway and enables the management of messages and objects for inter application communication. The messaging layer may be designed based on Publisher Subscriber or Point to Point Asynchronous messaging models utilizing JMS Topics Producer Consumer Object classes . The messaging layer may also use the Request Response Synchronous model using JMS Queues.

In one embodiment the messaging layer may enable message persistence using Durable Topics Queues and may enable the administration of integration gateway services using a stand alone user interface. The messaging layer may also enable configuration of certain services e.g. Publisher Subscriber and Point to Point using the stand alone user interface. Finally the messaging layer may include failover and load balancing which may be implemented using Sun Java System Message Queue 4 2005Q1 Enterprise Edition.

Generally the integration gateway and in particular the messaging layer may allow components and applications to communicate by producing and consuming messages. The integration gateway defines two patterns or messaging domains that govern this communication. These messaging domains are Point to Point Messaging and Publish Subscribe Messaging as described above . The integration gateway may be configured to support either or both of these patterns. The basic integration gateway objects include connections sessions Producers Consumers destinations and messages that are used to specify messaging behavior in both domains.

In the Point to Point domain message Producers are called Senders and Consumers are called Receivers. The senders and receivers may exchange messages by means of a destination called a Queue senders produce messages to the Queue and receivers consume messages from the Queue.

Point to Point messaging may provide a number of features. First more than one Producer may be allowed to send messages to a Queue. Such Producers can share a connection or use different connections even though they may all access the same Queue. Second more than one Receiver may be allowed to consume messages from a Queue. However in one embodiment each message can only be consumed by one Receiver. Thus Msg Msg and Msg will be consumed by different Receivers. Third Receivers can share a connection or use different connections but they may all access the same Queue. Fourth the sending and receiving of messages via Point to Point messaging may be enabled with no timing dependencies. Thus a Receiver can fetch a message even if it was running when the Client sent the message. Fifth Senders and Receivers may be added and deleted dynamically at runtime. This feature may allow the integration gateway to expand or contract as needed. Sixth messages may be placed on the Queue in the order sent but the order in which they are consumed may depend on factors such as message expiration date message priority and whether a selector is used in consuming messages.

The Point to Point domain may also offer certain advantages. For example the fact that multiple Receivers can consume messages from the same Queue may allow effective load balancing of message consumption as long as the order in which messages are received is not important. As another example messages destined for a Queue may be retained even if there are no Receivers. Finally Clients may be able to use a Queue browser object to inspect the contents of a Queue. The Clients can then consume messages based on the information gained from this inspection. That is although the consumption model is normally FIFO first in first out in some embodiments Clients can consume messages that are not at the head of the Queue if they know what messages they want based at least in part on message selectors. Administrative Clients may also use the Queue browser to monitor the contents of a Queue.

In the Publish Subscribe domain message Producers are called Publishers and message Consumers are called subscribers. The Publishers and Subscribers may exchange messages by means of a destination called a topic Publishers produce messages to a topic and Subscribers subscribe to a topic and consume messages from a topic.

The subscribers to these topics can be non durable or durable. The Broker may be configured to retain messages for all active subscribers but it may be configured to only retain messages for inactive subscribers if these subscribers are durable.

In the Publish Subscribe domain more than one Producer may be allowed to publish messages to a topic. Such Producers can share a connection or use different connections but they may all access the same topic. In some embodiments more than one subscriber can consume messages from a topic. The subscribers may retrieve all of the messages published to a topic unless they use selectors to filter out messages or the messages expire before they are consumed. Subscribers can also share a connection or use different connections but they may all access the same topic. As described above durable subscribers can be active or inactive. However even when a durable subscriber is inactive the Broker may be configured to retain messages for them. Publishers and subscribers may be added and deleted dynamically at runtime thus allowing the integration gateway to expand or contract as needed. In one embodiment messages are published to a topic in the order sent but the order in which they are consumed depends on factors such as message expiration date message priority and whether a selector is used in consuming messages. Publication and subscription may include a timing dependency. For example a topic subscriber may be able to consume only those messages published after it has created the subscription.

A session object may be used to create a Durable Subscriber to a topic. The Broker may then retain messages for such subscribers even when the subscriber becomes inactive.

In some embodiments because the Broker must maintain the state for the subscriber and resume delivery of messages when the subscriber is reactivated the Broker can identify a given subscriber during its comings and goings. The subscriber s identity may be constructed from a Client ID a property of the connection that created the subscriber and a subscriber name specified at the time of its creation. Other means of identifying the subscriber may be used in different embodiments.

The Communication Services Layer may serve as the primary layer responsible for inter system communication. Message integrity may be achieved with ACK NAK messaging architecture while the Keepalive supports a real time Request Response message protocol.

The Web services provided by the Communication Services Layer may enable communication among different products produced by different companies.

For example communication between a Third Party Debit Ticket Kiosk system and ACSC for the Ticket number sequence may be enabled. In such an embodiment the Debit Ticket Kiosk may send out messages using the S2S protocol to the integration gateway and the integration gateway can then communicate with ASCS obtain a response and form an S2SMessage to send back to Debit Ticket Kiosk.

The Web Services may use message processor plug ins to translate messages into the format required by the requested system.

In one embodiment the communication services layer may support the following protocols Basic low level Client Server TCP IP sockets Secure File Transfer Protocol SFTP HTTP HTTPS SOAP e.g. using Apache Axis2 .NET Remoting using IIOP ORB protocol RMI EJB and Database Stored Procedures. Of course in other embodiments additional protocols including proprietary protocols may be supported by the communication services layer .

The Interceptor Services Layer may serve as a lightweight middleware object in the integration gateway that coexists with applications and or systems e.g. applications and systems distributed by Bally Gaming utilizing the integration gateway services. This layer may communicate with the local application using simple Java programs RMI IIOP and or database stored procedures.

In one embodiment the objects used to implement messaging by the integration gateway may remain essentially the same across programming domains. These objects may include Connection Factories Connections Sessions Producers Consumers Messages and Destinations. Table 1 below summarizes exemplary steps for sending and receiving messages. Note that steps 1 through 6 are the same for senders and receivers.

The following sections describe objects that may be used by Producers and Consumers such as the Connections Sessions Messages and Destinations. A description of the production and consumption of messages follows.

In one embodiment a Client uses an object e.g. a Connection Factory to create a connection. The connection object i.e. Connection represents a Client s active connection to the Broker. It may use an underlying connection service that is either started by default or explicitly started by the administrator for this Client.

The allocation of communication resources and authentication of the Client may take place when a connection is created. The Connection may comprise a relatively heavyweight object and Clients may do all their messaging with just a single connection. In some embodiments Connections support concurrent use i.e. any number of Producers and Consumers can share a connection.

When a connection factory is created the behavior of all connections derived from it may be configured by setting the properties of the connection factory. For example for a Message Queue the following information may be specified the name of the host on which the Broker resides the connection service desired and the port through which the Client can access the service how to handle automatic reconnection to the Broker if a connection fails This feature may reconnect the Client to the same Broker or to a different Broker if a connection is lost. Data failover may not be guaranteed as persistent messages and other state information may be lost when reconnecting to a different Broker. the ID of Clients that need the Broker to track durable subscriptions the default name and the password of a user attempting the connection This information may be used to authenticate the user and to authorize operations if a password is not specified at connection time. whether Broker acknowledgements should be suppressed for those Clients who are not concerned with reliability how to manage the flow of control and payload messages between the Broker and the Client runtime and whether certain message header fields should be overridden.

If a connection represents a communication channel between a Client and a Broker a session may designate a single conversation between the Client and Broker. The session object may be used to create messages message Producers and message Consumers. When a session is created reliable delivery may be enabled through a number of different acknowledgement options or through transactions.

A session may comprise a single threaded context for producing and consuming messages. Multiple message Producers and message Consumers may be created for a single session but a restriction may be instituted to use these message Producers and message Consumers serially. A session object may also be used to do the following create and configure destinations for those Clients that do not use administered objects to define destinations create and configure temporary topics and Queues These topics and Queues may be used as part of the request reply pattern discussed in greater detail below . support transaction processing define a serial order for producing or consuming messages and or serialize the execution of message listeners for asynchronous Consumers.

In one embodiment each message is composed of three parts a header the header s properties and a body.

The message header may be a requirement for every valid message. The header may inter alia contain the following exemplary fields set forth in Table 2.

Another field that may be used is a Delivery Mode field which may determine the reliability of message delivery. This field may indicate whether a given message is persistent.

The message body contains the data that Clients want to exchange. The type of message may determine the contents of the message body as well as how the message body should be processed by the consumer. Some exemplary types are set forth in Table 3. The Session object may include a create method for each type of message body.

Java Clients may be configured to set a property so that the Client runtime compresses the body of a message being sent. The Message Queue runtime on the consumer side may then decompress the message before delivering it.

In one embodiment messages may be sent or published by a message Producer within the context of a connection and or session. In one embodiment a Client uses a message Producer object Message Producer to send messages to a physical destination represented in the API as a destination object.

When a Message Producer is created a default destination may be specified to which all the Message Producer s messages will be sent by default. Default values for the message header fields that govern persistence priority and time to live may also be specified. These default values may then be used by all messages issued from that Producer unless they are over ridden. In one embodiment these default values may be easily over ridden if for example an alternate destination is specified when sending a message or if alternate values for the header fields are entered for a message.

The messages produced above may be received by a message consumer within the context of a connection and or session. In one embodiment the client uses a message consumer object Message Consumer to receive messages from a specified physical destination represented in the API as a destination object.

In one embodiment three factors may affect how the Broker delivers messages to a consumer 1 whether consumption is synchronous or asynchronous 2 whether a selector is used to filter incoming messages and 3 if messages are consumed from a topic destination whether the subscriber is durable.

Another factor that may affect message delivery and client design is the degree of reliability needed for the consumer.

Referring to one exemplary messaging process is illustrated. As illustrated therein client A and client B are message Producers sending messages collectively to client C client D client E and client F by way of two different kinds of destinations.

Messaging between clients A C and D illustrates a Point to Point pattern. Using this pattern client A may send a message Msg1 or Msg 2 to a Queue destination from which only one of the Receivers may get it. In the illustrated embodiment each message may be received by only one receiver and no other receiver accessing the Queue destination can get that message.

Messaging between clients B E and F illustrates a Publish Subscribe pattern. Using this broadcast pattern client B may send a message Msg3 to a Topic destination from which both consuming subscribers can retrieve it. Each subscriber may obtain its own copy of the message

Message Consumers in either the Point to Point or Publish Subscribe domains may choose to get messages synchronously or asynchronously. Synchronous Consumers may be required to make an explicit call to retrieve a message while asynchronous Consumers may specify a callback method that is invoked to pass a pending message. In some embodiments consumers can also filter out messages by specifying selection criteria for incoming messages.

Asynchronous communication can be defined as communication where one party simply sends a message to another. Problems may arise when the sending party expects a response to the message or when the timeframe during which a sending entity can remember that it sent a message and that it expects a reply is short.

Synchronous communication can be defined as communication where one party has a conversation with another. This may be presented as a request response scenario. An interface may be defined between two Objects or Services where an invocation results in a response once the requested processing has been completed. Indeed in some embodiments even if there is no actual response a void response may be required.

In one embodiment the integration gateway provides support for the following protocol definitions discussed in greater detail below Database Interface DotNet Client DotNet Server FTP Get FTP Put HTTP Get HTTP Post iSeries Data Queue Writer iSeries Data Queue Reader Object Serializer Object Deserializer RMI Client DotNet Server RMI Server DotNet Client Socket Server Socket Multiplexer Socket Relay Client Socket Client S2S Message Client S2S Message Service S2S Voucher End of Day Report Service. These services and related protocols may facilitate intersystem communication and message processing.

This protocol may be used to create a service that communicates with a database by making a stored procedure call. The service can take configurable parameters for connecting and executing a stored procedure on a database. It can then pass an entry to the host in alphanumeric form and then get a response too in alphanumeric form.

Apart from the database connection parameters the following parameters may also be configurable Source Event the point on the Queue where the service listens for incoming messages and Destination Event the point on the Queue where the stored procedure reply is written .

In one embodiment the service created listens to an event on a Queue associated with the integration gateway . When a message arrives in the Queue if configured the service may then process the message and pass it on to the stored procedure. If the stored procedure returns a response the response is then written back to the Queue at an event configured as its destination.

All database connection parameters such as Source Event and Destination Event may be configurable on a user interface of the integration gateway while creating a Database Interface service.

In one embodiment the DotNet protocols may use IIOP Internet Inter ORB Protocol to communicate with a .NET Remoting server and or a .NET Remoting Client. .NET Remoting is a feature of Microsoft s DotNet that provides RPC RMI like capabilities.

IIOP is a protocol that enables distributed programs written in different programming languages to communicate over the Internet. IIOP forms a part of the industry standard Common Object Request Broker Architecture CORBA .

In one embodiment the DotNet Client service listens to a Queue associated with the integration gateway . When a message arrives the service may access a remote object on a DotNet system e.g. a .NET Remoting Server by passing that message as a parameter to the method on that object. In some embodiments the following parameters may be configured for the DotNet Client service Context Provider URL the factory for ORB API and Object URI the URI of the object exposed on the .NET Remoting Server .

The DotNet Server service may allow a DotNet system e.g. a .NET Remoting Client to access an object exposed via the integration gateway by passing a message as a parameter to the method on this object. The DotNet Server service may then write to a Queue associated with the integration gateway on the configured event. In some embodiments the following parameters may be configured for the DotNet Server service Context Provider URL the factory for ORB API and Object URI the URI of the object exposed on the integration gateway Server .

The FTP Get Service may be used to poll a remote directory periodically using the File Transmission Protocol FTP . Once any new and relevant file is found the service can then download the file and write the file object to a Queue associated with the integration gateway . The Queue may be monitored by other programs e.g. by FTP Put which may retrieve the file object from the Queue.

The FTP Put Service may be used to listen to Message Events of the Queue. Once a message is written to the Queue the service may check whether it is a file object. If so the FTP Put service may retrieve and upload the file to an FTP Server.

The HTTP Post service may send the data of a file in a local file system to a configured http server. The HTTP Post request can also send additional data to the host server which may be specified after the URL the headers and a blank line to indicate the end of the headers.

The HTTP Get service may be used to download files from the configured http Server to the local file system.

In some embodiments these HTTP services may also provide other processing options e.g. by marking the downloaded uploaded files by deleting or renaming the files.

These services may be included to allow writes reads to from iSeries Data Queues. The iSeries Data Queue Reader service may be configured to read messages from an iSeries Data Queue and write them to the Queue associated with the integration gateway . The iSeries Data Queue Writer service may be configured to listen to the Queue associated with the integration gateway and when a message is received write that message to an iSeries Data Queue.

In some embodiments a variety of iSeries Data Queue access parameters may be configured on a user interface of the integration gateway . For example the iSeries Data Queue service may be configured for the following iSeriesDataQueueRx and iSeriesDataQueueTx.

These RMI related protocols may enable a Java system and a DotNet system to communicate using RPC based on IIOP. The difference between the RMI Server Client DotNet protocols and other DotNet protocols described herein is that these RMI protocols may be designed so as not to include a Queue concept. Thus these RMI Server Client DotNet protocols may be used for synchronous inter system communication.

Object Serialization is the process of saving an object s state to a sequence of bytes and may also be used to describe the process of rebuilding those bytes into a live object at a later point in time. In the integration gateway the Object Serializer service may allow all of the files in a selected directory e.g. a source directory to get serialized and may then write the object form of these files to the Queue associated with the integration gateway .

The Object Deserializer service that resides on the Queue may listen for Object messages and may deserialize them into files in a configured path.

Sockets are interfaces that can plug into each other over a network such as network . Once plugged in the programs or software components so connected can communicate with each other. A socket represents a single connection between exactly two pieces of software. When more than two pieces of software communicate in client server or distributed systems for example many web browsers simultaneously communicating with a single web server multiple sockets may be required. Socket based software may execute on two separate computers on the network however sockets can also be used to communicate locally i.e. inter process on a single computer. Various socket based services may be made available on the network via the integration gateway .

Sockets may be bi directional i.e. either side of the connection is capable of sending and receiving data. The application that initiates communication may be termed the client and the other application may be termed the server.

There are two types of Internet Protocol IP traffic described generally in Table 4. These two types of traffic may have very different uses.

For socket based protocols the integration gateway may allow configuration of the type of the protocol i.e. whether it is TCP or UDP.

Once a socket server service is started a server socket may wait at the configured port for requests to come in over the network . The socket server may then perform operations based on those requests and then possibly return results to the requester.

In some embodiments this protocol enables different socket behaviors based on two configuration parameters the parameter Listener and the parameter Full Duplex . The parameter Listener is a Boolean parameter and may cause the socket to act as a server. If set to true the socket waits for requests and accepts connections. If set to false the socket may connect to an external server socket on the network .

The parameter Full Duplex is a Boolean parameter related to two way communication on the same line. When set to true the socket may behave in a two way fashion. When the Full Duplex parameter is configured to true a Full Duplex Event value may also be configured in order to identify the point where the service listens to the Queue of the integration gateway for incoming messages. This value may be written to the socket. If the Full Duplex parameter is set to false the communication is one way. That is the socket listens at a port and writes the incoming message to the Queue associated with the integration gateway at the specified point configured in Request Event .

The Full Duplex parameter may be used to define the type of communication between the Queue and the Socket Server Service. However irrespective of the Full Duplex value a socket may be configured to send or receive data.

For the socket multiplexer service the integration gateway may enable configuration of the following parameters port number IP IP address where the server socket will be opened multiplexer ports a list of values each value in the format of IPaddress Port the assumption being that server sockets are listening at all of these ports at the corresponding IP address and single pipe when set to true the conversation ends with a single request response scenario the Client socket is closed and looped for the next Client connection .

The socket multiplexer service may be configured to open a server socket at the specified IP address and port and listen for incoming connections. When a Client connects the incoming messages may be routed to a list of server sockets configured by the parameter multiplexer ports sequentially. The first message to the first socket the second message to the second socket and so on.

The socket relay client service may constitute two threads Receiver and Transmitter. These two threads may enable two way communication between a server socket and a regular socket. Each of these threads may be configured to read from one socket and write to another socket which may help in controlling traffic between the two sockets.

Socket client services may listen to the Queue of the integration gateway . When a message is received the socket client service writes to the configured IP address and port number. In some embodiments a Listener value can be configured to obtain Server Socket attributes. The period of delay in sending the acknowledgment after sending the message may also be configured using the parameter ackWait . If an acknowledgement is not received within the scheduled time the message may be re sent.

All of the socket services discussed above may also include other values that can be configured such as Start of Message SOM End of Message EOM and or Acknowledgment Message ACK .

The System to System S2S Messaging standard set by the Gaming Standard Association provides a set of communication protocols between gaming host systems e.g. accounting security progressive controllers advertising and promotion displays as well as between gaming and non gaming host systems. This S2S standard has emerged as a hospitality gaming industry solution. The current version of the S2S standard includes support for the following types of gaming and non gaming communications patron registration player ratings e.g. with respect to table games slots bingo keno poker sports book table games accounting hourly estimates open and closing fills and credits marker and chip purchase vouchers support comps e.g. complimentary awards points money or hospitality products system data and device configurations such as defining active inactive game types and calculations progressive controllers chip sets regional settings shifts or codes for particular types of data such as club or badge identifiers .

The S2S Message Service on the integration gateway may comprise a web service that is exposed to Clients who want to communicate using the S2S protocol. Both synchronous and asynchronous versions of S2S may be supported. An interceptor value may be configured based on the synchronous or asynchronous nature required. An interceptor may function as an entry point to the integration gateway for the incoming messages over the network and it may also handle the message processing tasks required for requests and responses. This message processing may even include translations performed for messages according to the target system requirements. In one embodiment the following interceptors may be supported 

Asynchronous Interceptor This interceptor may write incoming messages to a socket which in turn writes the message to the Queue of the integration gateway . This interceptor may be configured to achieve asynchronous S2S attributes.

Database Interceptor This interceptor may make a stored procedure call using the configured database connection parameters and return a response.

Java Interceptor This interceptor may make a Java RMI call to a remote method for which the message is sent as a parameter in order to receive a response.

DotNet Interceptor This interceptor may access an exposed object on a .Net Remoting server to access a remote method by passing the message as a parameter.

The S2S message client service may be configured to listen to the Queue for S2S responses and then write these S2S responses to a Web Service Client. The target URL may be configured as a parameter in some embodiments.

For Debit Ticket Kiosk functionality a Client may generate a request for a report that lists the ticket details for tickets issued during the current day. A corresponding S2S message may contain login details to the remote host and the required report name. The integration gateway can then perform S2S translations to generate a flat string message for ACSC.

ACSC may then respond with the link of the server to the integration gateway which in turn may use FTP to download the report from the identified server. The downloaded report may then be translated to S2S format and returned to the Client.

The integration gateway may allow the creation of multiple groups and services based on the application and requirements. In one embodiment the groups may be logically named. Groups and services may also be created within the groups. In one embodiment the same service may exist multiple times in the same group however it may have to be renamed. The following actions can be performed for each service Start Service used to start a selected service Stop Service used to stop a selected service Configure Service Save Service used to save a service selected after the configuration and Delete Service used to remove a selected service .

The services may be configured in a variety of ways depending on the Identity Message Filter and Client within a group. These settings may be common to all of the different service protocol settings.

In one embodiment an Identity tab displayed in the graphical user interface GUI of the integration gateway may be used to name and describe the services and their respective characteristics. For example the Identity tab may be used to access the Log Process Persistence Acknowledgement and Transaction settings described below.

The integration gateway may provide a logging facility to trace the run time of services. These logging facilities may log information at various levels such as the Engine Service Message levels. For each service the log level may be set independently according to information requirements.

The following types of messages may be made available in the Log files All all messages Debug messages generated during debugging Info information messages excluding Debug messages Warning all warning messages excluding debug and information messages and Error only error messages .

The process configuration on the integration gateway may allow the runtime of each service to be independently controlled. Using a Priority field the priority for each service may be defined. This priority setting may help in identifying those service threads that should execute prior to other configured service threads. The default priority for each service may be set to five i.e. the normal priority . One may be set to the highest priority and ten to the lowest priority. The service pause time may also be defined via this process configuration.

Persistence configuration may enable the definition of the Request and Response Event names for the service. These names in turn may determine the location of the respective message destinations on the JMS Queue.

The Response event may be configured for a number of services such as Database Interface DotNet Client DotNet Interceptor Database Interceptor S2S Message Client and or S2S Voucher End Of Day Report Service.

An acknowledgment mode may also be configured to determine the way a service handles the exchange of acknowledgment information when receiving messages from the Queue associated with the integration gateway . In one embodiment the services may be configured to have any of four possible acknowledgment modes 

Auto Acknowledge In Auto Acknowledge mode the client runtime sends a Client acknowledgment instantly for each message it delivers to the message consumer. The client runtime may then block waiting for a return Broker acknowledgment confirming that the Broker has received the Client acknowledgment. This acknowledgment handshake between the Client and the Broker may be handled automatically by the Client runtime.

Client Acknowledge In Client Acknowledge mode the Client application must explicitly acknowledge the receipt of all messages. This enables the deferment of acknowledgment until after the Client application has finished processing the message ensuring that the Broker will not delete it from persistent storage before processing is complete.

Dups OK Acknowledge In Dups OK Acknowledge mode the session automatically sends a Client acknowledgment each time it has received a fixed number of messages or when a fixed time interval has elapsed since the last acknowledgment was sent. This fixed batch size and timeout interval may be set to 10 messages and 7 seconds respectively but may also be configured differently. In one embodiment however the client may not itself configure the batch size or timeout interval. Unlike in the first two acknowledgment modes described above the Broker may not acknowledge receipt of the Client acknowledgment and the session thread does not block awaiting such return acknowledgment from the Broker. Thus there may be no way to confirm that the Client acknowledgment has been received and if that acknowledgment has been lost in transmission the Broker may redeliver the same message more than once.

No Acknowledge In No Acknowledge mode the Client application does not acknowledge receipt of messages nor does the Broker expect any such acknowledgment. In this mode there may be no guarantee that any message sent by the Broker has been successfully received. This mode thus sacrifices reliability for maximum message traffic throughput.

By enabling transactions an entire series of incoming and outgoing messages may be grouped together such that they may be treated as an atomic unit. The message Broker e.g. the integration gateway may then track the state of the transaction s individual messages but may be configured to not complete their delivery until the transaction as a whole is committed. In the event of a failure the transaction may be rolled back canceling all of the associated messages and restarting the entire series from the beginning.

A transacted session may be defined to have exactly one open transaction encompassing all messages sent or received since the session was created or the previous transaction completed. Committing or rolling back a transaction ends that transaction and automatically begins another.

In one embodiment the Message settings associated with the integration gateway may allow the configuration of Data transformational parameters.

In one embodiment the Message Processor Plug ins for Request and Response messages may be configured. Other message settings may also be configured such as message type e.g. string xml etc. . Messages may also be prioritized according to a particular type field of the message. This prioritization may help in filtering the messages that should be processed before other messages. Message scheduling may also be used to define the time for processing a given message. For more information on possible configurations that may be made using the user interface of the integration gateway the User Guide for the Bally Integration Gateway p. 38 et seq. may be consulted. This User Guide provides some exemplary user interface examples and examples regarding how one example integration gateway may be implemented.

The above description of illustrated embodiments including what is described in the Abstract is not intended to be exhaustive or to limit the embodiments to the precise forms disclosed. Although specific embodiments of and examples are described herein for illustrative purposes various equivalent modifications can be made without departing from the spirit and scope of the disclosure as will be recognized by those skilled in the relevant art. The various embodiments described above can be combined to provide further embodiments. To the extent that they are not inconsistent with the specific teachings and definitions herein U.S. patent publication No. 2008 0162729A1 U.S. patent publication No. 2007 0082737A1 U.S. patent publication No. 2007 0006329A1 U.S. patent publication No. 2007 0054740A1 U.S. patent publication No. 2007 01111791 U.S. provisional patent application Ser. No. 60 865 345 filed Nov. 10 2006 entitled COMPUTERIZED GAME MANAGEMENT SYSTEM AND METHOD U.S. provisional patent application Ser. No. 60 865 575 filed Nov. 13 2006 entitled COMPUTERIZED GAME MANAGEMENT SYSTEM AND METHOD U.S. provisional patent application Ser. No. 60 865 332 filed Nov. 10 2006 entitled DOWNLOAD AND CONFIGURATION SERVER BASED SYSTEM AND METHOD U.S. provisional patent application Ser. No. 60 865 550 filed Nov. 13 2006 entitled DOWNLOAD AND CONFIGURATION SERVER BASED SYSTEM AND METHOD U.S. nonprovisional patent application Ser. No. 11 938 121 filed Nov. 9 2007 entitled GAMING SYSTEM DOWNLOAD NETWORK ARCHITECTURE U.S. nonprovisional patent application Ser. No. 11 938 228 filed Nov. 9 2007 entitled GAMING SYSTEM CONFIGURATION CHANGE REPORTING U.S. nonprovisional patent application Ser. No. 11 938 155 filed Nov. 9 2007 entitled REPORTING FUNCTION IN GAMING SYSTEM ENVIRONMENT U.S. nonprovisional patent application Ser. No. 11 938 190 filed Nov. 9 2007 entitled SECURE COMMUNICATIONS IN GAMING SYSTEM U.S. nonprovisional patent application Ser. No. 11 938 163 filed Nov. 9 2007 entitled METHODS AND SYSTEMS FOR CONTROLLING ACCESS TO RESOURCES IN A GAMING NETWORK U.S. nonprovisional patent application Ser. No. 11 938 150 filed Nov. 9 2007 entitled NETWORKED GAMING ENVIRONMENT EMPLOYING DIFFERENT CLASSES OF GAMING MACHINES U.S. nonprovisional patent application Ser. No. 11 938 231 filed Nov. 9 2007 entitled DOWNLOAD AND CONFIGURATION SERVER BASED SYSTEM AND METHOD WITH STRUCTURED DATA U.S. nonprovisional patent application Ser. No. 11 938 225 filed Nov. 9 2007 entitled PACKAGE MANAGER SERVICE IN GAMING SYSTEM U.S. patent application Ser. No. 11 278 937 filed Apr. 6 2006 entitled LOGIC INTERFACE ENGINE SYSTEM AND METHOD U.S. Provisional Patent Application Ser. No. 60 676 429 filed Apr. 28 2005 entitled LOGIC INTERFACE ENGINE SYSTEM AND METHOD U.S. patent application Ser. No. 11 470 606 filed Sep. 6 2006 entitled SYSTEM GAMING U.S. Provisional Patent Application Ser. No. 60 714 754 filed Sep. 7 2005 entitled SYSTEM GAMING APPARATUS AND METHOD U.S. Provisional Patent Application No. 60 865 332 filed Nov. 10 2006 entitled DOWNLOAD AND CONFIGURATION SERVER BASED SYSTEM AND METHOD and U.S. Provisional Patent Application No. 60 865 396 filed Nov. 10 2006 entitled DOWNLOAD AND CONFIGURATION CAPABLE GAMING MACHINE OPERATING SYSTEM GAMING MACHINE AND METHOD are incorporated herein by reference in their entirety. Aspects of the embodiments can be modified if necessary to employ systems circuits and concepts of the various patents applications and publications to provide yet further embodiments.

For instance the foregoing detailed description has set forth various embodiments of the devices and or processes via the use of block diagrams schematics and examples. Insofar as such block diagrams schematics and examples contain one or more functions and or operations it will be understood by those skilled in the art that each function and or operation within such block diagrams flowcharts or examples can be implemented individually and or collectively by a wide range of hardware software firmware or virtually any combination thereof. In one embodiment the present subject matter may be implemented via Application Specific Integrated Circuits ASICs . However those skilled in the art will recognize that the embodiments disclosed herein in whole or in part can be equivalently implemented in standard integrated circuits as one or more computer programs running on one or more computers e.g. as one or more programs running on one or more computer systems as one or more programs running on one or more controllers e.g. microcontrollers as one or more programs running on one or more processors e.g. microprocessors as firmware or as virtually any combination thereof and that designing the circuitry and or writing the code for the software and or firmware would be well within the skill of one of ordinary skill in the art in light of this disclosure.

In addition those skilled in the art will appreciate that the mechanisms of taught herein are capable of being distributed as a program product in a variety of forms and that an illustrative embodiment applies equally regardless of the particular type of signal bearing media used to actually carry out the distribution. Examples of signal bearing media include but are not limited to the following recordable type media such as floppy disks hard disk drives CD ROMs digital tape and computer memory and transmission type media such as digital and analog communication links using TDM or IP based communication links e.g. packet links .

The various embodiments described above can be combined to provide further embodiments. To the extent that they are not inconsistent with the specific teachings and definitions herein all of the U.S. patents U.S. patent application publications U.S. patent applications foreign patents foreign patent applications and non patent publications referred to in this specification and or listed in the Application Data Sheet are incorporated herein by reference in their entirety. Aspects of the embodiments can be modified if necessary to employ systems circuits and concepts of the various patents applications and publications to provide yet further embodiments.

These and other changes can be made to the embodiments in light of the above detailed description. In general in the following claims the terms used should not be construed to limit the claims to the specific embodiments disclosed in the specification and the claims but should be construed to include all possible embodiments along with the full scope of equivalents to which such claims are entitled. Accordingly the claims are not limited by the disclosure.

