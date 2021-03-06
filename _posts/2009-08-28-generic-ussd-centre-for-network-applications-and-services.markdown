---

title: Generic USSD centre for network applications and services
abstract: The invention relates to a digital telecommunication system for the access, navigation, and use of digital applications and services, referred to as a USSD CENTRE (), that comprises at least one server for applications and services module (), at least one access gateway module (), at least one network gateway module (), at least one integration gateway module () and at least one database and profiling module (). The server for applications and services module (), referred to as a Browser (), is based on at least one USSD telecommunication protocol and on at least one VXML language interpreter (). The USSD CENTER () further includes charging, billing, proxy, routing, observation, ranking, and self-learning modules that execute the respective operations in real-time or offline. The USSD CENTER () further includes a WEB-type environment module for creating multilingual services, for test and for development of services and for managing the versions of the said services either locally or remotely. A method is implemented using the system (), thus enabling a user to access USSD services via existing or new non-USSD services and enabling a user to access existing or new non-USSD services via USSD services.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09060256&OS=09060256&RS=09060256
owner: 
number: 09060256
owner_city: 
owner_country: 
publication_date: 20090828
---
Applicant claims priority of Application PCT FR2009 001045 filed Aug. 28 2009 which claimed priority from French Application No. 0804815 filed Sep. 2 2008 and from which Applicant also claims priority.

The present invention is positioned in the area of conversational applications and client server applications more particularly in the field of dynamic dialogues between a terminal and a server for applications and services using interactive interfaces giving the ability to reach dialogue exchange information and use different applications and services.

The present invention is positioned in particular in the area of mobile telephony in a context of expansion of new features addition of interactive services convergence of dialogue and communication means between heterogeneous devices such as mobile phones mobile devices digital applications and services platforms Internet servers third parties services and devices and others.

In the era of new emerging technologies there is an increasing need to conceive systems for applications and services in particular generic servers based on simple for implementation and use protocols with ability for interactive intuitive easy to use navigation and fast integration.

To these characteristics are added the scalability requirements relative to the English word scalability which indicates the property of re dimensioning a system or a method respectively in term of components or steps of quality size resolution band width or other .

However the cost constraint in material and human resources to set up such systems is important. The technical problem to be solved is thus to conceive with the lower possible cost a system for application and services allowing to set up multiple and reusable applications and services targeting the mass market. The problem is also to fulfill the increasing need for compatible interactive services enabled on existing and emerging technologies without expensive integration and preferably with little or without modifications of network and user equipments.

To answer these problems prior art knows various approaches which however address only restricted and specific aspects of these problems making possible concrete applications however without proposing complete services such as navigation in various menus providing from various applications use of already available means in the devices as standard implemented functionalities in native way and also without important modifications of the digital servers or the end users equipments.

A known document of the prior art is the document FR2857816 which relates to a method for implementation of a voice communication WAP Wireless Protocol Application or MMS Multi media Message Service on a mobile phone. In the communication method a preliminary step consists in offering the user with the possibility to activate or not such a communication. The choice to activate or not such a communication is proposed to the user by an USSD connection Unstructured Supplementary Service Data .

Nevertheless this document is limited to the establishment of a connection for activation of a telephone voice communication via USSD without however approaching aspects of architecture or implementation of navigation and auxiliary services.

Another well known document of the prior art is the document EP0986275 which relates to a transaction method for ordering consumer items or services with a mobile phone. In this case an order for delivery is transferred to a service provider using the mobile network. Some order data including billing is encapsulated in one or more short communication messages such as SMS Shorts Message Service short textual message being able to be emitted and received by a cellular phone USSD or e mail. The data is transmitted to a validation platform connected to an enterprise center for short term communications. The cost of the indicated services is charged to the user account and it is transferred towards the service provider account.

However this document relates foremost to the aspects of a specific transaction based on existing protocols but without addressing the problems of interactive USSD navigation systems or architecture for USSD generic equipment.

Another prior art reference is the document FR2819675 relative to a cell phone that includes a browser for a computer network such as Internet means for capturing computer addresses received by the browser to control storage means and recall of computer addresses provided in the phone. The phone also includes means for generating and presenting electronic icons means for selecting these icons means for storing icons and means for matching icons and computer addresses stored in the computer memory and means to recall them.

