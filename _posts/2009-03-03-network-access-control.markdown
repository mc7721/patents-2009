---

title: Network access control
abstract: The invention provides for telecommunications user equipment including network access control means operative responsive to control parameters and further including a subscriber module accessible remote from the user equipment and arranged to store the said control parameters for use by the said access control means, and wherein the subscriber module can comprise a mobile equipment offering gateway functionality such as between a public access network and a local IP link.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08923308&OS=08923308&RS=08923308
owner: Lenovo Innovations Limited (Hong Kong)
number: 08923308
owner_city: Quarry Bay
owner_country: HK
publication_date: 20090303
---
Within a network environment IP based applications are increasingly running on User Equipment UE such as mobile devices Home Gateway solutions as defined in ETSI Technical Specification 185 003 TISPAN CNG Architecture and Interfaces etc. particularly with the emergence of Voice over IP VoIP and related internet telephony services. Some such applications could also perform sensitive IP based access protocols such as SSH Secure SHell FTP File Transfer Protocol and SIP Session Initiation Protocol sessions on a public access network and could receive a variety of different formats of IP Internet Protocol traffic.

Also with improving device performance it is foreseen that a mobile terminal could be interconnected through a private local IP link to embedded internal devices and or to external terminal equipment such as by way of a WiFi private network. In the field of the Home Gateway HG technology the HG can also be connected through a private local IP link.

In all such situations the local IP sub network is effectively hidden behind the UE acting as a border gateway and router to provide connectivity to the IP based services that can be offered by wireless operators. However the UE is often seen as a single device on the public access network and in some configurations IPv4 IPv6 stateful autoconfiguration mode only a single routable IP address will be allocated. To take account of such configurations a Network Address Translation NAT defined in RFC 3022 Traditional IP Network Address Translator based solution is required for management of the addressing of the local sub network elements in order to map internal private addresses i.e. the local link addresses to the single routable IP address allocated by the public access network. Filtering functions required for address translation can also be extended to cover firewall type capabilities which can assist in the control of IP traffic the local IP network security and also protect access to the public network.

Additionally Session Initiation Protocol SIP as defined in RFC3261 IP Multimedia Subsystem IMS as defined by the 3rd Generation Partnership Project in Technical Specification 23.228 that specifies the IMS stage 2 applications including network information such as the IP address and port number at application layer in addition to network layer can also employ Application Level Gateway ALG as defined in RFC2663 translations at the border gateway element of the telecommunication mobile device arranged with the local IP network.

Besides by passing of NAT during SIP communication for example by way of the Simple Traversal of UDP User Datagram Protocol through NAT STUN protocol as defined in RFC3489 is possible since specific protocols transport IP level information at the application level and which are contrary to the network layer philosophy. It is also well known that firewall whether SIM based or not and NAT solutions exist to enable the control and management of IP flows. Further NAT is often accompanied by an Application Level Gateway ALG to monitor the payload of the packet and perform the alteration when IP level information is transported at application layer for example with the SIP protocol.

It is further foreseen that mobile devices will enable users to download a wide variety of IP based applications requiring connection with different network services through a home operator network. While the application download may be restricted at the time of application installation there is farther desire for security in limiting undesired access at the network level and thereby preventing a potentially malicious application from achieving network connection. For example subsequent to installation of an IP based application the network operator may later notice malicious actions from that application such as the sending of undesired network application requests are sent and so firewall application software is then required.

Also a network operator can enter into agreements with service providers for services such as Instant Messaging applications or VoIP applications. However since future mobile platforms are likely to be open to many IP based applications the user may be able to download any application of choice thereby rendering the agreement between the network operator and the service provider s potentially ineffective. Besides such agreement may further be limited by the time at which a user can access the IP based service.

The present invention seeks to provide for a system and arrangement for controlling and configuring network access and which exhibit advantages over known such systems and arrangements.

