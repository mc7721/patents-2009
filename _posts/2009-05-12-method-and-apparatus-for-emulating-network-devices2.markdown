---

title: Method and apparatus for emulating network devices
abstract: Methods, apparatuses, data structures, and computer readable media are disclosed that perform emulated processing of packets communicated via a physical port between emulated network devices and real network devices. The emulated processing performs forward equivalence class classification on the packets. The forward equivalence class classification varies with the contents of the packets, and subsequent to the forward equivalence class classification the emulated processing varies with particular successful classifications resulting from the forward equivalence class classification.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09654303&OS=09654303&RS=09654303
owner: Spirent Communications, Inc.
number: 09654303
owner_city: San Jose
owner_country: US
publication_date: 20090512
---
The application claims the benefit of U.S. Provisional Patent Application No. 61 096 206 filed 11 Sep. 2008 titled METHOD AND DEVICE FOR EMULATING NETWORK DEVICES . The application s are incorporated by reference.

The application is related to U.S. Patent Application filed 30 May 2008 titled METHOD AND DEVICE USING TEST DATA STREAMS BOUND TO EMULATED DEVICES Ser. No. 12 130 944 U.S. Patent Application filed 30 May 2008 titled REAL TIME TEST RESULT PROMULGATION FROM NETWORK COMPONENT TEST DEVICE Ser. No. 12 130 963 and U.S. Patent Application filed 30 May 2008 titled METHOD AND APPARATUS FOR EMULATING NETWORK DEVICES . Ser. No. 12 130 584. The related applications are incorporated by reference.

The technology relates to scalable testing of complex networks and or complex network devices. Network test equipment to perform such useful scalable testing should emulate a large number and variety of network devices without artificial limits on the overall topology configuration and types of traffic.

Traffic types vary by supported network layer link layer and physical layer protocols such as Internet Protocol Generic Routing Encapsulation Ethernet Virtual Local Area Network 802.1q Multiprotocol Label Switching Point to Point Protocol over Ethernet Point to Point Protocol and Layer 2 Tunneling Protocol WiMAX Provider Backbone Bridge 802.1ah and Asynchronous Transfer Mode. Existing network test equipment places artificial limits on the types of emulated traffic in particular variable combinations of network layer link layer and physical layer protocols.

One prior approach to handling MPLS packets does not perform transmit forward equivalence class classification but rather is a shortcut which falls well short of transmit forward equivalence class classification. This shortcut combines a forward equivalence class that is static with dynamic binding of only the MPLS label. This shortcut does not perform forward equivalence class classification on packets for multiple reasons. Because the shortcut determines the static forward equivalence class information before the packets even exist the shortcut is not performing forward equivalence class classification transmit forward equivalence class classification requires that the packets exist prior to performing forward equivalence class classification and that the packet contents be analyzed to determine an IP address of a next hop router and an IP address of a resolving router. Instead this short cut requires that a human user manually specify FEC binding information in particular the IP address of a next hop router and the IP address of a resolving router. This requirement of manual entry by a human user is driven by the following consideration. When multiple transmit FEC classifications are required to transmit a packet the result of a subsequent FEC classification depends on the result of a prior FEC classification and thus may be performed correctly only with a correct method. Accordingly because this shortcut depends on FEC to label bindings at a particular time which may be changing manual entry by a human user is required. Dynamically assigning a label value to packets still does not perform forward equivalence class classification on packets. The fact that different labels are assigned does not change the static nature of the FEC to which it has been mapped.

Another prior approach to handling MPLS packets does not perform receive forward equivalence class classification but rather is a shortcut which falls well short of receive forward equivalence class classification. This prior approach simply throws away the MPLS label without accessing the forward equivalence class binding and without determining the forward equivalence class and next layer protocol from the binding. Instead this prior approach guesses the next layer protocol without use of the forward equivalence class binding. The prior approach assumes a valid FEC binding which may not even exist.

Methods apparatuses data structures and computer readable media are disclosed that perform emulated processing of packets communicated via a physical port between a group of emulated network devices and group of real network devices. The emulated processing performs forward equivalence class classification on the packets. The forward equivalence class classification varies with the contents of the packets. Subsequent to the forward equivalence class classification the emulated processing varies with particular successful classifications resulting from the forward equivalence class classification.

