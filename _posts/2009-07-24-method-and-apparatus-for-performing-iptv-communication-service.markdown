---

title: Method and apparatus for performing IPTV communication service
abstract: Provided are a method and apparatus for performing an internet protocol television (IPTV) communication service. The method includes: acquiring an application message providing the IPTV communication service from an external input with respect to a general-purpose web application by using plug-in application programming interfaces (APIs) of a web browser which are independent of an IPTV communication service provider; sending the application message to an IP multimedia subsystem (IMS) gateway (IG) functional entity apparatus; and receiving a response message comprising a result of processing the application message as a response to the sending of the application message, from the IG functional entity apparatus.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09258619&OS=09258619&RS=09258619
owner: SAMSUNG ELECTRONICS CO., LTD.
number: 09258619
owner_city: Suwon-si
owner_country: KR
publication_date: 20090724
---
This application claims the benefit of Korean Patent Application No. 10 2009 0045471 filed on May 25 2009 in the Korean Intellectual Property Office and U.S. Provisional Application No. 61 083 309 filed on Jul. 24 2008 in the United States Patent and Trademark Office the disclosures of which are incorporated herein in their entirety by reference.

Methods and apparatuses consistent with the present invention relate to performing an internet protocol television IPTV communication service by using plug in application programming interfaces APIs of a web browser the APIs being independent of an IPTV communication service provider.

An internet protocol television IPTV communication service denotes a service providing an information service a video content service and a broadcasting service to TVs through an IP network that is a high speed internet network. As a communication broadcasting convergent service is being developed interest in IPTV services is growing. Activation of the IPTV service may greatly affect not only communication and broadcasting industries but also content manufacturing and home appliance industries.

Conventionally in order for an IPTV service user to be provided with the IPTV service through an IP network the IPTV service user may own set top boxes that are different for each IPTV vendor. Only the IPTV service user who owns an IPTV set top box manufactured according to the standards set by an IPTV service provider providing an IPTV service may be provided with the IPTV service from the corresponding IPTV service provider. For example when there are three IPTV service providers A B and C a user who purchases A s set top box may only use an IPTV service provided from A. Also in order to use an IPTV service from B or C a set top box manufactured by B or C are separately purchased. Due to such a compatibility problem between the IPTV services and the set top boxes selection of the IPTV services is limited and consequently the quality of the IPTV services deteriorates or it is difficult to expand a service base.

In this regard an open IPTV forum has been recently established and the standardization is under discussion. In this forum common standards which are not dependent upon IPTV service providers are formed and the provision of IPTV services to service users based on the common standards is under discussion.

The open IPTV forum aims to form an interface and a hardware platform which are not dependent upon IPTV service providers and to use IPTV services provided from a plurality of IPTV service providers by users. According to open IPTV forum architecture even if the user does not own the set top boxes that are different for each IPTV service provider the user may use the IPTV services provided from a plurality of different IPTV service providers and thus a range of selection for the services may be expanded.

In order for the user to use the services provided from the plurality of different IPTV service providers apparatuses for relaying services provided from the plurality of different IPTV service providers are present in a residential network having functional architecture according to the open IPTV forum. The apparatuses may be entities such as Application Gateway AG IMS Gateway IG and CSP Gateway CG according to the functional architecture of the open IPTV forum. These relaying apparatuses receive IPTV services provided from a provider network outside of the residential network and relay the received IPTV services to a terminal included in the residential network.

Exemplary embodiments of the present invention provide a method and apparatus for performing an internet protocol television IPTV communication service by using plug in application programming interfaces APIs of a web browser the APIs being independent of an IPTV communication service provider and a computer readable recording medium having embodied thereon a computer program for executing the method.

According to an aspect of the present invention there is provided a method of performing an internet protocol television IPTV communication service the method including acquiring an application message providing the IPTV communication service from an external input with respect to a general purpose web application by using plug in application programming interfaces APIs of a web browser which are independent of an IPTV communication service provider sending the application message to an IP multimedia subsystem IMS gateway IG functional entity apparatus and receiving a response message comprising a result of processing the application message as a response to the sending of the application message from the IG functional entity apparatus.

The method may further include receiving an application message providing the IPTV communication service from the IG functional entity apparatus sending the application message to the web browser by using the plug in APIs for processing an event informing reception of the application message and outputting the application message through the general purpose web application.

The method may further include acquiring a session setting request message for the application providing the IPTV communication service from an external input with respect to the general purpose web application by using the plug in APIs sending the session setting request message to the IG functional entity apparatus and receiving a response message for the session setting request message from the IG entity apparatus.