According to one aspect of the present invention there is provided telecommunications user equipment including network access control means operative responsive to control parameters and further including a subscriber module accessible remote from the user equipment and arranged to store the said control parameters for use by the said access control means.

According to another aspect of the present invention there is provided a telecommunications system comprising a network element and a telecommunications user equipment as defined above and further including a local IP link and at least one device connected via the local IP link and which may be an embedded device for instance a Central Control Processing Unit an Application Control Processing Unit a Subscriber Identity Module a SD Card or external terminal equipment for instance a PC a laptop a Personal Digital Assistant a handset .

Yet further the present invention provides for a method of network access control by way of control parameters in a user equipment of a telecommunications system comprising the steps of storing the control parameters in a subscriber module of the user equipment and allowing access by network access control means of the user equipment to the subscriber module for use of the said control parameters.

According to yet another aspect of the invention there is provided a method of controlling network access by way of control parameters in a user equipment of a telecommunications system including the steps of remotely accessing a subscriber module of the user equipment for the provision of the said control parameters therefrom.

The invention is described further hereinafter by way of example only with reference to the accompanying drawings in which 

Turning first to there is provided a schematic illustration of a communication system in which a mobile radio communications device such as a cell phone handset achieves connectivity with both a local terminal device and a public network .

As will be appreciated from the present invention the handset can function as a network gateway device allowing for IP communication by way of a local link with the terminal device and can also allow for the transfer of ALG parameters and filtering rules with optional exchange updates capabilities.

IP communication is also provided between the handset and the public network and an update of NAT parameters and filtering rule updates at the handset can be initiated from the network .

Importantly the handset includes a subscription module such as a SIM or USIM which provides for NAT and IP filtering within the handset on the basis of the filtering rules and NAT parameters found therein and as described further below.

There are currently no mechanisms to enable an operator to manage IP traffic and NAT in UE including a subscription module at pre provisioning and which would ensure that the appropriate applications will be granted network level access. Besides such NW Access can further be limited in time and dependent upon the localisation.

As will be appreciated the present invention serves to enable the operator to limit the access of the network services to IP based applications on the basis of information stored in a subscription module such as a SIM or USIM.

The invention is embodied in a device system and method serving to enable NAT IP filtering and QoS settings in a UE such that an operator can restrict access to specific applications control addition of further application dynamically loaded on the UE and provide for pre provisioning of security rules enabling the device to safely connect to the IP based network. As such the invention enables the operator to grant network access to specific services for which it may have concluded appropriate agreements with service providers.

The UE can be in the form of a mobile phone personal digital assistant with mobile telecommunication capabilities or Home Gateway etc. which with a subscription module can comprise a Border Gateway element having an access control functionality by means of at least one of NAT Firewall or Quality of Service elements.

In the form of a border gateway the device can be interconnected via a local IP link to other internal devices or external terminal equipment devices requiring IP connectivity to a wireless public access network.

The Border Gateway can then act as a router for a local IP link applying as required NAT parameters and filtering rules.

The UE can have a well defined API to access the NAT parameters and or filtering rules from the subscriber module element and the NAT and filtering rules can be read undated or removed as required.

In particular the NAT parameters can be modified dynamically during an IP based session such as for example a SIP session or a media session.

The storing of the control parameters such as the NAT Filter QoS rules and preferences in the subscription module to enable operator and user control on the incoming or outgoing IP traffic advantageously serve to enable pre provisioning and improved operator control on the IP traffic at the UE.

Turning now to there is provided a schematic illustration of a network gateway device such as the cell phone handset of .

Respective connectivity between the local terminal device and public network is again illustrated alone with the further functional characteristics of the handset .

That is the handset includes a border gateway element with NAT and or firewall functionality and which is arranged to communicate with read update remove operators NAT and filtering rules preferences with a subscriber module of the handset which as noted can comprise a SIM or USIM.

Within the subscriber module there is stored the operators NAT NAPT ALG and filtering rules preferences.