Examples of subsequent varying emulated processing are as follows. If there are multiple MPLS labels then the outcome of one FEC classification affects the next FEC classification. For receive a valid FEC binding must be known and if not known processing halts. Similarly the next layer protocol type and VPN disambiguation are other examples of subsequent varying emulated processing.

The successful classifications process the contents of the packets for forward equivalence class classification instead of discarding the contents of the packets.

The packets traverse the plurality of emulated network devices by traversing one or more encapsulated protocol stacks. The layers of the protocol stacks represent emulated network devices.

Forward equivalence class classification refers to both transmit forward equivalence class classification and receive forward equivalence class classification. Transmit forward equivalence class classification requires the use of packet contents resulting in assignment of a forward equivalence class binding which includes at least determination of an IP address of a next hop router and an IP address of a resolving router. Receive forward equivalence class classification requires the use of the MPLS label value to access the forward equivalence class binding and determining the next layer protocol.

In some embodiments the forward equivalence class classification is receive forward equivalence class classification of the packets received via the physical port from the group of real network devices.

The receive forward equivalence class classification performs inspection of the label values in the packets uses the label values to access forward equivalence class bindings determines a next layer protocol and varies the emulated receive processing subsequent to the forward equivalence class classification with the particular successful classifications of the forward equivalence class bindings.

The receive forward equivalence class classification handles reserved label values instead of ignoring the reserved label values. One such reserved label value is implicit null. The receive forward equivalence class classification handles reserved label values to determine a next layer protocol type.

In various embodiments the receive forward equivalence class classification associates a source MAC address of an encapsulated packet with an endpoint in a layer 2 virtual LAN associates a source MAC address in at least one of the packets with an endpoint in a Virtual Private LAN Service emulates a layer 2 switch MAC learning table on a layer 2 virtual LAN and or on a Virtual Private LAN Service uses the forward equivalence class bindings to disambiguate different layer 2 Virtual Private Networks and or to disambiguate different layer 3 Virtual Private Networks.

In some embodiments the forward equivalence class classification is transmit forward equivalence class classification of the packets transmitted via the physical port from the group of emulated network devices.

The transmit forward equivalence class classification performs inspection of the contents of the packets performs assignment of forward equivalence class bindings from the inspection of the contents of the packets and varies the emulated transmit processing subsequent to the forward equivalence class classification with the particular successful assignment of the forward equivalence class bindings.

The successful classifications determine an IP address of a next hop router and an IP address of a resolving router.

The transmit forward equivalence class classification handles reserved label values. One such reserved label value is implicit null.

In various embodiments the transmit forward equivalence class classification inspects upper layers of the packets for Quality of Service metrics inspects upper layer upper layers of the packets for time to live values selectively performs forward equivalence class classification in particular layers and selectively skips forward equivalence class classification in other particular layers performs Virtual Private LAN Service flooding performs static lookaside is performed on a simulated packet and or determines a next hop MAC address for lower layers of the packets.

With regard to Quality of Service metrics. te MPLS label has three bits reserved. Service providess have adopted the three bits for QoS. An ingress router picks certain metrics and assigns bits for QoS.

Static lookaside is for testing purposes. Despite a packet not normally being assigned to a particular label switched path manual FEC assignment can be performed.

A simulated packet is for user diagnostic purposes and doesn t have to be actually transmitted. For example with a device under test configuration errors or protocol implementation errors can be detected.

The label value 3 is defined as the implicit NULL label. LSRs can assign and distribute this label however it will never appear in actual packets instead it is implicitly there like an imaginary protocol layer. The receive side requires speculative classifications to imaginary FEC s and multiple dispatch of incoming packets. The transmit side can explicitly or implicitly classify to implicit NULL either way nothing is pushed on the packet. Implicit NULL classification allows a BGP connection to start on the wire as IP Eth and then switches to IP MPLS Eth once labels are bound.