The sending of the application message and the reception of the application message may be performed during the set session.

The method may further include acquiring a session completion request message for the application providing the IPTV communication service from an external input with respect to the general purpose web application by using the plug in APIs sending the session completion request message to the IG functional entity apparatus and receiving a response message for the session completion request message from the IG functional entity apparatus.

The plug in APIs for acquiring the application message providing the IPTV communication service may include messages to be sent to a remote user and a remote user identifier as input arguments.

The plug in APIs for processing an event informing reception of the application message may include a received message as a return value.

The plug in APIs for acquiring the session setting request message may include a session identifier ID as return values.

The plug in APIs for acquiring the session completion request message may include a session identifier ID as an input argument.

The plug in APIs for acquiring the application message providing the IPTV communication service on the set session may include a message to be sent to the remote user and the session ID as input arguments.

The plug in APIs for processing an event informing about reception of the application message during the set session may include a received message as a return value.

The method may further include performing at least one of the plug in APIs providing a list of users who use the IPTV communication service the length of the list of users specific user information for a specific index in the list of users a function of adding a specific user to the list of users a function of deleting a specific user from the list of users and a function of modifying a specific user in the list of users.

The method may further include performing at least one of the plug in APIs providing the number of user groups formed of the list of users who use the IPTV communication service specific user group information for a specific index in the user groups a function of adding a specific user group to the user groups and a function of deleting a specific user group from the user groups.

According to another aspect of the present invention there is provided an open IPTV Terminal Function OITF entity apparatus including a first plug in unit acquiring an application message providing the IPTV communication service from an external input with respect to a general purpose web application by using plug in application programming interfaces APIs of a web browser which are independent of an IPTV communication service provider an application message sending unit sending the application message to an IP multimedia subsystem IMS gateway IG functional entity apparatus and a response message receiving unit receiving a response message comprising a result of processing the application message as a response to the sending of the application message from the IG functional entity apparatus.

The present invention will now be described more fully with reference to the accompanying drawings in which exemplary embodiments of the invention are shown. In the drawings like reference numerals denote like elements and the thicknesses of layers and regions are exaggerated for clarity.

In the present exemplary embodiment at least one IPTV service provider provides a predetermined IPTV communication service to an IPTV user terminal that is an Open IPTV Terminal Function OITF entity apparatus .

The OITF entity apparatus is an apparatus for performing entity functions of a user domain according to open IPTV forum architecture. The OITF entity apparatus accesses the IPTV service provided by the service provider through gateways of the user domain that is an application gateway AG functional entity apparatus and an IP multimedia subsystem IMS gateway IG functional entity apparatus . An apparatus which finally uses the IPTV service such as a TV may be the OITF entity apparatus .

The IG functional entity apparatus is an apparatus for permitting access to the IPTV service linked to an IMS. The IG functional entity apparatus receives the IPTV service provided from the service provider and relays the received IPTV service to the OITF entity apparatus . The IG functional entity apparatus interacts with the OITF entity apparatus by using a predetermined protocol defined for interaction within a residential network. The IG functional entity apparatus requests the service provider to provide the IPTV service according to a request to provide the IPTV service by the OITF entity apparatus and receives the IPTV service from the service provider for relaying the received IPTV service to the OITF entity apparatus .

IPTV middleware of the OITF entity apparatus performs functions of establishing an IPTV network through the IG functional entity apparatus searching and selecting an IPTV service provider through an IPTV service provider searching entity apparatus not shown and searching and accessing IPTV communication service applications provided by the service provider selected through the IPTV service provider searching entity apparatus not shown or an IPTV service searching entity apparatus not shown .

Examples of applications for providing the IPTV communication service may include a chatting application an instant message application a voice over IP VoIP application a multimedia over IP MoIP application and a presence application. The chatting application provides a chatting service and the instant message application provides a messaging service. The VoIP application allows telephonic communication as in a general telephone network using a packet network for data communication. The MoIP application supports not only voice calls but also video communication by using a packet network for data communication. The presence application provides a service in which an online state and a location of a user are used.

A user of the OITF entity apparatus inputs uniform resource identifier URI information used to access the IPTV communication service in a web browser and thus may access the searched IPTV communication service application.

A user of the OITF entity apparatus accesses the IPTV communication service applications from the web browser and then may use the IPTV communication service through a web application . The functions of each application for providing the IPTV communication service are supported by plug in application programming interfaces APIs which are independent of the service provider .

