---

title: System and method for anonymous addressing of content on network peers and for private peer-to-peer file sharing
abstract: A system and method for efficient and private peer-to-peer file sharing consists of ascribing a uniquely identified and anonymous link (an “edgelink”) to any file or set of files on a peer computer. The link is registered with a publishing server along with continuously updated connectivity information about the peer without registering any identifying information about the file. A peer recipient is able to access the link, receive connectivity information about the publishing peer from the server, and then receive the file from the publishing peer without file content passing through the server, mediating any intermediary NAT devices without requiring any manual or automatic device reconfiguration.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09112875&OS=09112875&RS=09112875
owner: 
number: 09112875
owner_city: Ottawa, ON
owner_country: CA
publication_date: 20090804
---
This invention pertains to the field of electrical computers and digital processing systems and in particular file sharing systems and specifically a system and a method for anonymous addressing of content stored on computers at the edge of the network. This is coupled with a system and method for the private peer to peer exchange of anonymously addressed content.

Client server is a computing architecture which separates a client from a server and is almost always implemented over a computer network. Each client or server connected to a network can also be referred to as a node. The most basic type of client server architecture employs only two types of nodes clients and servers. This type of architecture is sometimes referred to as two tier. It allows devices to share files and resources.

Each instance of the client software can send data requests to one or more connected servers. In turn the servers can accept these requests process them and return the requested information to the client.

A peer to peer P2P computer network exploits diverse connectivity between participants in a network and the cumulative bandwidth of network participants rather than conventional centralized resources where a relatively low number of servers provide the core value to a service or application. Peer to peer networks are typically used for connecting nodes via largely ad hoc connections.

A pure peer to peer network does not have the notion of clients or servers but only equal peer nodes that simultaneously function as both clients and servers to the other nodes on the network. This model of network arrangement differs from the client server model where communication is usually to and from a central server. A typical example for a non peer to peer file transfer is an FTP server where the client and server programs are quite distinct and the clients initiate the download uploads and the servers react to and satisfy these requests.

The first generation of peer to peer file sharing networks had a centralized file list. In the centralized peer to peer model a user would send a search to the centralized server of what they were looking for. The server then sends back a list of peers that have the data and facilitates the connection and download.

The first file sharing programs marked themselves by inquiries to a server either the data to the download held ready or in appropriate different Peers and so called Nodes further obtained so that one could download there. Two examples were Napster today using a pay system and eDonkey2000 in the server version.

Justin Frankel of Nullsoft set out to create a network without a central index server and Gnutella was the result. Unfortunately the Gnutella model of all nodes being equal quickly died from bottlenecks as the network grew from incoming Napster refugees. FastTrack solved this problem by having some nodes be more equal than others .

By electing some higher capacity nodes to be indexing nodes with lower capacity nodes branching off from them FastTrack allowed for a network that could scale to a much larger size.

Gnutella quickly adopted this model and most current peer to peer networks implement this design as it allows for large and efficient networks without central servers.

Also included in the second generation are distributed hash tables DHTs which help solve the scalability problem by electing various nodes to index certain hashes which are used to identify files allowing for fast and efficient searching for any instances of a file on the network. This is not without drawbacks perhaps most significantly DHTs do not directly support keyword searching as opposed to exact match searching .

The best examples are Gnutella Kazaa or eMule with Kademlia whereby Kazaa has still a central server for logging in.

The third generation of peer to peer networks has anonymity features built in. Examples of anonymous networks are ANts P2P RShare Freenet I2P GNUnet and Entropy.

A degree of anonymity is realized by routing traffic through other users clients which have the function of network nodes. This makes it harder for someone to identify who is downloading or who is offering files. Most of these programs also have strong encryption to resist traffic sniffing.

Friend to friend networks only allow already known users also known as friends to connect to the user s computer then each node can forward requests and files anonymously between its own friends nodes.

Third generation networks have not reached mass usage for file sharing because most current implementations incur too much overhead in their anonymity features making them slow or hard to use.

BitTorrent is a peer to peer file sharing P2P communications protocol. BitTorrent is a method of distributing large amounts of data widely without the original distributor incurring the entire costs of hardware hosting and bandwidth resources. Instead when data is distributed using the BitTorrent protocol each recipient supplies pieces of the data to newer recipients reducing the cost and burden on any given individual source providing redundancy against system problems and reducing dependence on the original distributor.