VPLS complexities are described. Efficient L2 VPN operation requires MAC learning so that unicast packets are not flooded unnecessarily. After a receive side classification to a VPLS FEC the source MAC address is re associated with the originating endpoint.

VPLS flooding is described. During a flood the packet is sent to all VPN endpoints. Each flooded packet may take a different path through the core so this requires separate lower layer classifications.

In some embodiments the physical port is any of Ethernet Packet over Synchronous optical networking Packet over Synchronous Digital Hierarchy Asynchronous Transfer Mode and WiMAX.

In some embodiments encapsulation protocols of the plurality of encapsulated protocol stacks include at least one of Internet Protocol Generic Routing Encapsulation Ethernet Virtual Local Area Network 802.1q Multiprotocol Label Switching Point to Point Protocol over Ethernet Point to Point Protocol Layer 2 Tunneling Protocol WiMAX Provider Backbone Bridge 802.1ah and Asynchronous Transfer Mode.

Many embodiments emulate the packet sending process of a network device. Some embodiments process the packet with an encapsulated protocol stack corresponding to the network device and send the packet via the physical port. Some embodiments create the packet with a payload part and an additional part having space sufficient to store encapsulated protocol data added by encapsulated protocol stack processing.

Many embodiments emulate the packet receiving process of a network device. Some embodiments receive a packet via the physical port and process the packet with an encapsulated protocol stack corresponding to the network device. Some embodiments identify the encapsulated protocol stack based on at least sets of values corresponding to the encapsulated protocol stack. The sets of values specific to packet processing of particular encapsulation protocols.

Many embodiments emulate the broadcast packet receiving process of a network device. Some embodiments receive either a broadcast packet or a multicast packet via the physical port process the packet with an encapsulated protocol stack corresponding to the network device such that the encapsulated protocol stack is in a broadcast domain. This includes identifying the broadcast domain of only a subset of the encapsulated protocol stacks and based on the broadcast domain decreasing processing of the packet with encapsulated protocol stacks outside of the broadcast domain.

Some embodiments store statistics based on packets processed by the plurality of encapsulated protocol stacks.

Some embodiments emulate network layer communication of the plurality of network devices with a socket Application Programming Interface.

Various methods apparatuses data structures and computer readable media are directed to the disclosed embodiments.

The VIF manages operations such as send a packet and receive a packet. The VIF is a small structure representing a single protocol layer maintained and organized in operating system kernel memory. Examples of protocol layers are Internet Protocol e.g. versions 4 and 6 Generic Routing Encapsulation Ethernet e.g. 10 MBit s 100 MBit s 1 Gbit s 10 Gbit s Virtual Local Area Network 802.1q Multiprotocol Label Switching Point to Point Protocol over Ethernet Point to Point Protocol and Layer 2 Tunneling Protocol e.g. versions 2 and 3 WiMAX Provider Backbone Bridge 802.1ah and Asynchronous Transfer Mode e.g. adaptation layers 1 5 .

The VIF has a protocol value specifying the protocol type. The VIF also has a set of values specific to the protocol type. An exemplary XML template listing such sets of values follows 

The tree data structure allocates one node per VIF. The root node of the tree is a special VIF representing the physical interface PHY such as a port for Ethernet or a port for Packet over SONET SDH. In this particular view as a result of tree operations the tree grows down as children nodes representing encapsulation protocols are added to emulate network devices that do not exist physically. The tree has a depth equivalent to that of the tallest encapsulated protocol stack.

The process of sending a packet from an emulated device begins at a leaf node of the tree and the process of receiving a packet at an emulated device begins at the root node of the tree. All children nodes of a particular node are unique to prevent ambiguity about the recipient emulated device. In one embodiment to ensure such uniqueness the protocol specific set of values associated with each child node is unique with respect to the protocol specific set of values associated with all other peer nodes. A simple embodiment just assigns a unique name.

At any given node the collection of child nodes has properties of a red black tree such that the node can have any number of children. Accordingly child lookup has efficient performance of O logn with n being the number of potentially consulted nodes in the lookup.