According to the present exemplary embodiment standardized plug in APIs of a web browser which are independent of the IPTV communication service provider are provided and thus the OITF entity apparatus may use the IPTV communication service including the chatting application the instant message application the VoIP application the MoIP application and the presence application independently of the service provider . Accordingly a user of the OITF entity apparatus may use the IPTV communication service with other users who use the IPTV communication service applications provided from different service providers. In addition the service provider does not need to develop and provide non standardized IPTV communication service applications and instead may develop and provide general purpose web applications by using the standardized plug in APIs of a web browser.

A user of an OITF entity apparatus requests to set a session for applications providing the IPTV communication service through the web application in operation . The request to set a session is transmitted to the web browser by using a createSession plug in API . In the present embodiment the createSession plug in API is provided to request the setting of a session. Other plug in APIs performing the same functions having other method names other input arguments and other return values may be used.

In operation the IPTV middleware of the OITF entity apparatus generates a session setting request message by using a hypertext transfer protocol HTTP and transmits the generated message to an IG functional entity apparatus .

In operations through the session setting request message is converted into a session initiation protocol SIP and is transmitted to a peer to peer communication enabler P2P CE entity apparatus from the IG functional entity apparatus via an Authentication and Session Management ASM entity apparatus . The ASM entity apparatus and the P2P CE entity apparatus perform network domain entity functions managed by the service provider. The ASM entity apparatus performs access management and IPTV service session management so that only a specific user may access a network domain managed by the service provider. The P2P CE entity apparatus provides interfaces for the IPTV communication service applications in the network domain.

In operations through a response message for the session setting request message is transmitted from the P2P CE entity apparatus to the IG functional entity apparatus via the ASM entity apparatus by using the SIP.

In operation session setting between the IG functional entity apparatus and the P2P CE entity apparatus is completed.

In operations through the OITF entity apparatus and the IG functional entity apparatus set and manage connections for transmitting and receiving various events related to the session set in operation .

A user of the OITF entity apparatus may request to complete a session for applications providing the IPTV communication service through the web application . The request to complete a session is transmitted to the web browser by using a closeSession plug in API. In the present embodiment the closeSession plug in API is provided to request to complete a session. Other plug in APIs performing the same functions having other method names other input arguments and other return values may be used.

The IPTV middleware of the OITF entity apparatus generates a session completion request message by using the HTTP protocol and transmits the generated message to an IG functional entity apparatus .

The session completion request message is converted into a SIP and is transmitted to the P2P CE entity apparatus from the IG functional entity apparatus via the ASM entity apparatus .

A response message for the session completion request message is transmitted from the P2P CE entity apparatus to the IG functional entity apparatus via the ASM entity apparatus by using the SIP. Accordingly a session between the IG functional entity apparatus and the P2P CE entity apparatus is completed.

A user of an OITF entity apparatus acquires a message for applications providing the IPTV communication service through the web application in operation . The acquired application message is transmitted to the web browser by using a sendMessage plug in API . In the present exemplary embodiment the sendMessage plug in API is provided to acquire the application message. Other plug in APIs performing the same functions having other method names other input arguments and other return values may be used.

In operation the IPTV middleware of the OITF entity apparatus transmits the application message to an IG functional entity apparatus by using the HTTP protocol.

In operations through the application message is converted into a message session relay protocol MSRP and is transmitted to a P2P CE entity apparatus from the IG functional entity apparatus via an ASM entity apparatus in a session that is previously set. The MSRP is an Internet engineering task force IETF standard for transmitting a series of instant messages in a session. A detailed description of the MSRP will be omitted herein.

In operations through a response message including a result of processing the application message is transmitted to the IG functional entity apparatus from the P2P CE entity apparatus via the ASM entity apparatus by using the MSRP.

In operations through the OITF entity apparatus is informed of the result of processing the application message from the IG functional entity apparatus as an event and outputs the result.

A user of the OITF entity apparatus may receive an application message from a remote user who uses the IPTV communication service applications.

In operations through the application message received from the remote user is transmitted to the IG functional entity apparatus from the remote user by using the MSRP. In the present exemplary embodiment the remote user who uses the IPTV communication service applications is a user using a plain old telephone service POTS . However the present embodiment may be applied to remote users who use other services. The POTS is a basic voice call service which is widely used in residential homes.

In operations through the OITF entity apparatus receives the event informing reception of the application message from the IG functional entity apparatus .