As will be appreciated from the following the appropriate locations within the subscriber module are arranged to be accessed and updated by way of the communication link from the public network such that a network operator can update and otherwise enable or disable the appropriate NAT and firewall functionalities so as to allow for dynamic adaptation of the gateway functionality of the handset .

It will be appreciated that the invention is well suited to configure incoming outgoing IP traffic to a local IP Link such as the IP based application residing on the same device in which is located the firewall NAT solution or the IP based application residing on another device connected through the IP local link. Undesired applications are consequently prevented from accessing network services either such as local IP Network Services or public network services if they do not meet the operator policy.

As illustrated an example of the overall system comprises a network element a UE with IP technology capability a local IP link and one or more embedded internal devices and or external terminal equipments connected through the local IP link and requiring IP connectivity to public access network. The network element can of course that transfers IP traffic over any transport technology and underlying Access Technology such as 2G 3G WiFi WiMAX XDLS.

As required for the border gateway a UE single routable IP address will be available and as provided by wireless public access network such as an IPv4 or an IPv6 public address to be used by NAT functions to perform address translation. Also provided is a border gateway link local IP address for communication on IP private local link acquired for example at startup via IPv4 or IPv6 configuration procedures. Further each internal device external terminal equipment a link local IP address is provided for communication on private local link acquired for example at startup via IPv4 or IPv6 configuration procedures will be used by NAT functions to perform address translation.

For any IP based application or service the UE or external terminal equipment will use its link local address in all IP packets. In a scenario in which the ALG function is implemented with the NAT function the link local IP address and port will also be used to build all application level messages. The user or device that controls the UE may also enable disable the gateway capabilities using a field value in the subscription module. As such the gateway can disable any IP traffic from any of the devices configured in the local IP network

At the UE the NAT function can serve to control replacing the link local IP addresses and ports of the messages with the UE public IP address and ports for all outgoing IP flows. NAT tables can have been previously populated with the appropriate information such as IP flow direction source and destination IP addresses and ports in order to filter and translate the IP traffic. For incoming flows the IP address would be replaced by the appropriate link local IP address where resides a network service accessible from the outside network.

In one arrangement of the invention the filtering and translation information that can be stored can include optionally the IP flow direction i.e. whether outgoing or incoming flow the original calling callee IP addresses and or ports for filtering purposes for translation purposes the new calling callee IP addresses and or ports can be included and which comprise a combination of both port and IP address for translation purpose can be used in case of NAPT Network Address Port Translation also known as Port Address Translation or Reverse Address and Port Translation .

In general at least a subset of the filtering and or translation rules must be provided. The NAT is used to perform translation of address and or port whereas the filtering is used to reject accept a particular type of traffic. Of course QoS rules Quality of Service are used to apply a specific QoS Policy on a particular type of traffic or on a given Interface.

Any NAT parameters pre configured in the subscription module will advantageously be used to populate the NAT table for static NAT purposes such as for Network address port Translation for connection initiated outside the local network. Such an example could comprise a server application having local IP non routable address accessible by a network operator client for device management purposes. Another example would arise when a client application of a remote HG network desires to access a server application of the local HG network such that point to point sessions can be allowed between the HG routers.

The filtering and translation rules applied by a NAT Solution for Source NAT Alteration of the source address at POSTROUTING or OUT would be

In this case the packets issued from the local IP address on the local port and destined to the callee IP address on the callee port will be modified into packets issued from the public IP on public port and destined to callee IP and callee port. The source information is translated thereby enabling the callee to reply by sending the packets to the public IP address.

Wherein the filtering and translation rules applied by a NAT Solution or the Destination NAT Alteration of the destination address at PREROUTING would be

In this case the destination information is translated by the local information of the IP local IP link.

It should be noted that the local IP address may also relate to a pool of addresses by indicating the mask value e.g. 16 or 8 if the network devices are to be configured with an address from a predefined set of IP addresses for example as from a sub network.