Shown are the business layer logic BLL and instrument layer logic IL of a test device communicating with a device under test DUT . The test device includes hardware and software that implement features described herein. The test device may include one or more of logic arrays memories analog circuits digital circuits software firmware and processors such as microprocessors field programmable gate arrays FPGAs application specific integrated circuits ASICs programmable logic devices PLDs and programmable logic arrays PLAs . The hardware may be found in the chassis card rack or integrated unit. It may include or operate with the console or the general purpose computer in communication with the test device. The test device may include a number of separate units that are clustered together as shown in or remote from one another. For some levels of testing and some components of an overall test setup the test control may be implemented on a computer such as a personal computer server or workstation.

Typically the BLL has been hosted on a laptop or PC and provided a user interface and control for a test chassis that included both general purpose CPUs and FPGAs. The FPGAs have been dynamically configured to optimize test packet generation. Some combination of hardware supports the BLL and IL logic.

The IL logic depicts an operating system view divided into kernel space and user space. An exemplary division reserves kernel space for operating system kernel kernel extensions and some device drivers and permits user mode applications to reside in user space.

An ifsetup message sets up the interface and is shown in the figure sending requests from a protocol plug in in BLL to a VIF library in user space which in turn makes ioctl system calls to a dynamically loaded VIF kernel module in kernel space.

The kernel module creates the tree data structure as discussed in shown with a VIF representing the physical port as the root node. Also as shown the kernel module does not have to create a net device at each layer and instead creates one net device e.g. eth0 0 . . . eth0 xxx at each leaf node which supports the BSD socket API and can take advantage of any built in command line utilities of the operating system. Because the kernel model sandwiches protocol specific VIFs the kernel model hides complexity of the encapsulated protocols from the OS and upper layer utilities in the IL and BLL.

The operating system is non limiting and can be e.g. embedded Linux other Unix derivatives such as BSD VxWorks IOS by Cisco etc.

The process of sending a packet is described as follows. In the IL the data to be sent is generated by a protocol daemon. The socket API communicates the data to be sent to kernel space. Then within kernel space the socket abstraction one of the protocol stacks IP protocol stacks PF INET or PF INET packet driver PF PACKET sends a partially built packet from the emulated device. As the partially built packet is processed by each encapsulated protocol of the emulated device protocols headers are added until the packet is complete and ready to send via the physical port.

Some embodiments create partly formed packets with sufficient headroom to store additional header data added by each subsequent encapsulated protocol to prevent wasteful copying and reallocating of memory.

Some embodiments allow the MPLS encapsulated protocol PPPoE encapsulated protocol and the Ethernet encapsulated protocol to determine and communicate the destination address of a peer.

The process of receiving a packet follows oppositely ordered iterative steps of the sending process. However the receive process has the ambiguity about how a parent node determines which of multiple children nodes is an immediate destination following any processing by the parent node. This ambiguity is resolved by the VIF kernel module with the unique node data discussed in connection with . The particular encapsulated protocol of a candidate child node extracts key fields from the packet. If comparison between key fields of the received packet matches the unique data of a child node the encapsulated protocol continues processing such as validating the packet and removing header data corresponding to that encapsulated protocol. However if the match process fails then the packet is discarded.

Broadcast multicast packets are treated specially to prevent the prohibitive expense of repeated processing of the same packet by a large number of emulated devices.

In one mechanism a special case handler determines the broadcast domain of the packet and sends copies of the packet to only nodes that belong to that broadcast domain.

In another mechanism for Ethernet VLAN 802.1q a hash is consulted which was developed to determine whether any leaf nodes in the tree belong to the same broadcast domain. This hash prevents traversal of the entire tree.

1 Broadcast IPv4 packet IPv4 broadcasts are received one time at the first VIF in a broadcast domain.

3 Unicast IPv4 packet IPv4 unicasts are received by only the VIF with that address. Besides eliminating non broadcast domain packets this eliminates other leaf VIFs without that IP address.

ARP Address Resolution Protocol has a special rule as well. An ARP broadcast is received only at VIFs with matching IP addresses.

Some operating systems such as Linux allow the maintenance a net device multicast list. The multicast list may be consulted to eliminate VIFs outside that broadcast domain.