However this document relates to a browser implemented in the user device and does not address aspects related to interpreters and browsers implemented on the network.

A document also known by the prior art is the document WO 2007 030413 concerning a control channel for a VXML browser Voice eXtensible Markup Language language voice extended tagging which means an application programming interface for communication using peripheral devices related to the speech synthesis and telephony . This document focuses on a system that allows external applications to interact with a VXML browser running on a processor based on VXML interpreter. A control is functionally positioned between the external application and the VXML interpreter using a communication channel. The control inserts into the VXML interpreter instructions which are processed by the VXML browser in a conventional manner to allow the external application to interact with the VXML browser.

However this document is limited to the interpretation and to the VXML browser capabilities and their adaptation to a transport channel with standard protocols such as UDP User Datagram Protocol communication protocol providing for the exchange of a minimum of data across a network TCP Transmission Control Protocol basic protocol for exchanging data over a network or SIP Session Initiation Protocol standard protocol for initiation of an interactive network session . Therefore this document does not resolve the technical problem outlined in the present invention namely the navigation in non voice services such as USSD or other and any issues related to the specificity of the implementation and the integration of such a navigation.

The present invention relies on existing standards and protocols open and already implemented on devices thus already available. It is based on native functionality of networks and of terminals by providing a generic multi applications and multi services architecture. In addition the implementation and the integration centralized on networks side allow an optimal management of network resources and implementation efforts.

The present invention aims to overcome the prior art lack and to solves the stated technical problem by using an unique method and a generic system for multiple applications and services. The implementation of this method is based on the use and the adaptation of network protocols such as USSD with interpreters related to structured languages descriptors.

The present invention relates to a system for network applications and services based on standard network protocols such as USSD containing at least one server for applications and services including a dynamic interactive browser based on a language interpreter structured by conversational objects such as VXML. The system for applications and services based on USSD protocols is centralized in a telecommunications or computer network. The browser based on a VXML interpreter is integrated on the network.

In its broadest meaning the present invention relates to a digital telecommunications system for the access navigation and use of digital applications and services called USSD CENTER which includes at least one server for applications and services module at least one access gateway module at least one network gateway module at least one integration gateway module and at least one database and profiling module said server for applications and services module called Browser being based on at least one USSD telecommunication protocol and on at least one module interpreter of languages structured by objects relative to descriptors structured by objects.

In another embodiment the system is connected to at least one module such as WAP gateway and or OTA and or IVR and or GPRS for any telecommunications network.

Advantageously the system is connected to at least one set of network based on communications protocols and interfaces.

In one embodiment the system is connected to at least one services module of telecommunication operators or of third parties and or to at least one module for mobile value added services.

In another embodiment the system is connected to at least one module of systems said intelligent networks and for business support.

Advantageously at least one server module for applications and services or at least one access gateway module or at least one network gateway module or at least one integration gateway module or at least one database and profiling module is self sufficient.

Preferably the server for applications and services includes at least one VXML interpreter at least one USSD services module and at least one VXML files module.

In one embodiment the USSD services module includes USSD services unstructured or structured in menus said USSD services being interactive or non interactive.

In a preferred embodiment example the service logic is independent of services language for the whole end to end chain.

Preferably said USSD CENTER includes at least one charging module and or at least one billing module and or at least one observation and ranking module.

In a second preferred implementation the USSD CENTER is as system for hosting of third parties applications and services.

Preferably an administration module includes a WEB like system administration environment for creation testing deployment of services and version management of these services a control module of the USSD CENTER and configuration modules for features parameters and network gateways.

The present invention relates also to a method that is performed in a step of codes allocation for the USSD services or generic a step of service logics creation a step of testing evaluation and versioning of the services and a step of services activation deployment use and backup.

In another implementation the method also includes an additional step of billing in real time or offline.

Advantageously the method includes a step of convergent unification of payment modes for all types of users postpaid mode prepaid mode third party mode of at least one telecommunications network.

