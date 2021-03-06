---

title: Rotating encryption in data forwarding storage
abstract: A method includes receiving a request from a source system to store data, directing the data to a computer memory, the computer memory employing an encryption scheme, and continuously forwarding the data from one computer memory to another computer memory in the network of interconnected computer system nodes without storing on any physical storage device in the network, each computer memory employing the encryption scheme. The continuously forwarding includes determining an address of a node available to receive the data based on one or more factors, sending a message to the source system with the address of a specific node for the requester to forward the data, detecting a presence of the data in memory of the specific node, and forwarding the data to another computer memory of a node in the network of interconnected computer system nodes without storing any physical storage device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08489687&OS=08489687&RS=08489687
owner: Tajitshu Transfer Limited Liability Company
number: 08489687
owner_city: Wilmington
owner_country: US
publication_date: 20090925
---
This application is a U.S. National Phase of International Application No. PCT US2009 058362 filed Sep. 25 2009 which is a continuation of U.S. patent application Ser. No. 12 240 951 filed Sep. 29 2008 now U.S. Pat. No. 7 636 759 entitled ROTATING ENCRYPTION IN DATA FORWARDING STORAGE each of which is hereby expressly incorporated by reference in its entirety.

At least some embodiments disclosed herein relate to data storage and more particularly to rotating encryption in data forwarding storage.

The volume of data that must be stored by individuals organizations businesses and government is growing every year. In addition to just keeping up with demand organizations face other storage challenges. With the move to on line real time business and government critical data must be protected from loss or inaccessibility due to software or hardware failure. Today many storage products do not provide complete failure protection and expose users to the risk of data loss or unavailability. For example many storage solutions on the market today offer protection against some failure modes such as processor failure but not against others such as disk drive failure. Many organizations are exposed to the risk of data loss or data unavailability due to component failure in their data storage system.

The data storage market is typically divided into two major segments i.e. Direct Attached Storage DAS and Network Storage. DAS includes disks connected directly to a server.

Network Storage includes disks that are attached to a network rather than a specific server and can then be accessed and shared by other devices and applications on that network. Network Storage is typically divided into two segments i.e. Storage Area Networks SANs and Network Attached Storage NAS .

A SAN is a high speed special purpose network or subnetwork that interconnects different kinds of data storage devices with associated data servers on behalf of a larger network of users. Typically a SAN is part of the overall network of computing resources for an enterprise. A storage area network is usually clustered in close proximity to other computing resources but may also extend to remote locations for backup and archival storage using wide area WAN network carrier technologies.

NAS is hard disk storage that is set up with its own network address rather than being attached to the local computer that is serving applications to a network s workstation users. By removing storage access and its management from the local server both application programming and files can be served faster because they are not competing for the same processor resources. The NAS is attached to a local area network typically an Ethernet network and assigned an IP address. File requests are mapped by the main server to the NAS file server.

All of the above share one common feature that can be an Achilles tendon in more ways than one i.e. data is stored on a physical medium such as a disk drive CD drive and so forth.

The present invention provides methods and apparatus including computer program products for rotating encryption in data forwarding storage.

In general in one aspect the invention features a method including in a network of interconnected computer system nodes receiving a request from a source system to store data directing the data to a computer memory the computer memory employing an encryption scheme and continuously forwarding the data from one computer memory to another computer memory in the network of interconnected computer system nodes without storing on any physical storage device in the network each computer memory employing the encryption scheme. The continuously forwarding includes determining an address of a node available to receive the data based on one or more factors sending a message to the source system with the address of a specific node for the requester to forward the data detecting a presence of the data in memory of the specific node and forwarding the data to another computer memory of a node in the network of interconnected computer system nodes without storing the data on any physical storage device.

In another aspect the invention features a network including a group of interconnected computer system nodes each receiving data and continuously forwarding the data from computer memory to computer memory without storing on any physical storage device in response to a request to store data from a requesting system and retrieve data being continuously forwarded from computer memory to computer memory in response to a request to retrieve data from the requesting system each computer memory employing an encryption scheme each node further configured to detect the presence of data in its memory and forward the data to computer memory of another node in the interconnected computer systems nodes according to a node s availability.

The details of one or more implementations of the invention are set forth in the accompanying drawings and the description below. Further features aspects and advantages of the invention will become apparent from the description the drawings and the claims.

Unlike peer to peer networks which use data forwarding in a transient fashion so that data is eventually stored on a physical medium such as a disk drive the present invention is a continuous data forwarding system i.e. data is stored by continually forwarding it from one node memory to another node memory.

As shown in an exemplary network includes a user system and a number of network systems . Each of the network systems can be considered to be a node in the network and one such network system may be designated as a central server such as network system which may assume a control position in network . Each of the nodes may be established as a privately controlled network of peers under direct control of the central server . Peered nodes may also be a mix of private and public nodes and thus not under the direct physical control of the central server . The network may also be wholly public where the central server or servers has no direct ownership or direct physical control of any of the peered nodes.