While the port may be specified if it is statically attributed since the port or service used can change dynamically the value can be null in the Access Control Parameters and the port is then dynamically set by the Firewall NAT solution.

Insofar as the Public IP address may not be known the information available in the Access Control Parameters can therefore include the type of Radio Access Technology RAT which is usually attached to a network interface. Consequently by indicating this information the alteration of the IP address just needs to replace the address of the packets by the one affected on the Interface for source NAT.

Advantageously a domain name will be provided in place of an IP Public Address thereby requiring the UE to further resolve it into an IP address using Domain Name Resolution DNS means while the DNS Server address can be retrieved using Dynamic Host Configuration Protocol means.

The destination NAT can be used when external devices want to access a network service attached to the link local IP address. For a specific service for example an operator application server for configuration purpose the application must be arranged to provide security access mechanisms to ensure that only the legitimate persons can access the server. This can be controlled by way of the NAT Information for the translation to he made and the service to he accessible

For traffic and device access control other Access Control parameters can be added such as the number of IPsec Internet Protocol Security whose reference architecture is defined in RFC 2401 sessions allowed whether or not the Gateway is enabled for all types of connection supported by the device such as 2G 3G WLAN Wireless Local Area Network XDSL Digital Subscriber LAN etc. whether or not NAPT is enabled and whether or not an application and if so which application is allowed to modify parameters

The NAT Filter QoS Information stored in the USIM can be included in the Configuration Information used a Customer Network Gateway CNG . In this example of the invention an Interface is required between the CNG NAPT and Firewall function of the CNG and subscription module for retrieving the information of present invention.

When a UE starts up NAT rules IP filtering rules and QoS rules can be read from SIM USIM so as to configure the Access Control element. Also the information about data and Time duration location and whether the gateway shall be turned on or off is retrieved if present. When the telecommunication mobile device establishes an IP bearer with the network as well as a PDP Packet Data Protocol context for 3GPP Access Network then IP communication can be received by the telecommunication mobile device if the PDP Context refers to an IP context.

During any currently established IP communication the filtering rules and NAT will apply. On this basis some of the traffic whether it is incoming or outgoing traffic is not blocked and filtered at the border gateway element. For example in the example of an embedded web server listening on a given port number with a specific IP address incoming traffic can be filtered so as to give access to incoming connection with the server only. In addition for SIP based communication NAT coupled with for example the STUN protocol can be used to enable network address translation during data transmission sessions.

Files are added in to the USIM. The AFDshall be selected using the AID Application Identifier and information in EFDIR as defined in 3GPP TS 31.102. The services can be added at first bit of byte within EFstructure so that the telecommunication mobile device can select those services for the purpose of NAT and or Filtering rules execution and or QoS settings and as shown in the following table of available services for NAT parameters and filtering rules.

Service 81 relates to NAT FILTER QOS NWCTRL Service. While the remainder are designated Reserved for Future Use RFU . Coding of this Service is shown in the following table although it should be appreciated that the value service n 81 is merely illustrative and could be any appropriate value.

The Elementary Files EF EF and EFcontain the coding for NAT Parameters IP Filtering parameters and QoS parameters respectively.

Turning now to there is provided a schematic system overview of an exemplary embodiment of the present invention employing the border gateway element and subscriber modules of .

Within the border gateway element there is provided NAT firewall functionality which includes a pre routing table and post routing a forward table an IN table local processor and an OUT table .

Subsequent to post routing by the POSTROUTING processing unit or POSTROUTING node packets are delivered as illustrated to the Network Interface Device NWIF while incoming packets are forwarded to the pre routing processing unit .

As discussed further below over the air updates will also be delivered from the NWIF directed to the subscriber module for updating of the NAT filtering and OoS rules .

Between the border gateway element and the subscriber module there is provided a NW IP module manager which is arranged to retrieve check and apply rules as appropriate from the subscriber module through the reading thereof and subsequent application to the NAT firewall functionality . Also delivered from the subscription module to the NWIP policy manager is a trigger for effectively triggering operation of the NWIP policy manager upon for example receipt of an OTA update.