A BitTorrent client is any program that implements the BitTorrent protocol. Each client is capable of preparing requesting and transmitting any type of computer file over a network using the protocol. A peer is any computer running an instance of a client.

To share a file or group of files a peer first creates a torrent. This small file contains metadata about the files to be shared and about the tracker the computer that coordinates the file distribution. Peers that want to download the file first obtain a torrent file for it and connect to the specified tracker which tells them from which other peers to download the pieces of the file.

Though both ultimately transfer files over a network a BitTorrent download differs from a classic full file HTTP request in several fundamental ways 

First BitTorrent makes many small P2P requests over different TCP sockets while web browsers typically make a single HTTP GET request over a single TCP socket. Second BitTorrent downloads in a random or in a rarest first approach that ensures high availability while HTTP downloads in a sequential manner.

Taken together these differences allow BitTorrent to achieve much lower cost much higher redundancy and much greater resistance to abuse or to flash crowds than a regular HTTP server. However this protection comes at a cost downloads can take time to rise to full speed because it may take time for enough peer connections to be established and it takes time for a node to receive sufficient data to become an effective uploader. As such a typical BitTorrent download will gradually rise to very high speeds and then slowly fall back down toward the end of the download. This contrasts with an HTTP server that while more vulnerable to overload and abuse rises to full speed very quickly and maintains this speed throughout.

FTP is used to transfer data from one computer to another over the Internet or through a network. Specifically FTP is a commonly used protocol for exchanging files over any network that supports the TCP IP protocol such as the Internet or an intranet . There are two computers involved in an FTP transfer a server and a client. The FTP server running FTP server software listens on the network for connection requests from other computers. The client computer running FTP client software initiates a connection to the server. Once connected the client can do a number of file manipulation operations such as uploading files to the server download files from the server rename or delete files on the server and so on.

UDP is one of the core protocols of the Internet protocol suite. Using UDP programs on networked computers can send short messages sometimes known as datagrams using Datagram Sockets to one another. UDP is sometimes called the Universal Datagram Protocol.

UDP does not guarantee reliability or ordering in the way that TCP does. Datagrams may arrive out of order appear duplicated or go missing without notice. Avoiding the overhead of checking whether every packet actually arrived makes UDP faster and more efficient at least for applications that do not need guaranteed delivery.

HTTP is a communications protocol used to transfer or convey information on intranets and the World Wide Web. HTTP is a request response protocol between a client and a server. The client making an HTTP request such as a web browser spider or other end user tool is referred to as the user agent. The responding server which stores or creates resources such as HTML files and images is called the origin server. In between the user agent and origin server may be several intermediaries such as proxies gateways and tunnels. HTTP is not constrained to using TCP IP and its supporting layers although this is its most popular application on the Internet.

Typically an HTTP client initiates a request by establishing a Transmission Control Protocol TCP connection to a particular port on a host. An HTTP server listening on that port waits for the client to send a request message.

Upon receiving the request the server sends back a status line such as HTTP 1.1 200 OK and a message of its own the body of which is perhaps the requested file an error message or some other information.

Resources to be accessed by HTTP are identified using Uniform Resource Identifiers URIs or more specifically Uniform Resource Locators URLs using the http or https URI schemes.

CURIE a compact URI is an abbreviated URI expressed in CURIE syntax and may be found in both XML and non XML grammars. An example CURIE is curl EA83BZ99 excluding the quotation marks.

NAT devices allow internal networks to communicate with external networks using a limited number of external IP Addresses by changing the source address of outgoing requests and listening for replies. This leaves the internal network ill suited to act as a server as the NAT device has no way of determining the internal host for which incoming packets are destined. On the Internet this problem has not generally been relevant to home users behind NAT devices as they either do not need to act as servers or can use static NAT mappings to correlate incoming requests to internal hosts. However applications such as P2P file sharing such as BitTorrent or Gnutella clients or VoIP networks such as Skype require clients to act like servers thereby posing a problem for users behind NAT devices as incoming requests cannot be correlated to the proper internal host.

A possible solution to this problem is to use NAT traversal techniques using protocols such as STUN Simple Traversal of UDP or ICE Interactive Connectivity Establishment or proprietary approaches in a session border controller. NAT traversal is possible in both TCP and UDP based applications but the UDP based technique is simpler more widely understood and more compatible with legacy NATs. In either case the high level protocol must be designed with NAT traversal in mind and it does not work reliably across symmetric NATs or other poorly behaved legacy NATs.