User interface input devices may include a keyboard pointing devices such as a mouse trackball touchpad or graphics tablet a scanner a touchscreen incorporated into the display audio input devices such as voice recognition systems microphones and other types of input devices. In general use of the term input device is intended to include all possible types of devices and ways to input information into computer system or onto computer network .

User interface output devices may include a display subsystem a printer a fax machine or non visual displays such as audio output devices. The display subsystem may include a cathode ray tube CRT a flat panel device such as a liquid crystal display LCD a projection device or some other mechanism for creating a visible image. The display subsystem may also provide non visual display such as via audio output devices. In general use of the term output device is intended to include all possible types of devices and ways to output information from computer system to the user or to another machine or computer system.

Storage subsystem stores the basic programming and data constructs that provide the functionality of certain embodiments. For example the various modules implementing the functionality of certain embodiments may be stored in storage subsystem . These software modules are generally executed by processor .

Memory subsystem typically includes a number of memories including a main random access memory RAM for storage of instructions and data during program execution and a read only memory ROM in which fixed instructions are stored. File storage subsystem provides persistent storage for program and data files and may include a hard disk drive a floppy disk drive along with associated removable media a CD ROM drive an optical drive or removable media cartridges. The databases and modules implementing the functionality of certain embodiments may be stored by file storage subsystem .

Bus subsystem provides a mechanism for letting the various components and subsystems of computer system communicate with each other as intended. Although bus subsystem is shown schematically as a single bus alternative embodiments of the bus subsystem may use multiple busses.

Computer readable medium can be a medium associated with file storage subsystem and or with network interface . The computer readable medium can be a hard disk a floppy disk a CD ROM an optical medium removable media cartridge or electromagnetic wave. The computer readable medium is shown storing program instructions performing the described technology.

Computer system itself can be of varying types including a personal computer a portable computer a workstation a computer terminal a network computer a television a mainframe or any other data processing system or user device. Due to the ever changing nature of computers and networks the description of computer system depicted in is intended only as a specific example for purposes of illustrating the preferred embodiments. Many other configurations of computer system are possible having more or less components than the computer system depicted in .

The VIF kernel module communicates with the interface manager of user space. The MPLS binder communicates with the interface manager. The MPLS Binder is discussed in detail below. MPLS information is exchanged via various protocols such as BGP LDP and RSVP with the system under test. Binding information is exchanged with an SQL database. The hardware generator generates packets to transmit based on the MPLS binder. Finally the MPLS binder communicates with the BLL.

The receive forward equivalence class classification performs inspection of the label values in the packets uses the label values to access forward equivalence class bindings determines a next layer protocol and varies the emulated receive processing subsequent to the forward equivalence class classification with the particular successful classifications of the forward equivalence class bindings .

The transmit forward equivalence class classification performs inspection of the contents of the packets performs assignment of forward equivalence class bindings from the inspection of the contents of the packets and varies the emulated transmit processing subsequent to the forward equivalence class classification with the particular successful assignment of the forward equivalence class bindings .

Various embodiments perform test equipment emulation of MPLS Label Switch Routers LSRs including networks of LSRs or devices behind LSRs hereafter MPLS networks carrying real world L2 L7 traffic. Various embodiments solve some combination of one or more of five problems that enable such emulation 

1. Emulated i.e. transmitted packets sourced from higher layer protocols may be classified as a member of a Forwarding Equivalency Class FEC based on a potential combination of source IP address destination IP address destination MAC address and Virtual Private Network identifier. Successful FEC classification allows packets to be tagged with a MPLS label value as a LSR would do in a real MPLS network. The results of FEC classification cannot be easily predicted a priori. FEC classification takes place on a per packet basis as packets are prepared for transmission.

2. Incoming i.e. received packets that are tagged with MPLS label values are classified as a member of a Forwarding Equivalency Class FEC based on a label to FEC lookup. Successful FEC classification allows packets to be fully received and processed in the correct context as a LSR would do in a real MPLS network. FEC classification takes place on a per packet basis as packets arrive at a network interface.