This causes the NW IP Policy Manager to read again the NAT FILTER QOS values in order to reset the IP Policy for the user plane in the UE. An example of such use is when the Operator Network detects the localisation of the UE if for example the UE is a mobile agent and requires a change in the IP Policy for example when the UE moves from its home network to its corporate network. Another usage example is when the operator updates the user s subscription such as when a service is no longer time restricted or no longer accessible due to subscription limitation and the Network Access Control parameters are modified accordingly.

In further detail rules are applied in the Tables of the NAT Firewall for NAT Filter or QoS purposes and the tables and are used indifferent phases of the packet routing process through the device. The pre routing node manages incoming packets from the outside before they are routed. This is usually used to change information such as the destination information DNAT of a connection.

The postrouting node manages outgoing packets after the routing decision by the device and this is usually used to change information such as the source information of a connection.

The forward node serves to filter packets that the local device has to transmit and the IN node filters packets destined to the local device while the OUT node filters packets transmitted by the local process of the device .

It should be noted that time and location restrictions are not illustrated in the structure of this table which is provided by of example only. However it will be appreciated that such information could be added to the structure of a rule by using for instance a Date and a Location field.

The NW Flow Restriction Type can be a NAT EF element. Filter EF element or QoS EF element. Each EF contains information in TLV Format and this information is a succession of rules. Such rules are decoded by the device to perform the correct configuration of the Firewall NAT solution using specific API.

As will be appreciated QoS behaves in a rather different manner from NAT and FILTER. APPLY QOS consists in setting one or more specific value s in the flow characteristics e.g. set a max TTL value set a bandwidth value for a given techno etc. . . . .

It should be noted that all operation are not possible for all kind of Network Access control i.e. NAT FILTER or QOS .

Therefore according to the association scheme illustrated in the a NAT rule can be NAT A B C meaning that NAT applies to PREROUTING node for a TCP or UDP protocol and which is to be applied in said PREROUTING node.

Turning now to there is provided an example of use of the proposed solution. In the example the Firewall NAT solution is NETFilter.

A NAT rule is retrieved from the USIM. The rule is in the form of NAT A B B C and it is interpreted from the information stored in the EFelement of the SIM USIM 

This rule is transformed in the appropriate command to be used by IPTable of Netfilter. It is interpreted as Replace the IP address of all TCP packets going out via 2G Interface and whose destination port is 3555 by the IP address configured on the 2G out Interface .

With regard to there is provided an example of coding for NAT EF elements arranged to be employed within an embodiment of the invention.

Further indication about time date location and related profile indication could be added as required.

As illustrated in the structure is considered transparent and there is no SDU Format Information SFI . The element is made optional and the update requires ADMIN privileges ADM . As such the operator may only be the only one to change this value e.g. via OTA update .

TARGET identifies the Node to which the NAT rule is applied. The node indicates at which step of the packet routing by the UE should be done the translation.

PROTO used to further indicate protocol related information. Such protocol can be a Transport layer protocol or Network layer protocol for which specific information should be used as matching criteria if indicated in the structure.

IP use to indicate that the NAT rule applies to IP flows. In such a case at least the source port or the destination port SHALL be indicated.

Finally illustrates the NAT Rule Content structure in TLV Format of and which mainly shows to which payload is related the length for each tag.

Other mechanisms for the external device to update NAT tables and retrieve the public IP address are also possible and which can provide support for UPnP IGD Universal Plug Play Internet Gateway Device .

ALG function is arranged to map IP addresses and ports in all applications level messages supported and the ALG may require NAT configuration information to perform its own filtering translations.

The ALG function can be either collocated with the NAT functions or implemented separately by internal devices and or external terminal equipments. In this case the NAT access control element must be able to exchange configuration information for ALG processing. NAT tables configuration by ALG may also be possible.