In operation the received application message is transmitted to the web browser of the OITF entity apparatus by using an onReceivingMessage plug in API . The OITF entity apparatus outputs the application message received through the web application . In the present exemplary embodiment the onReceivingMessage plug in API is provided to process the event informing the reception of the application message. However other plug in APIs performing the same functions having other method names other input arguments and other return values may be used.

A user of an OITF entity apparatus acquires a message for applications providing the IPTV communication service through the web application in operation . The acquired application message is transmitted to the web browser by using a sendSMS plug in API . In the present exemplary embodiment the sendSMS plug in API is provided to acquire the application message. However other plug in APIs performing the same functions having other method names other input arguments and other return values may be used.

In operation the IPTV middleware of the OITF entity apparatus transmits the application message to an IG functional entity apparatus by using the HTTP protocol.

In operations through the application message is converted into the SIP and is transmitted to a P2P CE entity apparatus from an IG functional entity apparatus via an ASM entity apparatus . As illustrated in a session that is previously set does not exist between the IG functional entity apparatus and the P2P CE entity apparatus .

In operations through a response message including a result of processing the application message is transmitted to the IG functional entity apparatus from the P2P CE entity apparatus via the ASM entity apparatus by using the SIP.

In operations through the OITF entity apparatus receives the response message including the result of processing the application message from the IG functional entity apparatus and outputs the result.

A user of the OITF entity apparatus may receive an application message from a remote user who uses the IPTV communication service applications.

In operations through the application message received from the remote user is transmitted to the IG functional entity apparatus from the remote user by using the SIP. In the present exemplary embodiment the remote user who uses the IPTV communication service applications is a user using the POTS. However the present exemplary embodiment may be applied to remote users who use other services.

In operations through the OITF entity apparatus receives an event informing about reception of the application message from the IG functional entity apparatus .

In operation the received application message is transmitted to the web browser of the OITF entity apparatus by using an onReceiveSMS plug in API . The OITF entity apparatus outputs the application message received through the web application . In the present embodiment the onReceiveSMS plug in API is provided to process the event informing about the reception of the application message. Other plug in APIs performing the same functions having other method names other input arguments and other return values may be used.

A Buddy object includes a callerID property a Name property a friendlyName property a logoURL property and a status property wherein the callerID property represents a callerID of a user the Name property represents a name of the user the friendlyName property represents a nickname of the user the logoURL property represents a logo URL of the user and the status property represents a state of the user.

A BuddyGroup object includes a buddyGroupName property a buddyGroupID property a length property an item method an addBuddy method a deleteBuddy method a modifyBuddy method and a modifyBuddyGroupNam method wherein the buddyGroupName property represents a name of user groups the buddyGroupID property represents an identifier of the user group the length property represents a length of the user in the user groups the item method checking the users of a designated index the addBuddy method adds the users the deleteBuddy method deletes specific users the modifyBuddy method modifies information of the specific users and the modifyBuddyGroupName method modifies the name of specific user groups.

A BuddyGroupCollection object includes a length property an item method an addBuddyGroup method a deleteBuddyGroup method a findBuddy method and a createBuddy method wherein the length property represents the number of user groups formed of the list of users the item method checking the user groups of a designated index the addBuddyGroup method adding the user groups the deleteBuddyGroup deleting specific user groups the findBuddy method checking specific users by using callerIDs and the createBuddy method generating an instance for adding specific users.

A presence object for the presence application includes a BuddyGroupList property a permitSharingCurrentContent method and an inviteSharingExternalApplication method wherein the BuddyGroupList represents the user groups formed of the list of users the permitSharingCurrentContent method provides a function of viewing contents of a current user together with another presence user and the inviteSharingExternalApplication method provides a function of using an application of a current user together with another presence user.

A Messaging object for the instant message application includes an onReceiveSMS property and a sendSMS method wherein the onReceiveSMS property informs reception of a message with a callback and the sendSMS method provides a function of sending a message.

A ChattingManager object for the chatting application includes a callerList property an onReceivingMessage property a onInviteChat property a createSession method a closeSession method an inviteChat method and a sendMessage method wherein the callerList property represents a list of users who are able to chat the onReceivingMessage property informs about reception of a message with a callback the onInviteChat property informs about chatting invitation with a callback the createSession method sets a session for the chatting application the closeSession method completes a session for the chatting application the inviteChat method provides a chatting inviting function to the list of selected users and the sendMessage method sends a chatting message.