3. In MPLS networks packets may be tagged multiple times by multiple LSRs creating a stack of MPLS label values. Emulation of MPLS networks is facilitated by encapsulating each LSR s behavior and state into a MPLS virtual interface. Each MPLS virtual interface processes a single layer of the MPLS label stack. MPLS virtual interfaces may also be used as the substrate for other virtual interface types to enable emulation of L2 i.e. Ethernet VPNs or L3 i.e. Internet Protocol VPNs.

4. Currently ten different FEC types are defined IPv4 host IPv6 host IPv4 prefix IPv6 prefix IPv4 RSVP IPv6 RSVP IPv4 VPN Prefix IPv6 VPN Prefix VPLS and PWE3. Each FEC type is uniquely defined by a set of FEC specific configuration data. Emulation of MPLS networks requires that FEC information and MPLS label values are transmitted into the network and received from the network using a variety of protocols BGP RSVP LDP . FEC to label bindings must be established and subsequently configured updated and deleted in each MPLS virtual interface so that packet handling correctly emulates that of a real world MPLS network.

5. Emulation of real world MPLS networks requires a large number order of magnitude 10 6 of FECs. Relationships between emulated LSRs higher layer emulated protocols and the system under test may be very complex. When packet handling errors do occur they may be difficult for humans to diagnose. Each MPLS virtual interface maintains diagnostic information regarding failed classification attempts. FEC configuration data and MPLS label information are separately maintained in an embedded SQL database. Both the MPLS VIF diagnostic information and SQL database are visible to higher layers of the Spirent TestCenter system software so the information may in turn be made available in GUI or programmatic forms.

It was previously impossible for test equipment to correctly transmit MPLS tagged packets where the destination IP address or destination Ethernet address was variable. MPLS emulation was only possible in situations where the addresses were static and thus transmit FEC classification could be performed a priori. Similarly received packets could arrive with any combination of MPLS label values. Lacking a mechanism for per packet FEC classification these packets could only be minimally processed. It was not possible to emulate control plane protocols over MPLS networks.

Some embodiments take advantage of the virtual interface technology to encapsulate FEC state and LSR behavior for a single layer of the MPLS label stack.

Some embodiments include a novel algorithm for transmit FEC classification where any given packet may be classified as belonging to one of ten different FEC types.

Some embodiments include technology that enables emulation of L2 and L3 VPNs with potentially overlapping addressing schemes e.g. overlapping subscriber IP address spaces.

Some embodiments maintain large amounts of FEC configuration and diagnostic information in an embedded SQL database that can be easily accessed. Powerful SQL query tools speed debugging and fault isolation.

Without this technology of MPLS networks one of ordinary skill would implement carrying real world L2 L7 traffic by actually procuring and provisioning MPLS LSRs as part of the test equipment despite the large capital costs involved difficultly of configuring and controlling such equipment lack of vendor neutrality and inability to isolate a specific device in the test.

Simplified control plane over MPLS concepts can also be used for control plane over WiMax. On WiMax interfaces selection of transport CID is based on destination IP address and potentially other IP header fields ToS .

Routing s binder maintains an embedded SQL database of all bindings. Each MPLS VIF is configured with a subset of bindings.

 2 The MAC address of the next hop router is only significant for the outer most label stack entry LSE 

Currently there are ten FEC types specified IPv4 IPv6 Host IPv4 IPv6 Prefix IPv4 IPv6 RSVP IPv4 IPv6 VPN Prefix VPLS and PWE3.

Host FEC types are implemented as a special case of Prefix FEC types with a prefix length of 32 or 128 bits for IPv4 and IPv6 respectively . PWE3 FEC types are implemented as a special case of VPLS FEC types with a single endpoint identifier.

Partially built packets that are presented to an MPLS VIF for transmit processing may have come from any number of sources 

The primary transmit responsibility of a MPLS VIF is FEC classification and subsequent labeling of the packet with a MPLS label stack entry LSE .

Transmit FEC classification varies with the FEC type. Generally classification requires a lookup based on packet contents such as data or meta data e.g. longest prefix match on destination source destination address pair match and destination MAC address endpoint ID lookup. Because there are different FEC types each with their own requirements the transmit algorithm is guided by characteristics of the higher layer interfaces that produced the packet 