As will be appreciated the described method includes the storage of the preferences on the SIM USIM attached to a UE reading removing and updating of said preferences to be used by the UE during IP communication for IP based services. The NAT ALG NAPT pre provisioned configurations parameters and preferences are advantageously set up at a switch on of the UE to secure and filter the IP traffic.

The invention is well suited to configure incoming outgoing IP traffic to local IP Link such as an IP based application residing on the same device in which is located the firewall NAT solution or the IP based application residing on another device connected through the IP local link. Undesired applications are consequently prevented from accessing network services either local IP Network Services or Public network services if they do not meet the operator policy and the contract that the user has subscribed to.

The invention can therefore enable restriction for network access to IP based applications which can further be based on date and time duration associated with the control parameters and the settings can vary depending on the location of the UE. Moreover easier application of said control parameters will be performed thanks to profile settings associated with the control parameters thereby leading to personalized network access settings.

According to one aspect of the present invention there is provided telecommunications user equipment including network access control means operative responsive to control parameters and further including a subscriber module accessible remote from the user equipment and arranged to store the said control parameters for use by the said access control means.

The invention can prove advantageous in facilitating operator and user control of network access. In particular updates that can only be performed by the operator can be provided in a restricted area in the subscription module. Also IP policy rules can be applied when the user equipment is turned on and this can include other IP based session information such as the number of IP sessions allowed.

The network operator can therefore perform IP traffic analysis and dynamically set filtering rules to block undesired traffic which would not respect a service agreement. When a UE allows IP based application installation the service management becomes complex and the operator cannot guarantee high level of control which may cause a breech of the agreements the operator has entered into with the service provider s . Therefore it should be possible for the operator to define a local IP based policy applied on each individual UE and which may depend on the location of the UE e.g. at a corporate network or at home or in outdoor network the subscription and IP security level to be applied.

The telecommunications user equipment can comprise a network gateway device providing access to the external public network to internal devices located in the local IP sub network and the invention advantageously exhibits the possibility for the user to turn on off the gateway functionality.

Further the telecommunications user equipment can comprise a router between a public network and IP local link and the subscriber module can of course comprise a SIM Subscriber Identity Module or USIM Universal Subscriber Identity Module as defined by the 3rd Generation Partnership Project in the Technical Specification 31.102 card.

In one aspect of the invention the telecommunications user equipment comprises a mobile radio communications device.

Preferably the control parameters comprise at least one of NAT filtering and or quality of service preferences.

Preferences are further dependant upon the location of the UE for instance in outdoor home or corporate network the settings may vary . As such the control parameters may comprise an indication of which situation they apply to.

Further said control parameters are associated to time restriction and as such the control parameters may only be applied at a given date for a defined period of time thereby limiting the access to the specific applications depending on the contract the user has subscribed to.

The telecommunications user equipment can advantageously include an Application Programming Interface API for retrieval of the parameters from the subscriber module by the control means.

The telecommunications user equipment can include a Network IP NWIP policy manager for retrieval and application of the said control parameters.

According to another aspect of the present invention there is provided a telecommunications system comprising a network element and a telecommunications user equipment as defined above and further including a local IP link and at least one device connected via the local IP link and which may be an embedded device for instance a Central Control Processing Unit an Application Control Processing Unit a Subscriber Identity Module a SD Card or external terminal equipment for instance a PC a laptop a Personal Digital Assistant a handset .

Yet further the present invention provides for a method of network access control by way of control parameters in a user equipment of a telecommunications system comprising the steps of storing the control parameters in a subscriber module of the user equipment and allowing access by network access control means of the user equipment to the subscriber module for use of the said control parameters.

The said parameters can be further associated with time and location restrictions. Also the said parameters can be further associated with one or more configuration profile for the network access control means to easily apply those control parameters. For examples such a profile may refer to a child profile corresponding to a set of control parameters enabling access limitation only to child specific applications.