In one embodiment the method includes an additional step of distribution of data and services such as Broadcast.

Preferably the Broadcast distribution step is followed by a step of interactive or not interactive exchange with the user.

In one embodiment example the method includes an additional step of subscription and or unsubscribe to at least one third party application.

In another embodiment example the method performs the differentiation of the users the users being subscribers and or third party applications or services in real time using a dynamic customization.

In a preferred embodiment users being subscribers and or third party applications or services manage themselves their own environment for creation of services applications and contents.

Advantageously the environment for creation of services is accessible locally or remotely from a terminal by the operators and or the third parties and or the subscribers themselves.

In a first embodiment the method defines at least one profile of at least one user and or of at least one service.

In a second embodiment the method performs a detection of the user behavior and generates features for assistance and or self study.

In a first particular implementation the user accesses the USSD services via existing or new non USSD services.

In a second particular implementation the user accesses the existing or new non USSD services via existing or new USSD services.

In a third particular implementation the user accesses the existing or new USSD services via existing or new USSD services.

In a fourth particular implementation the user accesses the existing or new non USSD services via existing or new non USSD services.

In one embodiment the method includes a step of static and or dynamic modifications of the switched parameters.

Preferably the USSD browsing performs the supply the consultation and the modification of at least one information managed in the core network.

The general scheme of the present invention is illustrated in . A platform for applications and services called in the present invention CENTER for applications and services or also CENTER is designed to perform and to bill services for example such as messaging USSD or SMS Short Message Service or other such as Browsing i.e. navigation such as Hosting and such as Broadcast i.e. distribution of data from a single source to a set of receivers.

The CENTER is a generic open system multi applications and multi services which provides services compatible with standard protocols used in mobile phones such as for example the protocols SS7 Signaling System 7 telecommunications protocol for high bits rate connections in circuit mode and or IP protocols Internet Protocol .

In the present invention under the term USSD generic system is understood a system based on standard protocols existing or new enabling the implementation by using USSD of any service and any existing or new application. Said center is located within a server in a network such as mobile telecommunications network SS7 network 3G 3G network NGN network Next Generation Networks the generic name of any future telecommunications network Internet computer network or any other digital network. This CENTER consists of five main modules a server for application and services with a browser called herein Browser said Browser being based on at least one USSD protocol an USSD access gateway a networks gateway based on protocols compatible with telecommunications networks an integration gateway dedicated to information technology systems information and a data and profiling database .

In a general case said CENTER consists of at least one server for application and services of at least one access gateway of at least one networks gateway of at least one integration gateway and of at least one data and profiling database .

In a second particular case at least one module or at least one module or at least one module or at least one module or at least one module is self sufficient.

In the present invention is understood that a networks gateway is a platform or a set of intermediate platforms which processes and transmits information packets on a network or on multiple networks to the specified destination and allows heterogeneous networks to communicate. Under the term gateway is understood therefore a networks gateway to any network including at least one network interface.

The integration gateway communicates with the server for applications and services said Browser via the link and using at least one interfacing protocol for example an IP standard protocol.

Under standard IP protocol is understood the set of IP protocols used in the networks. The Browser communicates with the USSD access gateway via the link and using protocols for example such as IP or SMS applications protocol such as SMPP Short Message Peer to Peer . The Browser communicates also with the network gateway via the link using standard IP protocols for example. The Browser exchanges data with the data and profiling database via the link using protocols such as IP. Said data and profiling database contains information for example on white lists and black lists regarding various users on users profiles on the services profiles and on the various usage statistics used in the analysis and the service management. The module also includes modules for static or dynamic definition of at least one user profile and of at least one service profile. Subsequently said CENTER such implemented is called USSD CENTER .

The USSD CENTER is connected through the USSD gateway to a network such as Core Network Core Network basic central network or core of the telecommunications network . The Core Network is for example such as core network for GSM Global System for Mobile telecommunications GPRS General Packet Radio Services communications system with access using packets services UMTS Universal Mobile Telecommunications System 3G 3G and or any other core network such as for NGN. For instance the network is such as SS7 and communicates with the USSD CENTER via the link through which the communications are exchanged for example using the MAP protocol Mobile Application Protocol protocol for mobile applications .