Instant messaging IM is a form of real time communication between two or more people based on typed text. The text is conveyed via computers connected over a network such as the Internet. Files may also be transferred to users via an IM client.

IM is built around the concept of real time synchronous messaging. For example I send a message intended for you right now.

A Social Network or Social Graph e.g. Facebook is a social structure made of nodes which are generally individuals or organizations that are tied by one or more specific types of interdependency such as values visions idea financial exchange friends kinship dislike conflict trade web links sexual relations disease transmission epidemiology or airline routes.

RSS is a family of Web feed formats used to publish frequently updated content such as blog entries news headlines or podcasts. An RSS document which is called a feed web feed or channel contains either a summary of content from an associated web site or the full text. RSS makes it possible for people to keep up with their favorite web sites in an automated manner that s easier than checking them manually.

Media RSS MRSS is an RSS module used for syndicating multimedia files audio video and image in RSS feeds. It was designed in 2004 by Yahoo and the Media RSS community and adds several enhancements to RSS enclosures.

In computer and telecommunications networks presence information is a status indicator that conveys ability and willingness of a potential communication partner for example a user to communicate. A user s client provides presence information presence state via a network connection to a presence service which is stored in what constitutes his personal availability record called a presentity and can be made available for distribution to other users called watchers to convey his availability for communication. Presence information has wide application in many communication services and is one of the innovations driving the popularity of instant messaging or recent implementations of voice over IP clients.

Universal Plug and Play UPnP is a set of computer network protocols promulgated by the UPnP Forum. The goals of UPnP are to allow devices to connect seamlessly and to simplify the implementation of networks in the home data sharing communications and entertainment and corporate environments. UPnP achieves this by defining and publishing UPnP device control protocols built upon open Internet based communication standards.

The term UPnP is derived from Plug and play a technology for dynamically attaching devices to a computer directly. UPnP enables communication between any two devices under the command of any control device on the network LAN .

The UPnP architecture supports zero configuration invisible networking and automatic discovery for many device categories from a range of vendors any device can dynamically join a network obtain an IP address announce its name convey its capabilities upon request and learn about the presence and capabilities of other devices. DHCP and DNS servers are optional and are only used if they are available on the network. Devices can leave the network automatically without leaving any unwanted state information behind.

The foundation for UPnP networking is IP addressing. Each device must have a Dynamic Host Configuration Protocol DHCP client and search for a DHCP server when the device is first connected to the network. If no DHCP server is available that is the network is unmanaged the device must assign itself an address. If during the DHCP transaction the device obtains a domain name for example through a DNS server or via DNS forwarding the device should use that name in subsequent network operations otherwise the device should use its IP address.

Broadcatching is the downloading of digital content that has been made available over the Internet using RSS syndication.

The general idea is to use an automated mechanism to aggregate various web feeds and download content for viewing or presentation purposes.

The present invention provides for a system and method for efficient and private peer to peer file sharing. The system consists of means to ascribe a uniquely identified and anonymous link an edgelink to any file or set of files on a peer computer means for registering the link with a publishing server along with continuously updated connectivity information about the peer without registering any identifying information about the file and means for a peer recipient to access the link receive connectivity information about the publishing peer from the server and then receive the file from the publishing peer without file content passing through the server mediating any intermediary NAT devices without requiring any manual or automatic device reconfiguration.

The invention further provides a system for creating private peer to peer file sharing networks comprising means to integrate an external set of social graphs and build private groups of individuals through an assembly or invitation process means to aggregate uniquely identified and anonymous links to files stored on peer nodes computers belonging to individuals within the group within the private group means for a peer recipient to access the link and receive the file from the publishing peer without file content passing through the server mediating any intermediary NAT devices without requiring any manual or automatic device reconfiguration.

In one embodiment of the invention the system for peer to peer filing sharing further comprises a social network layer.

In another embodiment of the invention the system for peer to peer file sharing further comprises means for security options that require peers to authenticate prior to the release of identifying connectivity information.

In yet another embodiment of the invention the system for peer to peer file sharing further comprises a swarming protocol to allow wide scale distribution of published content.

In still another embodiment of the invention the system for peer to peer file sharing further comprises a link syndication capability for a peer to publish an automatically updated list of files that enables other users to subscribe to content feeds streams and get notified of changes and newly shared files.