As shown in the user system can include a processor memory and input output I O device . Memory can include an operating system OS such as Linux Apple OS or Windows one or more application processes and a storage process explained in detail below. Application processes can include user productivity software such as OpenOffice or Microsoft Office. The I O device can include a graphical user interface GUI for display to a user .

As shown in each of the network systems such as network system can include a processor and memory . Memory can include an OS such as Linux Apple OS or Windows and a data forwarding process explained in detail below.

In traditional systems application processes need to store and retrieve data. In these traditional systems data is stored on local or remote physical devices. And in some systems this data can be segmented into different pieces or packets and stored locally or remotely on physical mediums of storage. Use of fixed physical data storage devices add cost maintenance management and generate a fixed physical record of the data whether or not that is the desire of the user .

The present invention does not use fixed physical data storage to store data. When a request to store data is received by the central server from storage process data is directed to a node in the network where it is then continuously forwarded from node memory to node memory in the network by the data forwarding process in each of the network nodes without storing on any physical storage medium such as a disk drive. The forwarded data resides only for a very brief period of time in the memory of any one node in the network . Data is not stored on any physical storage medium in any network node.

In a like manner when a request to retrieve data is received by the central server from storage process the requested data which is being forwarded from node memory to node memory in the network is retrieved.

Data forwarded in this manner can be segmented and segments forwarded as described above. Still the segmented data is not stored on any physical storage medium in any network node but merely forwarded from the memory of one node to the memory of another node.

As shown in storage process includes sending a request to a central server to store or retrieve data. If the request is a retrieve data request storage process receives the requested data from the central server or node in the network.

If the request to the central server is a store data request storage process receives an address of a node from the central server and forwards the data to the node memory represented by the received address.

As shown in data forwarding process includes receiving a request to store or retrieve data. If the received request is a request to store data data forwarding process determines an address of a node available to receive the data in memory. This determination can include pinging the network and determining which of the nodes in a network is available or determining which node in the network has the least traffic or determining which node in the network has the largest available memory or any combination of these or other factors.

Process sends a message to the user system with the address of a specific node for the requester to forward the data.

Process detects the presence of data in node memory. Process forwards the data in memory to another node in the network of nodes and continues to repeat detecting and forwarding of the data from node memory to node memory. When data arrives in any node memory process affixes a time stamp to the data.

Forwarding can include pinging the node in the network to determine which of the nodes in the network is available or determining which node in the network has the least traffic or determining which node in the network has the largest available memory or any combination of these or other factors.

In one specific example at the point of entry to a node data undergoes an encrypted handshake with the node or central server or user. The encryption scheme employed is under the control of the central server which can change or rotate the scheme periodically or in response to external factors. Any two or more encryption schemes can be used. For example encryption schemes involving simple conversions can include ASCII to Binary Binary to ASCII ASCII to Hex Hex to ASCII Binary to Hex Hex to Binary Dec to Hex Hex to Dec Dec to Roman and Roman to Dec and so forth.

Encryption schemes involving network tools can include IP to Dec Dec to IP IP to Hex Hex to IP IP Net Calculator IPv6 Validator IPv6 Compress IPv6 Uncompress and so forth.

Non Key En DeCryption schemes can include PasswordGen Backwards Base 64 Encode Base 64 Decode Caesar Bruteforce 133t 5p34k 3nc0d3 133t 5p34k d3c0d3 Igpay Atinlay Un Pig Latin ROT 13 and so forth.

HTML Encoding schemes can include HTML Entities Encode HTML Entities Decode URL Encode URL Decode and so forth.

Hash Algorithm schemes can include DES MD4 MD5 SHA1 SHA 224 SHA 256 SHA 384 SHA 512 HAVAL 128 HAVAL 160 HAVAL 192 HAVAL 224 HAVAL 256 RIPEMD 128 RIPEMD 160 RIPEMD 256 RIPEMD 320 Tiger Tiger 128 Tiger 160 Adler 32 Whirlpool GOST CRC32 CRC32B and so forth.

Key En DeCryption schemes can include Tripple DES Blowfish CAST 128 CAST 256 GOST Rijndael 128 Rijndael 192 Rijndael 256 SERPENT Safer RC2 XTEA LOKI97 DES TwoFish Wake ECB mode BASE64 armored and so forth.

Time Conversion schemes can include Unix Timestamp to Date Time Date Time to Unix Timestamp Unix Timestamp to RFC 2822 Unix Timestamp to Internet Time Unix Timestamp to ISO 8601 and so forth.

The central server can direct a different encryption scheme to each of the network systems or a single encryption scheme to all of the network systems .