In another implementation the USSD CENTER is connected to the network through the network gateway via a link and using one or more protocols such as SS7. For example said link consists of a CAP protocol CAMEL Application Part application part protocol of CAMEL protocol Customized Applications for Mobile network Enhanced Logic allows a telecommunications operator to provide inside or outside of its own network special services to its users such as real time billing of a INAP protocol Intelligent Network Application Protocol application part for intelligent applications on SS7 protocol or of a MAP protocol.

Said core network includes different modules with which the network gateway and or the USSD gateway exchange data. For example these modules are such as HLR module Home Location Register MSC module Mobile Switch Center center for mobile communications VMSC module Visited Mobile Switching Center visited center of mobile services GMSC module Gateway Mobile Services Switching Center switched mobile services gateway SIGTRAN module set of protocols defined for transporting SS7 messages over IP or any other module related to mobile telephony.

Said core network exchanges information via the link with the set of the users and or . The set of users is for instance such as network RAN Radio Access Network the radio access network for mobile phones for GSM EDGE UMTS 3G 3G or for example such as PSTN Public Switched Telephone Network NGN or any other digital network of a set of users. The communication link is set up using standard protocols.

The user equipment said terminal is for example a mobile phone said also cell phone a PDA Personal Digital Assistant handheld computer combining many functions a multi functions board computer or for vehicle a home or business multi platform including for example a monitoring or safety function or any other fixed or mobile device being able to communicate with at least one network.

In the present invention under the term user is understood an individual subscriber fixed nomadic or Roamer roamer itinerant subscriber in the sense of roaming between networks to at least one network or a third party for example a provider of applications of services of contents or of any equipment for example alarm or signaling equipment.

The network gateway is also connected to a services platform via the link and using protocols such as IP. The services platform is for example WAP gateway OTA Over The Air standard protocol for transmitting and receiving information relating to an application for mobile phones IVR Interactive Voice Response or GPRS for instance MMSC Multi Media Messaging Service Center multimedia service center . This platform is also connected to the telecommunications network via the link and using standard or specific protocols for example such as SS7 or IP. The gateway is also connected to a module which is such as SMSC SMS Center via the link and using protocols such as SMPP. The SMSC module is itself connected to the telecommunications network via a link using communications protocol such as SS7.

Preferably the Browser is also connected to the SMSC module via the link and using protocols such as SMPP. In this case the USSD services are also offered as SMS services. Also The USSD services are offered as services WAP IVR OTA GPRS or 3G 3G .

A third module for processing of SMS applications treats the SMS queries and communicates in a conventional manner with the SMSC module via the link and protocols such as SMPP.

In a particular implementation of the USSD CENTER the application SMS queries of the module are transmitted via the links and with protocols such as SMPP and are processed directly by the USSD access gateway allowing these external SMS services to be available in USSD.

Also other existing non USSD services such as IVR OTA WAP GPRS or 3G 3G are available via USSD. In general using this architecture the user accesses the USSD services via non USSD services existing or new and also the user accesses the non USSD services existing or new via USSD.

The USSD CENTER is connected via a link which is for example such as IP to a set of IP networks which includes various protocols linked to platforms for applications and services and . Through this set of networks the USSD CENTER has access to platforms for example such as VAS mobile Value Added Services . Data between this set of networks and the platform are exchanged via the link using standard protocols such as for example VXML HTTP HyperText Transfer Protocol text transfer protocol SOAP HTTP Simple Object Access Protocol standard protocol for the WWW services World Wide Web or WEB global network XML HTTP XML extended Markup Language extended markup language for describing and analyzing data SMPP or using proprietary protocols such as for example ORACLE server for interface and applications for mobile chain MySQL relational database LDAP Lightweight Directory Access Protocol simplified protocol for accessing databases DIAMETER IP extension for mobile RADIUS IP extension for mobile MML Man Machine Language or other kinds of protocols.

According to one implementation through the network the USSD CENTER has access to a platform such as for example ASP Applications Service Providers providers for applications and services or such as MVNO Mobile Virtual Network Operator or other third parties such as for instance banks with which through the network the USSD CENTER exchanges information via a link such as .