2. Assertion The partially built packet came from a MPLS VIF or IP interface and has accessible IP address information in its packet meta data.

4. Check for a static mapping of IP source destination address to FEC. If a mapping exists go to step 8 below.

5. Attempt RSVP FEC classification see RSVP FEC section below for details. If classification succeeds go to step 8 below.

6. Attempt Prefix FEC classification see Prefix FEC section below for details. If classification succeeds go to step 8 below.

7. If the previous protocol layer was not MPLS assume an implicit NULL match pass the unmodified packet to the next layer protocol for processing. If the previous protocol layer was MPLS drop the packet ENETDOWN .

8. FEC classification succeeded push a LSE onto the packet using the bound label value. Update packet metadata resolving router address becomes IP source next hop address becomes IP destination . Pass the packet to the next layer protocol for processing.

When an MPLS VIF is presented with an incoming packet the primary responsibility of the MPLS VIF is FEC classification and subsequent stripping of the outer most label stack entry LSE .

FEC classification is implemented as a simple verification that the label value is currently bound to a FEC. As long as this is true the LSE will be stripped and the packet can be forwarded to the next layer VIF for processing. If the label value is not currently bound the packet is dropped i.e. it was misrouted .

The MPLS VIF implements receive classification using a simple label lookup. As long as the incoming label value is bound to a FEC the label stack entry is stripped and packet processing can continue. The Next layer protocol type is determined by the S bit as follows 

There is also a special case of receive side processing that is not actually implemented in the MPLS VIF but has that appearance. While in the VIF module s packet processing loop 

This special case handler facilitates implicit NULL label matches at the top of MPLS label stack but prevents back to back MPLS interfaces from matching the implicit NULL label.

 1 The route distinguisher differentiates VPN Prefix FECs that route to the same destination in the same VPN

Depending on what specific FEC types are configured additional structures will need to be maintained. Most of these are used for FEC classification during transmit however some entries e.g. VPLS endpoint id MAC address mappings may also be updated during receive.

Rx FEC information obtained from the BLL data model will be applied from the BLL to the IL via routing specific messages and not via ifsetup 1 messages

With all FEC label binding information provided by the routing IL components it is problematic to run control plane over statically i.e. administratively configured tunnels

MPLS control plane protocols will manage FEC label bindings via IfMgrClient API calls yet to be specified

VPLS FECs has difficulty with learning MAC addresses that are received only in signature frames since signature tagged packets are not seen on the cut through channel 

In the basic operation of the binder client code can register observers to be notified of changes as they happen. A protocol that negotiates labels updates and deletes FEC to label bindings. When this happens observers are notified about the change so they can react accordingly. Client code can also query the current bindings directly.

In one embodiment the binder services two clients. The Generator generates line rate stateless data plane traffic. In some configurations it requires dynamically bound MPLS labels for FECs known at configuration time. The VIF kernel module handles encapsulation for all stateful traffic generated by content daemons and kernel stacks. In some configurations it requires dynamically bound MPLS labels for FECs not known until the packet needs to be encapsulated.

The binder uses an embedded database as its main data store. The central data that the binder deals with are FEC to label bindings. A binding has the following data fields 

A session handle direction and FEC uniquely identify a FEC to label binding. The rest of the fields are meta information associated with the binding that are needed by some clients. For storage efficiency this data is split up in multiple tables as follows.

Each FEC type has its own table that associates it with a FEC id. FEC ids are used both for compression and uniform representation in other database tables.

RSVP Tunnel endpoints are stored in a separate table because they are uniquely determined by the Tunnel ID and session regardless of the LSP ID. This eases storage overhead significantly.

And finally to pull it all back together the binder has two tables for label storage. The first is for labels that are received from a remote peer and the second is for labels that are advertised to remote peers.

The binder has a simple API that it presents to protocols. There are 3 different things a protocol can do.

i They can update a FEC to label binding. If the binding did not already exist then Ids are generated and data is inserted into the tables. If the binding already existed the Ids are found then non key fields are updated in the tables. In either case observers are notified of change and generated Ids.

ii They can remove a FEC to label binding. The generated Ids are found the information is removed from the label tables and the observers are notified of the removal by Ids only.