A CallManager object for the VoIP application and the MoIP application includes a width property a height property a volume property a bFullScreen property an onFullScreenChange property an onCallError property an onCallSucceeded property an onCalllnvited property an onVolumeChanged property an onPipPositionChanged property a makeCall method an acceptCall method a cancelCall method a hangupCall method a rejectCall method a setPipPosition method a setEableMyCamera method a setEableMyMIC method a setFullScreenCall method and a setvolume method wherein the width property represents the width of a screen the height property represents the height of a screen the Volume property represents the volume the bFullScreen property represents a setting state of a full screen the onFulIScreenChange property represents a change state of setting information of a full screen the onCallError property informs about a phone call error event the onCallSucceeded property informs a phone call success event the onCalllnvited property informs about a phone call invitation event the onVolumeChanged property informs about a volume information change event the onPipPositionChanged property informs about a PIP position information change event the makeCall method sets a VoIP MoIP connection the acceptCall method receives the VoIP MoIP connection the cancelCall method cancels a VoIP MoIP connection service the hangupCall method stops the received VoIP MoIP service the rejectCall method rejects the VoIP MoIP service the setPipPosition method sets VoIP MoIP screen position information the setEableMyCamera method sets a camera of the MoIP service the setEableMyMIC method sets a microphone of the VoIP MoIP service the setFullScreenCall method sets a full screen of the MoIP service and the setVolume method sets the volume of the VoIP MoIP.

The OITF apparatus according to the present exemplary embodiment includes a web application unit a plug in unit an application message sending unit a session setting request unit a session completion request unit a response message receiving unit an application message receiving unit a session setting response unit a session completion response unit .

The plug in unit includes a first plug in unit a second plug in unit a third plug in unit a fourth plug in unit a fifth plug in unit and a sixth plug in unit .

The first plug in unit acquires an application message for the IPTV communication service from an external input through a general purpose web application by using plug in APIs of a web browser which are independent of an IPTV communication service provider. The plug in APIs for acquiring the application message for the IPTV communication service include remote user identifiers and a message to be set to the remote user as input arguments.

The application message sending unit sends the application message to the IG functional entity apparatus .

The response message receiving unit receives a response message including a result of processing the application message as a response to sending the application message from the IG functional entity apparatus .

The application message receiving unit receives an application message for an IPTV communication service from the IG functional entity apparatus .

The second plug in unit transmits an application message to a web browser by using plug in APIs for processing an event informing about reception of the application message. The plug in APIs for processing an event informing about reception of the application message include the received message as return values.

The third plug in unit acquires a session setting request message for an application providing the IPTV communication service from an external input through a general purpose web application by using the plug in APIs. The plug in APIs for acquiring the session setting request message include a session identifier ID as a return value.

The session setting request unit sends the session setting request message to the IG functional entity apparatus .

The session setting response unit receives a response message for the session setting request message from the IG functional entity apparatus .

The fourth plug in unit acquires a session completion request message for an application providing the IPTV communication service from an external input through a general purpose web application by using the plug in APIs. The plug in APIs for acquiring the session completion request message include a session ID as an input argument.

The session completion request unit sends the session completion request message to the IG functional entity apparatus .

The session completion response unit receives a response message for the session completion request message from the IG functional entity apparatus .

The fifth plug in unit performs at least one of the plug in APIs providing a list of users who use the IPTV communication service the length of the list of users specific user information for a specific index in the list of users a function of adding a specific user to the list of users a function of deleting a specific user from the list of users and a function of modifying a specific user in the list of users.

The sixth plug in unit performs at least one of the plug in APIs providing the number of user groups formed of the list of users who use the IPTV communication service specific user group information for a specific index in the user groups a function of adding a specific user group to the user groups and a function of deleting a specific user group from the user groups.

The OITF apparatus according to the exemplary embodiments of the present invention may include a bus coupled to each unit illustrated in the OITF apparatus of at least one processor coupled to the bus and a memory coupled to the bus for storing commands received messages or generated messages and the memory is coupled to the at least one processor for executing the commands.

The invention can also be embodied as computer readable codes on a computer readable recording medium. The computer readable recording medium is any data storage device that can store data which can be thereafter read by a computer system. Examples of the computer readable recording medium include storage medium such as magnetic storage medium for example read only memory ROM floppy disks and hard disks and optical data storage devices for example CD ROMs and DVDs . The computer readable recording medium can also be distributed over network coupled computer systems so that the computer readable code is stored and executed in a distributed fashion.

While the present invention has been particularly shown and described with reference to exemplary embodiments thereof it will be understood by those of ordinary skill in the art that various changes in form and details may be made therein without departing from the spirit and scope of the present invention as defined by the following claims.