In a particular embodiment a portion of the set of networks is connected with one or many platforms of the network via for example an IP link such as MML or TELNET TELecommunication NETwork network protocol to remotely execute controls . This is an effective and practical way for the USSD CENTER to propose via browsing the supply the consultation and the modification of the information managed in the core network and by default inaccessible for the users.

In one embodiment example the network has access to the service platform such as for instance BSS Business Support Systems via the link using protocols such as INAP MAP CAP and CDR Call Data Records recording of the call data . The BSS module is for example such as post paid billing module or a prepaid billing module such as IN Intelligent Network concept defining advanced functions driving the equipments of the phone network .

The platform is also connected via the link using specific or proprietary protocols to a gateway which is for example such as USSD dedicated to modules such as BSS. The gateway communicates with the network via a link using the USSD MAP protocol and with the USSD gateway via a link using the USSD MAP protocol. The link is in this case merged with any link such as . This particular connection makes it possible to configure the architecture of for new services.

In a particular embodiment the platform exchanges information with the network via the link using standard or proprietary protocols specific to the platform such as for example Ericsson UCIP User Communication Integration Protocol Ericsson specific protocol Huawei MML the applications protocol Corba for NSN Nokia Siemens Network BSS Corba for Alcatel BSS or Corba for LHS BSS. In another embodiment the platform is directly connected to the network gateway via the link using standard or specific protocols.

The generic architecture described in this no limiting example comprising the modules and the links illustrated in presents a dynamic and interactive system for the access and the use of multiple applications and services by users of at least one telecommunications network . Using this architecture new services are offered to users through classical interfaces such as USSD SMS IVR WAP GPRS or 3G 3G . In addition an USSD access is opened to the users for existing classical services such as SMS IVR WAP GPRS or 3G 3G .

Also classical and difficult to use network features such as call forwarding Roaming functions roaming inter network roaming short numbers callbacks and others are made convenient and easy to use thanks to the USSD CENTER . In addition real time services are offered such as for example the differentiation of a user in roaming mode and for example an appropriate dynamic customization and profiling.

Advantageously are added supplementary modules such as or of telecommunication operators or of third parties. In this way the architecture shown in including the module the network and the modules and has properties of scalability adapted to the capacity of processed information in terms of data applications services networks or others.

The USSD CENTER manages applications and services in function of the network resources and plans routing of each task in function of the available bandwidths or queries requesting additional allocation of resources.

In a particular embodiment telecommunication operators have access to this architecture in order to do operational and load testing of external systems. The USSD CENTER therefore offers possibility for connections and testing of additional modules. Preferably all connections of the USSD CENTER to external systems are based on pre requisites for security of these systems. The exchanges are unsecured or secured using for example an encryption such as for example SSL Secure Socket Layer a protocol that encrypts data sent by a browser or other .

The present invention is detailed below with preferred and not limiting embodiment examples. In a preferred implementation the Browser is designed based on USSD protocol and on a structured VXML language interpreter.

Said browser includes at least one interpreter of language structured by object . In this preferred example of implementation the interpreter is such as VXML. The VXML interpreter exchanges information with a module containing lists of services or also USSD menus via the link and using protocols such as VXML. USSD menus are unstructured or structured. At least one given service is described using call of VXML files via the link and using VXML protocol in order to identify the context and the properties of the communication with each user of mobile phones. In this case the Browser is based on VXML.

In this way the navigation is done through menus such as USSD. All USSD services of the module are deployed in the browser as VXML files for example VoiceXML v2 and downloaded into the memory of the VXML interpreter . Preferably the VXML interpreter is designed to take into account the specifications of the USSD protocol communication. The VXML interpreter uses internal virtual memories or caches for already interpreted queries and thus they are interpreted for the same USSD sequence without navigation i.e. without a new interpretation of the already explored service tree structure.

In a first preferred embodiment said Browser is configured as a browser. The browsing logic is similar to that of a WEB browser. Configuration interfaces indicate lists and sub lists of all principal existing services and applications these lists and sub lists are respectively called pages and sub pages or menus and submenus.