The central server can periodically direct one or more of the network systems to change their current encryption scheme to another encryption scheme. The central server can direct the network systems to employ a particular encryption scheme based on the type of data being forwarded from node memory to node memory. The central server can direct the network systems to employ a particular encryption scheme based on an owner of the data being forwarded from node memory to node memory.

The central server can store the various encryption schemes locally and send a particular encryption scheme to a node memory for use or the network systems can store the various encryption schemes locally and wait for instructions received from the central server to select a particular encryption scheme for use.

If the received request is a request to retrieve data being continuously forwarded from node memory to node memory data forwarding process matches at the central server using a hash mark or other unique code that can be sniffed by the node upon the data entering the node via the encryption handshake. This can occur by pinging the nodes in the network. Process sends the message to return the data to the user directly to the node or node state where the central server believes the data will likely appear. The more the central server can narrow the node state that it pings to then the more efficient the retrieval will become and the less burdened by unnecessary messaging traffic to nodes that are not necessary for a transaction between the central server and the node capable of forwarding the data.

Once the correct node receives the message to forward the data in node memory to the requester process forwards in node memory the data to the requester and forwards a confirmation message that the data has been sent to the user. This routing message may be sent directly to the central server or may be passed to the central server or servers via other node s or supernode s in the network . Upon the user receiving the requested data the user s application functions to automatically ping the central server that the data requested has been received. Thus the network creates data storage without caching downloading and or storing the data on any physical storage medium. Data storage and management is accomplished via a continuous routing of the data from node memory to node memory the forwarded data only downloaded when the user requests the data to be returned to the user from the network .

New nodes and node states may be added and or deleted from the network based upon performance. Users may have access to all nodes or may be segmented to certain nodes or node states by the central server s or via the specific architecture of the private public or private public network.

Individual nodes nodes states and supernodes may also be extranet peers wireless network peers satellite peered nodes Wi Fi peered nodes broadband networks and so forth in public or private networks. Peered nodes or users may be used as routing participants in the network from any valid peer point with the same security systems employed as well as custom solutions suitable for the rigors of specific deployments such as wireless encryption schemes for wireless peers and so forth.

In process rather than have data cached or held in remote servers hard drives or other fixed storage medium the data are passed routed forwarded from node memory to node memory. The data are never downloaded until the authorized user calls for the data. A user on the system may authorize more than one user to have access to the data.

A primary goal in process is to generate a data storage and management system where the data is never fixed in physical storage but in fact is continually being routed forwarded from node memory to node memory in the network. The path of the nodes to which data is forwarded may also be altered by the central server to adjust for system capacities and to eliminate redundant paths of data that may weaken the security of the network due to the increased probability of data path without this feature.

The invention can be implemented to realize one or more of the following advantages. A network creates data storage without caching or downloads. Data storage and management are accomplished via a constant routing of the data.

Embodiments of the invention can be implemented in digital electronic circuitry or in computer hardware firmware software or in combinations of them. Embodiments of the invention can be implemented as a computer program product i.e. a computer program tangibly embodied in an information carrier e.g. in a machine readable storage device for execution by or to control the operation of data processing apparatus e.g. a programmable processor a computer or multiple computers. A computer program can be written in any form of programming language including compiled or interpreted languages and it can be deployed in any form including as a stand alone program or as a module component subroutine or other unit suitable for use in a computing environment. A computer program can be deployed to be executed on one computer or on multiple computers at one site or distributed across multiple sites and interconnected by a communication network.

Method steps of embodiments of the invention can be performed by one or more programmable processors executing a computer program to perform functions of the invention by operating on input data and generating output. Method steps can also be performed by and apparatus of the invention can be implemented as special purpose logic circuitry e.g. an FPGA field programmable gate array or an ASIC application specific integrated circuit .

Processors suitable for the execution of a computer program include by way of example both general and special purpose microprocessors and any one or more processors of any kind of digital computer. Generally a processor will receive instructions and data from a read only memory or a random access memory or both. The essential elements of a computer are a processor for executing instructions and one or more memory devices for storing instructions and data. Generally a computer will also include or be operatively coupled to receive data from or transfer data to or both one or more mass storage devices for storing data e.g. magnetic magneto optical disks or optical disks. Information carriers suitable for embodying computer program instructions and data include all forms of non volatile memory including by way of example semiconductor memory devices e.g. EPROM EEPROM and flash memory devices magnetic disks e.g. internal hard disks or removable disks magneto optical disks and CD ROM and DVD ROM disks. The processor and the memory can be supplemented by or incorporated in special purpose logic circuitry.

It is to be understood that the foregoing description is intended to illustrate and not to limit the scope of the invention which is defined by the scope of the appended claims. Other embodiments are within the scope of the following claims.