iii They can remove all FEC to label bindings associate with a session Id. This is a convenience routine for when the entire protocol session goes down. It will remove all the bindings for that session and then notify observers in the same way it would with a regular removal.

The majority of communication from the label binder to clients should be through the observer. The observer has two delegates that need to be overridden by the clients. The update delegate will be called with all Ids binding information and meta info while the remove delegate will be called only with Ids and a direction. In addition to the observer notifications clients can make the following API calls 

In order for the Generator to transmit some of its traffic it needs dynamically bound MPLS labels to known FECs. The BLL will configure blocks of FECs to the client that the Generator needs. As these blocks resolve the client will send messages to the Generator so it can insert the labels into its traffic. Also the client will send periodic status updates to the BLL so it can determine when all labels are resolved. Optionally the BLL can request all of resolved labels for the subscriptions.

The BLL can configure the client with subscriptions to FECs. Each configured subscription has a protocol session ID a block of FECs and a subscription ID. The protocol session ID is the ID of the protocol that must resolve the FECs. If the same FEC is resolved by a different session it is ignored by this subscription. The subscription ID is a common ID known to the BLL the client and the Generator and it is used to identify the subscription in all communications between the three processes.

Subscriptions in the Generator client are fairly simple. Each has a subscription ID a session ID and FEC IDs produced by the Binder from the configured FEC blocks. The FEC IDs are kept with a boolean flag indicating whether or not it is resolved. These FEC IDs are kept in a sequential list corresponding to the order in which they appeared in the FEC block. There s also an index on this list by FEC ID to allow fast updating of resolved status. In addition the subscription object keeps track of how many FECs are resolved and if it has been bound before.

The VIF client has the responsibility of making sure that the VIF kernel module receives all the FECs it needs. The BLL configures mappings from device handles to VIF identifiers. The client simply relays all bindings for a device to that VIF. There are also static mappings that can be configured. These are mappings from IP source and destination pairs to an arbitrary FEC. Finally the client relays Tx diagnostic requests from the BLL to the VIF kernel module.

The BLL configures mappings from device IDs to VIF identifiers. Any FEC binding associated with the device ID is updated to the VIF module via an IfMgr API. With each mapping and optional filter is also configured. The filter will ignore certain types of FECs dependent on what s needed to support the topology. The BLL can also configure static FEC mapping. These mappings configure a source and destination IP pair to an arbitrary FEC.

Once configured the client searches the database and updates the VIF module with all matching resolved FEC bindings. As protocols update the database with new FEC bindings or delete old FEC bindings the client will observe these changes and update IfMgr accordingly. The client will update VIFs if the FEC bindings match the corresponding filter. There are three ways to update a FEC binding to the IfMgr 

When the client receives a handle for a FEC binding that matches a FEC for a configured static mapping then that static mapping is configured in the VIF through IfMgr. That static mapping is then associated with that handle. If that FEC binding is ever removed the static mapping is removed first.

Transmit diagnostics were implemented to assist the user in debugging a faulty configuration setup. The idea is to simulate a packet being transmitted through the VIF stack and record everything that happens. The goal is that the user will see what MPLS labels the packet would receive on its way through the stack and what FECs it matched to get those labels or why it failed to transmit.

The BLL will send a IP address source and destination pair or a destination MAC address along with a VIF identifier to the client. The client will then in turn translate it to the appropriate request for IfMgr. The IfMgr will respond with a list of either successful resolutions with binding handles or a reason why classification failed. If the classification was successful then the client uses the returned handle to populate a message with the FEC information and label value. If the classification was not successful then the client constructs a message with the reason why to send to the BLL. The reasons a classification could fail would be that there was no match or that it would flood into an L2 VPN. Once all responses are handled from IfMgr the client will respond to the BLL with a list of the constructed messages.

While the present invention is disclosed by reference to the preferred embodiments and examples detailed above it is to be understood that these examples are intended in an illustrative rather than in a limiting sense. It is contemplated that modifications and combinations will readily occur to those skilled in the art which modifications and combinations will be within the spirit of the invention and the scope of the following claims.