For example USSD service codes are generated and assigned to menus. In one embodiment the USSD service codes are assigned to all menus. In another embodiment the service codes are assigned to some of the menus.

Preferably the menus represent at least one USSD page these USSD pages being linked to a browsing logic. The menus are enabled or disabled for example by an internal administrator and their state is indicated in the USSD CENTER with configuration messages stored in the data and profiling database .

The browsing method including the generation the allocation and the management of menus is defined by several steps 

The Browser allows thus to perform browsing from a main menu to sub menus with direct access through an USSD string creating a shortcut . The shortcut includes sequence of user response from the USSD screen to modify.

The Browser interprets each parameter of the USSD string from the user in a sequential way and will then display the appropriate menu. In the case where the menu is a last node the Browser will send a query such as HTTP to a service provider which will as feedback provide for example the desired content.

Using the Browser dynamic operations are set up and performed such as navigation with feedback navigation from a main menu navigation from an intermediate menu browsing interruption. Advantageously these operations are accompanied by analysis capabilities configuration and store in the user profile. Under the term user profile is understood the set of characteristics related to at least one connection and to at least one session for example IP address phone number location time and date of the connection duration of the connection language of the browsing geographical location types of required applications and services required contents and any other characteristic related to this connection.

Preferably the USSD CENTER contains a multilingual menu configuration for the whole end to end chain between the final subscribers and the service providers for example . Also the services logic is independent of the languages for the whole end to end chain.

The Browser as designed has network architecture and connections which are multiple dynamic and interactive. The Browser includes internal connectors for example communication interfaces with the gateways and and these internal connectors may include at least one sub connector. By using the connector the Browser communicates with the integration gateway via a link . The Browser is also connected to the USSD access gateway via the USSD connector and a link . Also the Browser communicates with the network gateway via the connector and a link .

In a particular embodiment the network gateway is connected to the platform via a link such as specifically with modules such as IVR WAP and WEB . In this way services such as IVR WEB or WAP are proposed via USSD protocols. In general any digital service and any new or existing application for network systems can be set up by USSD protocols.

In another particular embodiment the network gateway is connected with the services platform SMSC via the link . The integration gateway exchanges data with the BSS platform via the link which is a composition of link network and link . Also the networks gateway exchanges data with the said BSS platform via the link . In a first implementation example the module is connected only to the module . In a second implementation example the module is connected only to the module . In a third implementation example the module is connected to the module and to the module .

The data and profiling database comprises a module for defining of at least one user profile and at least one service profile and exchanges separately information with the module via the link with the module via the link with the module via the link and with the module via the link . In this manner configuration information various administration data statistics and information about users and services profiles are completed used and inter exchanged between the modules and .

In a particular embodiment example the data and profiling database is connected only with the Browser via the link in which case the links and are omitted. Preferably the data and profiling database contains information on the characteristics of sessions static and dynamic statistics.

In a second preferred embodiment the Browser is configured such as Hosting platform or hosting of applications and of external or third parties services. Third parties access is enabled in a secure way for creation and activation of applications and services. These third parties then operate only the codes of the services they offer.

The embodiment such as hosting in the present invention allows telecommunication operators to set up USSD services operated by third parties such as service providers. The third parties access is completely secured. Telecom operators create one or many accounts for each third party by attributing at least one access code and USSD resources. Each service provider uses the same user interface as the telecom operator and operates remotely its own USSD application in the operating limits assigned by the telecommunications operator. For each services provider is recorded history of activities and of operations. Furthermore the environment for creating services and applications is provided not only to services providers but also to various users and subscribers who in this way adapt and customize their own applications services and contents. In a third preferred embodiment the USSD CENTER is configured as an USSD proxy module of an USSD system connected to another USSD system and performing queries and their backup for the services needs . This embodiment concerning for example the module is achieved via the specific gateway . The classic link connecting the gateway to the network is then merged by the module with the link connecting the gateway to the USSD gateway . The applications and services of module are then appropriated by the USSD CENTER .