In one embodiment of the invention the system includes the means to index search through browse and comment on published links.

In another embodiment of the invention the system includes a policy engine to control access to published links.

In yet another embodiment of the invention the system includes a buddy list that allows a user to maintain a contact list of friends co workers and other contacts and to selectively send link to all or a specific subset of those contacts.

In one embodiment of the invention the system provides a Public key Cryptography Scheme for uniquely identifying peers and securing P2P transfers at all points between publishing a link subscribing to a link and transferring files.

In another embodiment of the invention the system includes means to temporarily or permanently publish the content referenced by a link to a central server.

In one embodiment of the invention there is provided a system and method for peer to peer file sharing.

In one embodiment of the invention there is provided a system for peer to peer file sharing comprising 

The invention is a novel system and method for P2P file sharing and consists of means for a user to publish aURL or CURIE style link edgelink to a file on his or her peer computer. As part of the publishing process the edgelink is registered with a central publishing server. Along with this link additional connectivity information including file presence is stored on the central server to facilitate the process of connectivity establishment and NAT transversal between peers. Connectivity and NAT information are periodically republished by the publishing peer to ensure the information is current.

When a recipient clicks on the link the registered publishing server is contacted the server sends additional connectivity information to the peer and automatically negotiates a path through any intermediary NATs firewalls routers or similar devices without sending control signals to any of those intermediary devices e.g. No UPnP messages delivered to any intermediary devices . This enables the recipient peer to connect directly to the publishing peer and transfer the file without relaying or proxying the file content or passing though any central servers.

Referring to there is illustrated a High level Schematic of Peering System of one embodiment of the invention. It has six basic functioning modules a Peer Client a Publishing Server a Database Server a Web Server a PKI Server and a Swarming Server . Not shown are typical system components including system administrative functions privacy protection functions user setup and run execution functions reporting services input and output devices and backup systems. Not specifically disclosed but would be obvious to one skilled in the art are provisions of interfaces and services. Also not shown or described are all references to the Database Server as these would be obvious to anyone skilled in the art.

The Peer Client runs continuously on a peer node. It authenticates and communicates its connectivity information periodically with the Publishing Server . It negotiates direct connections to other peers for exchange files directly without relaying through a central server. Direct connection negotiation is mediated by the Publishing Server using the STUN Simple Transversal of UDP over NATs UDP NAT transversal algorithm. As an alternative one could use the TURN Transversal Using Relay NAT however that would relay all data through a central server obviating the benefits of P2P and incurring significant network bandwidth cost. One could alternatively also use the TCP protocol however it is not technically feasible to mediate connectivity establishment and NAT transversal thereby preventing direct P2P file transfer.

When a peer publishes a new link to a file or group of files the Peer Client requests an edgelink in URL or CURIE syntax. The Publishing Server generates the edgelink using a one way irreversible hashing algorithm. The Peer Client accepts the edgelink and sends its security access permissions to the Publishing Server . The security permissions denote who can request the content and for how long. Security permissions are stored with the edgelink in the Database Server . The Publishing Server communicates with the Web Server to create a unique HTML or equivalent e.g. Flash webpage preview of the file s called the prepage . Optional text audio images or video are embedded in the webpage depending on the security permissions of the edgelink.

The Peer Client periodically updates Presence and Connectivity information with the Publishing Server to facilitate direct connection mediation. Unlike standard web URLs today it is impossible for a malicious user to use the published edgelink to determine the type of content or location of the peer sharing the content. Since presence and connectivity information is not mapped inside the edgelink it is impossible to discover anything from the edgelink without contacting the Web Server . Any requests to the Web Server must pass the specified security permissions for the edgelink.

To prevent identity impersonation each Peer Client generates a public private key pair unique to each user device pair. The public key is transmitted to the PKI Server . The private key is never transmitted to any server. The PKI Server stores the public key for every user device pair. When a Peer Client is installed on a new device for an existing user the user undergoes a challenge process to ensure legitimacy of the new user device peer. The challenge process is not specifically described but would be obvious to a person skilled in the art. Devices in this case can be PCs servers laptops phones or any Internet capable device.