Besides the control parameters when referring to NAT rules application can be further adaptive to the Radio Access network Technology RAT Interface. That is a RAT interface can be deduced according to the information indicated in the said control parameters. As such different settings can be applied for different types of RAT such as a GPRS Evolved Radio Access Network GERAN RAT a Universal Terrestrial Radio Access Network UTRAN RAT Evolved UTRAN EUTRAN RAT or a WiFi RAT or a WiMAX RAT.

The parameters can be factory configured and further be updated or they can be dynamically provisioned by way of remote access means.

The method can employ remote access of the subscriber module for provisioning of the control parameters.

According to yet another aspect of the invention there is provided a method of controlling network access by way of control parameters in a user equipment of a telecommunications system including the steps of remotely accessing a subscriber module of the user equipment for the provision of the said control parameters therefrom.

Again such remote access can allow for pre processing of the control parameters and the said remote access can allow for updating of the control parameters within the subscribed module and which can comprise an over the air update procedure.

In one particular exemplary embodiment said remote access can allow for updating of the control parameters within the subscriber module on the basis of an IP based embedded server in the UE either in the mobile communication radio device or in the subscriber module and said embedded server allowing for provisioning of said control parameters and said embedded server receiving incoming requests if they are issued by the legitimate remote access e.g. this can be achieved by pre provisioning the remote access identifier by way of an IP address or domain name .

In another particular exemplary embodiment said remote access can allow for updating of the control parameters based on UE location thereby leading the subscriber module to trigger the access network control means for application of the new access network control settings by way of NAT rules filtering rules or QoS settings to specific IP traffic.

As with the device and system defined above the control parameters within the method can comprise one or more of NAT filtering and or quality of service preferences.

The proposed solution enables the operator to limit the access of the network services to IP based applications and on the basis of information stored in the subscriber module. Such information can be applied in a Firewall NAT software or hardware solution for example as an IP security policy that can be retrieved from the subscriber module.

Such stored information can be in a generic format stored in the subscriber module and to be used irrespective of the type of NAT Filtering Solution employed in the UE and such as Netfilter IPchain. IPFilter and IPFirewall fire walling tools.

Such stored information can alternatively be formatted in a script file stored in the subscriber module and to be used irrespective of the type of NAT Filtering Solution employed in the UE thereby requiring said Solution to execute or interpret said script for the application of said control parameters.

The present invention can therefore advantageously provide a method and system for assisting network operators in the definition of their IP Policy by way of for example IP filtering rules NAT pre configuration authorized port and gateway on off control.

As noted in one arrangement the invention is based on the concept of a UE comprising NAT filtering capabilities and a subscriber module such as for example a SIM or USIM for the storage of NAT information and filtering rules.

By means of the present invention an operator can control IP based services running on a telecommunication device for which a NAT is required and firewall rules need to be applied for security and IP traffic control purpose. As such the invention can provide means for an operator mobile device to control outgoing and incoming IP traffic at the end device having a public IP address and such as a mobile device or a Home Corporate Gateway with a SIM USIM. Data is stored and may be pre provisioned in the SIM or USIM and can be updated by the operator such as by way of Over The Air OTA functionality or otherwise.

It should be appreciated that the invention can be employed with any kind of internal device or external terminal equipment implementing IP based applications and connected via an IP local link located behind a device for example a Mobile Equipment or a Corporate Customer Gateway acting as a router and performing NAT to convert link local addresses into routable addresses assigned by network and in which is applied firewall rules.

While the invention has been particularly shown and described with reference to exemplary embodiments thereof the invention is not limited to these embodiments. It will be understood by those of ordinary skilled in the art that various changes in form and details may be made therein without departing from the sprit and scope of the present invention as defined by the claims.

This application is based upon and claims the benefit of priority from United Kingdom patent application No. 0804470.2 filed on Mar. 11 2008 the disclosure of which is incorporated herein in its entirety by reference.