In this way it becomes possible for the operator to group several USSD access codes in a single access code and also to introduce new services USSD or not which are not feasible without modifications of existing network elements. In a fourth preferred embodiment the USSD CENTER is configured as active routing platform which provides USSD like mediation between different network elements and solves problems related to routing of users of services and of applications. These problems are for example the routing of the user towards a BSS platform the routing such as MNP Mobile Number Portability and others.

When the USSD CENTER performs proxy and router functions it has the ability to make static and or dynamic changes on commuted parameters.

When the USSD CENTER performs proxy and router functions it has the ability to perform load sharing functions.

In a fifth preferred embodiment the USSD CENTER is configured to perform distribution such as Broadcast of data and services to multiple users for example broadcast advertising event alerts or other useful information. In one implementation the Broadcast is followed by a user response and interactive exchange for example for applications such as consumer enquiries and surveys.

Moreover a Broadcast service creation environment allows to services providers and end users to adapt and customize their own Broadcast distributions.

Advantageously the Broadcast environment of the USSD CENTER enables the operators to launch also conventional broadcast services such as SMS IVR WAP GARS or 3G 3G .

In an embodiment example of the USSD CENTER the Browser communicates via the link with a billing module . In this way the contents requested by the same user are generally subject to a control and to a billing in real time or offline.

In another embodiment example of said USSD CENTER the Browser communicates via the link with a charging module .

Both embodiments are applied to any kinds of users with subscription prepaid mode roaming fixed or nomadic.

The USSD CENTER manages for example the billing with subscription or in prepaid mode by using an approach called external payment procedure. A specific procedure for external billing is specified in the USSD services logic during the creation of the service and is triggered in real time during the user session. The payment procedures are in accordance with the specific payment requirements of the operator or the third party.

During the session a mobile user in roaming is also identified so that his navigation is taken into account in an appropriate way during the payment procedure. Advantageously this case is available through the use of the USSD CENTER functionalities.

In general the USSD CENTER includes a payment system that makes the charging and or the billing in real time or offline and therefore allows the convergence of the different services and modes of payment prepaid with subscription and mixed .

In a particular embodiment example users subscribe to any service using the USSD CENTER . Preferably the USSD CENTER includes a feature to change or to automatic cancel the subscription either following the request of the user or following the request of the services provider.

In one particular implementation of said USSD CENTER the Browser communicates via the link with a module for which a method of observation and ranking is defined. Preferably the method of observation and ranking makes in real time or offline observation analysis and ranking of user behavior content services providers and other users. This method is used for example for the analysis and ranking of services and their subparts and also for revenue generation. The observation and ranking parameters are defined during or after the process of service creation.

During the session network management administration integrated in the USSD CENTER generates in real time the required parameters and automatically creates an observation and or ranking events.

In one embodiment example the billing module the charging module and the observation and ranking module are integrated within the Browser module . The internal management administration of the USSD CENTER is connected with the Browser and therefore with the VXML interpreter via a link . The module is able to support at the same time all the deployed services including generic USSD operations initiated by the telecommunications network and the mobile terminal as well as sessions or dialogue of a bilateral USSD session. The observation and the ranking are applicable to service providers and to users. The observation is based on defined parameters such as for example the type of the event the date and time of the event the duration of the session the number of exchanges during the session the application code of the service end user or any network the VAS provider the message content based on keywords or content codes the location of the end user. Also a combination of observation factors is correlated with event phenomena such as for example holidays sports championships advertising campaigns.

In its most general definition the administration module includes a system administration such a WEB including a WEB environment for creation of services testing deployment and version control of these services a management module of the system USSD CENTER and modules for features parameters and network gateways configuration. The environment for services creation is accessible locally remotely or from a terminal by the operator and or by third parties and or by users themselves. The administration system controls connections data collection analysis and statistics. The system administration module is connected with at least one other internal module of the USSD CENTER other than the Browser . The system administration is for example connected with the integration gateway via link with the USSD gateway via link with the network gateway via link and with the data and profiling database via link .