A new file transfer is initiated by opening an edgelink. The first step is to satisfy the specified security permissions tied to the edgelink. Security permissions may consist of one or more shared keys shared secrets email challenge response authentication or social graph identity verification e.g. through Facebook Connect . The Publishing Server then relays the public key of the initiating Peer Client requesting access to the file to the publishing Peer Client . The initiating Peer Client relays a message digest and digital signature generated cryptographically using its private key to the publishing Peer Client . The Publishing Server then mediates a secured and direct connection through intermediary NAT devices following a NAT transversal algorithm e.g. STUN or ICE . Once a direct connection is established the initiating Peer Client reconfirms its identity by transmitting a digital signature generated using its private key.

The Swarming Server is used for edgelinks without security permissions that are publicly accessible for download. It implements a modified swarming protocol supporting NAT transversal e.g. BitTorrent over UDP to replicate and distribute large files to a large number of peers. The implementation can be used for Broadcatching or wide distribution. Protocol encryption e.g. Message stream and protocol encryption or MSE PE is used to prevent a man in the middle attack. Encryption keys are encrypted and exchanged using the PKI Server public keys. The details of this implementation should be obvious to one with skills in the art.

The Social Server in is used to import a social graph from a 3party service e.g. Facebook MySpace Google etc . The Social Server publishes an HTML interface enabling any authenticated peer to bind their social identity with their filesharing identity creating a social peer . Any social peer can create their own privnet. Once a privnet is created a social peer can invite any other directly linked connections in the social graph. Invited peers accept the invitation effectively binding them to the privnet. The Social Server contacts the Publishing Server to compile a database of all peer edgelinks in each privnet.

The Social Server publishes an HTML interface or equivalent e.g. Flash Silverlight for each privnet accessible to any authenticated social peers. Using a standard user agent as a standalone browser or embedded within the Peer Client a social peer can browse search and interact with edgelinks. For example a social peer can browse all edgelinks from another social peer search for specific text contained within the edgelink prepage interact with the edgelink prepage and leave comments directly to the edgelink prepage. The Social Server provides HTML interfaces via HTTP and stores any interactions in its database. The exact mechanisms for these web interactions should be obvious to one skilled in the art.

The social peer can request to download the file directly from prepage by clicking the edgelink. The download process then ensues as a P2P direct transfer as described in Example 1.

The user selects a file folder or group of files on their computer for publishing as a URL or CURIE style link. The user defines the access permissions for that file. E.g. the user specifies a password the number of times the file can be downloaded or the specific identities of the user s that can download the file. As part of the publishing process a link is requested from the central publishing server. The publishing server generates a unique URL or CURIE for the file and sends it back to the user. The generated link has no relation to the file itself and so cannot be brute forced hacked to figure out the name or type of file being shared. After receiving the link the following information is sent and stored on the central server 

The user maintains a persistent connection with the publishing server and periodically updates presence information. The publisher server creates a unique web page publishing the edge link information included real time updated presence.

The recipient receives an edge link via a web medium e.g. email search social network IM . Clicking the edge link opens up a web page with the information published by the user including presence status. The recipient requests the file s through the registered publishing server providing the necessary authentication credentials if required. The publishing server exchanges connectivity information for the user and recipient. It negotiates a direct connection between the user and recipient through any intermediary NATs firewalls routers or similar devices following a connectivity establishment protocol e.g. ICE STUN TURN . This enables the recipient peer to connect directly to the publishing peer and transfer the file without the file content passing through the server.

A social graph can be added to Examples 1 and 2 to enable a user to browse or search for shared files in his social network. The user creates a group and selects the identities of members in his social network to invite. The publisher server creates a unique edge link for the group and associates the unique identity of each member to the group. The publishing server creates a web page for the group. Access permissions are optionally restricted to the identities of invited members. The user or an invited member selects a file folder or group of file s to publish into the group. The file s and or folder s are published as in Example 1. For each file or folder the publishing server adds a link to the group web page. The link is indexed and tagged appropriately enabling other members of the group to browse and search through the links. An invited member browses the group and clicks on a link provided by the user or another member of the group. The file s and or folder s are downloaded as in Example 2. The invited member or user leaves a comment about the file and publishes his activity. The publisher server attaches the comment to the appropriate link and publishes the activity to the web page for the group.

A method is provided for creating a system for peer to peer file sharing comprising the following steps 

A method for creating a private peer to peer file sharing network is provided comprising the following steps 

The description above is not to be construed as limiting the scope of the invention but merely as providing illustrations and examples of some of the presently preferred embodiments of this invention. Thus the scope of the invention should be determined by the appended claims and their legal equivalents rather than by the examples given.