Thanks to the data and profiling database the USSD CENTER has the ability to determine in real time the profile of a user or of a group of users. The user profile is completed by its usage profile relative to at least one service and to a set of parameters specific to the sessions for this service. By using the data and profiling database the USSD CENTER has the ability to determine in real time the profile of a service or a set of services. This profile consists of information such as for example the lack of accessibility to free services or to a particular group of users the definition of white and black lists and others.

In function of the detected user behavior the USSD CENTER has the ability to trigger an event for assistance by setting up a self learning. Thus the USSD CENTER delivers in real time assistance adapted to the user when such is necessary. In one embodiment the USSD CENTER offers management of services and of contents performed directly by users. For example the services and the contents are created or customized by the user himself using a WEB site or directly using the mobile terminal.

Preferably the USSD system for browsing and for hosting generates CDR files. Once created for instance the files for billing are available for the telecommunications operator or for the services providers. The frequency of updating of these files is for example at least once per minute. Their format is for example such as ASN.1 Structured Abstract Syntax Notation One Structured standard way for describing a message sent or received by the network .

In one particular implementation the CDR files syntax is adapted by the telecom operator and some parameters are modified. The various CDR formats are generated using presets parameters. For each node in the tree of the service logic the choice of CDR formats and their uses by an administrator are flexible. Said administrator is in this case an operator a services provider or any third party to whom the administration of the services has been delegated. illustrates a non limiting embodiment example of the architecture referenced in and with external connectors to the Browser module . The Browser module is represented in architecture with the integration gateway module which includes at least one integration interface module. Preferably the interface modules are based on protocols such as HTTP SOAP XML HTTP CORBA ORACLE MySQL LDAP SMPP CIMD2 Computer Interface to Message Distribution version 2 distributing messages interface Diameter or any integration gateway . In the integration gateway module integration interfaces are such as client server client server or Peer to Peer point to point communication. Also the module is connected via a link such as and using IP protocol with a module comprising a set of services for example VAS services. The module includes for example the module which contains a MVNOs module and an ASP module and includes the module which consists of a VAS module and of a SMSC module . The module communicates with the modules and via a link such as followed by a link as .

The module also includes a service platform such as BSS or IN with which the module communicates via a link such as . Also the module includes an SMS applications platform with which the module communicates via a link followed by a link . In order to access multiple computer and telecommunications networks the Browser module is connected to the network gateway module via a link such as . The module contains at least one network gateway such as SOAP HTTP SMPP CAMEL MAP or any network gateway . In the network gateway module the network interfaces are such as client server client server or Peer to Peer point to point communication.

The module has access to networks for instance via a link which is for example such as and or such as and or such as and or via a link which is for example such as and or such as .

The USSD CENTER is an open platform adapted to existing standards with multi service and multi operator capabilities. The USSD CENTER enables deployment of new services providing opportunities for multiple mobile applications. The user interaction with mobile applications is easy and instantaneous the response time is guaranteed and the interactions during the session are supported unlike of the services such as SMS and GPRS. The USSD protocol is fully supported by the GSM network and the addition of the USSD CENTER in a telecommunication network does not require network modification. The USSD CENTER supports user initiated sessions such as pull pull withdrawal and network initiated sessions initiated by the application server such as push push pushing with unilateral or bilateral interactivity.

Using a simple reconfiguration mobile applications such as SMS STK SIM Tool Kit WAP IVR and others are immediately available.

The fact that the USSD gateway and the USSD Browser are open platforms allows the integration of different network protocols and multiple deployments with capacities of several thousand transactions per second.

For example the USSD CENTER is used for banking services and applications Broadcast advertisement alerts traffic simulation and various network services. Also the USSD CENTER is used for content management by geographical location as well as for multitude of emerging SPs Services Providers applications. Telecom operators have access to the USSD CENTER also to test external systems functionally and under load. Additional modules are integrated such as supervision and security modules or any other fixed or mobile device modules being able to communicate with at least one telecommunications network.

A particular and non limiting embodiment of the USSD CENTER module is performed using hardware platforms such as HP Hewlett Packard FSC Fujitsu Siemens Computers IBM International Business Machines or SUN Microsystems . The operating system is for example such as Red Hat Enterprise or Fedora Linux or such as Sun Solaris .

