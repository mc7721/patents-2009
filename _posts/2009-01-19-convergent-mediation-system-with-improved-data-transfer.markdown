---

title: Convergent mediation system with improved data transfer
abstract: An object is to create a convergent mediation system () and method that meet the technical requirements of low latency time and high reliability. According an aspect of the invention, these objects are achieved by providing a convergent mediation system () that comprises a plurality of independent processing nodes () adapted to form processing streams () for the online processing () and off-line processing () of data. Each of the processing streams () comprises at least two independent nodes () in sequence and buffers () between the nodes (). Furthermore, random access memory is utilized such that at least one of the buffers () in each of the online processing streams () is formed by a dedicated memory area in the random access memory.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09015336&OS=09015336&RS=09015336
owner: Comptel Corporation
number: 09015336
owner_city: Helsinki
owner_country: FI
publication_date: 20090119
---
This application is a U.S. National Stage patent application of PCT F12009 050044 which designated the United States filed Jan. 19 2009 which claims priority to European Patent Application No. 08150558.8 filed Jan. 23 2008 and U.S. Provisional Patent Application Ser. No. 61 006 639 filed Jan. 24 2008 the entire disclosures of which are hereby expressly incorporated by reference herein.

Convergent mediation systems are computer systems operating between a source system and a target system. A typical example of the source system is a telecommunications network and a typical target system is an OSS BSS Operations Support System Business Support System system of a telecom operator.

The present invention relates particularly to a method system and computer program product of mediating data records made in communication networks. The present invention is especially suitable for billing and charging calls and services used in communication networks. The billing and charging can be done simultaneously for both pre paid and post paid methods. The term convergent mediation specifically refers to the applicability of the method and system for both pre paid and post paid charging.

The increasing demand for tailored life style services in the telecom domain is changing the service landscape. Telecom service providers must rethink their offering to create a service palette that their subscribers can control and manage in real time. As a vital link in the supply chain for these services Operations Support Systems OSS must also be flexible and convergent. The main driver for convergence comes naturally from the need to maximise the business potential by the implementation of service and payment convergence that is unifying the service offering to all subscribers independently of the payment type prepaid or postpaid .

In order to achieve service and payment convergence service providers have to face and solve many technical challenges. Firstly there is the challenge of network convergence new networks being implemented along side of the old ones. Service providers infrastructure very often comprises different vendors equipment and various protocols creating challenges of vendor and technology convergence that is the need to integrate with different protocols standards and several vendors equipment. With service and payment convergence an increasing number of service providers are also facing the challenge of billing system convergence the challenge of handling all services payment and account types and rating of services with their often complicated system setups.

Thus one of the technical challenges is the requirement to provide low latency time for prepaid processing.

Another challenge is the reliability of the convergent mediation system No data should be lost even in error situations.

The above mentioned two challenges set contrary requirements to the convergent mediation system and therefore constitute a real technical problem. An extremely reliable system appears to be slow such that the latency time is unacceptable. And vice versa streamlining the data handling processes to shorten the latency time of the system tends to weaken the reliability.

The prior art discloses several convergent mediation solutions that can meet the above challenges with varying degrees of success.

Convergent mediation solutions in the market are typically real time collection based systems that are integrated with legacy pre paid systems. These convergent solutions are mainly a collection of different sets of known devices and systems. An example of such a system is described in .

Traditional off line mediation also called as billing mediation solution contains functionalities like collection of usage data from network elements aggregation conversion of data format to unified format correlation etc. This all has been ready for years and most likely will be used for years to come.

On the other hand online mediation solutions are used for example for charging the non voice services of prepaid customers executing charging for a multimedia session between a mobile terminal and a remote host on both an application media level and on an IP access bearer level and for minimizing credit losses caused by subscribers while at the same time maintaining good performance of the system.

Also the traditional IN based Prepaid Systems have been designed for charging the voice calls of prepaid customers. Already today prepaid subscribers form the majority of the total worldwide customer base and they want to be able to use the same services as the postpaid users. Until now the lack of open real time charging solution has been slowing down the service deployment for prepaid subscribers.

In a preferred online mediation solution an end user session management especially for charging is required. In most of the prior art systems operations requiring faster end user session charging cannot be performed and operations desiring faster end user charging are performed inconveniently. An example of operations that require faster end user session charging is online service offered to an unknown subscriber. An example of an operation that is performed inconveniently is one where subscriber has to give one s credit card number to unreliable host for charging Internet purchases.

Patent application publication WO 2004 095326 discloses a real time and continuous off line mediation method for event records generated by telecommunications network.

Patent application publication WO 2005 027409 discloses an online charging method in communications network.

Patent application publication EP 1761021 A1 discloses one kind of convergent pre and post paid billing architecture. The principle idea of EP 1761021 is that pre and post paid billing systems are combined together with rating and customer management facilities.

Patent application publication WO 2007 020499 discloses an online charging management server used with account management system. These kinds of solutions are also determined by different standardisation organisations like 3GPP ETSI etc.

Patent application publication WO 2007 002577 discloses a converged off line and converged online charging systems with a common rating and charging gateway function.

It is an object of the present invention to create a new convergent mediation system and method that solve the technical problem of providing both reliability and low latency time for data processing.

According to an aspect of the invention these objects are achieved by providing a convergent mediation system that comprises a plurality of independent processing nodes adapted to form processing streams for the online processing and off line processing of data. Each of the processing streams comprises at least two independent nodes in sequence and buffers between the nodes. Furthermore random access memory is utilized such that at least one of the buffers in each of the online processing streams is formed by a dedicated memory area in the random access memory.

According to another aspects of the invention there is provided a convergent mediation method wherein the data processing in an online processing stream includes passing data from a preceding node in the steam to the succeeding node in the steam via said buffer formed by the dedicated memory area in the random access memory.

According to the present invention there is also provided a computer program product for running a mediation system in accordance with the above described method.

The present invention makes it possible to construct a convergent mediation system that can simultaneously provide a low latency time and very good reliability of online processing. Division of the mediation process into a plurality of part processes in independent processing nodes contributes to both reliability and processing speed. This is because the possible errors are localized to particular independent part processes in the respective nodes. At the same time the system is scalable as the number of independent processing nodes can be increased in order to meet increasing processing load for instance. Furthermore even the possible problems caused by such localized error points are minimized by means of buffering the data between the processing nodes using a low latency buffering mechanism utilizing random access memory.

The inventive concept allows also several useful and advantageous embodiments which provide further advantages.

For example it is possible to provide all of said independent processing nodes on a single platform such that both online processing and off line processing is performed on one common platform. In such an embodiment the processing power of the platform can be allocated to the respective processes according to their needs such that the system can offer both a low latency time for online processing and a high throughput for off line processing. Furthermore the common platform embodiment provides the above benefits without compromising interoperability and ease of administration of the system. Indeed the prior are problems with interoperability and administration of the system can be alleviated by these embodiments as there is only one platform for both of said processing types. Consequently there is not anymore need to administrate two or more different processing platforms and try to guarantee their interoperation.

An embodiment of the invention providing a node manager that can start up new nodes when required offers scalability to the mediation system.

Invention offers also embodiments that can be operated continuously once started because all of the configurations can be made while the system is on production.

The invention allows even such embodiments that overcome all the challenges of different types of billing charging and payment convergence. These embodiments help the service providers to differentiate in highly competitive markets by offering smooth evolution of the current networks and BSS OSS environments into a fully convergent solution with the best of breed components for convergent mediation solutions.

Furthermore there are embodiments that are designed for rapid deployment and fast adaptation to new demands. These embodiments enable service providers to launch new and exciting services to the market fast while assuring accurate charging. These embodiments provide reliable usage collection and charging that ensure that the subscribers can be satisfied with the accuracy of their bills or their credit management. A system according to the embodiments is scalable and works equally well irrespective of whether the service provider has 10 000 or 100 million subscribers.

According to embodiments a further advantage is that the mediations system may play a pivotal role both in revenue assurance and in fraud detection. These embodiments can ensure that all usage data is collected and charged online accurately which is fundamental to a mobile service provider s revenue generation. Online capabilities are required to close the revenue leakage that is caused by e.g. hot billing based solutions. There are also embodiments with provisioning capabilities that help also reduce fraud especially in a prepaid environment thus reducing service provider losses. As mobile services and technologies evolve so too should charging models be tailored to a diversifying range of individual needs. There are also embodiments that meet new requirements for example in the migration path to 3G 4G Universal Mobile Telecommunications System UMTS Wireless Local Area Network WLAN Terrestrial Trunked Radio TETRA IP Multimedia Subsystem IMS Voice over IP VoIP IP group calls Push To Talk PTT content service sessions multiplayer interactive game sessions etc.

According to an embodiment of the invention the convergent mediation is processed within a truly one platform. Any distinct processing platforms or devices are not needed. An advantage of this embodiment is that operators need not to process and support several different billing and charging platforms that may be very difficult to adapt together. Today s convergent platforms in the market are integrated collections of existing billing legacy prepaid and account management systems. Typically convergent mediation solution in the market can handle network convergence by supporting multiple access networks e.g. mobile fixed and broadband and related services but does not support payment convergence e.g. online and offline mediation with the same platform. The present invention offers embodiments that provide a truly one solid and efficient convergent mediation platform for online and offline mediation that supports all kinds of billing and charging applications i.e. online cost control IP prepaid Rating and Balance Management. Furthermore the convergent mediation system according the embodiment that is powered with the truly one technology platform can give extremely reliable scalable and vendor independent environment with high throughput high availability and low latency facilities for both online and off line processing.

According to further embodiments operators can handle very cost efficiently their billing and charging though the network and OSS BSS is complex. One aspect of an embodiment of the invention is that the platform is totally and continuously controlled by the system manager which also divides the system capacity to online and off line sub processes.

By means of embodiments the operators and service providers are able in a very innovative way to construct several billing and charging services for their customers e.g. offering balance management services for subscribers. An example of such balance management services is that the pre paid account is used first and after it is empty the charge is made to postpaid. Business logic for this service is managed by the mediation solution. Another example of balance management service is that the convergent mediation solution uses both pre paid and post paid methods parallel so that e.g. access is charged by postpaid but all or some of the services is charged by pre paid.

As is apparent from the above disclosure the present invention can be applied in a great variety of applications requiring fast and reliable processing of both online data and off line data.

Event event record call detail record usage record transaction or service request are the items of data or data items equivalently processed in convergent mediation. Event is a transaction occurring in a telecommunications network or a service delivery platform for instance. One event may contain all the information needed in e.g. account management or billing. Typically in modern networks where events are generated by all or most of the network elements an event contains only a part of the information needed in e.g. account management or billing. Events are typically caused by actions taken by a subscriber while using telecommunication services. Events may also be based on actions taken by the telecommunication network or equipment connected to it while executing telecommunications services. Some events may be even generated automatically while executing service programs and performing other functions for providing services to the customers.

Off line mediation Off line mediation manages batch and real time data streams and controls data collection storing and processing routines for data items obtained from a communication network or from a service delivery platform. An efficient embodiment of an off line mediation implementation can operate between any two systems that need to communicate with each other but are not directly integrated with one another. In most cases the implementation operates between the communications network producing usage data and the destination OSS BSS systems utilising this information framework such as billing systems fraud management systems and statistical analysis systems.

Online mediation Interactive connectivity between communications network elements or service delivery platforms and Business Support Systems. One transaction in an online mediation environment is for instance a request response message pair. An efficient embodiment of an online mediation implementation can use delivery control functionality and mid session online metering for different control nodes. In an online mediation processing of the data is performed before or during the user session or service usage. The mediation system prepares a response on the basis of the processed data and sends the prepared response to the system providing services to the user. This response is sent during or preferably before the user session or service usage. In other words the term online mediation means that a response to a request is given during or preferably before the requested service is provided.

Convergent mediation A single solution for collecting and processing of usage data and managing service usage and charging for data items obtained from a communication network and or a service delivery platform. The solution supports the processing of usage data in batch real time collection and online transactional modes. Service management and charging are supported online over a transactional interface. Network usage data and service management can be leveraged consistently from all voice and data services for end user with multiple applications including service control rating balance management cost control prepaid billing charging interconnect marketing and service assurance for instance.

Communication network Communication network includes all network elements in access and core networks as well as service delivery systems or platforms which are involved in service delivery for end customer. Access network can be mobile fixed broadband cable network with any technology. Service delivery can be related to any services including voice data video messaging and content services.

The embodiment of described below provides a totally new kind of convergent mediation system that has been especially designed for simultaneous online and off line processing of streams of data items such as event records transactions and service requests. Usage data flows through the mediation solution as individual data items which are passed to billing traffic engineering network planning balance management fraud detection and or other OSS BSS systems. The embodiment of ensures that the OSS BSS systems can be sure that their operations are based on accurate real time information.

The billing system receives event records from the convergent mediation system in an instantly billable form. The convergent mediation system allows various applications like Rating Service Catalog and Policy Control . Billing can be based for example on volume content value QoS Quality of Service or time or any combination of these. This applies also to other applications like rating balance management and cost control. The convergent mediation system enables charging for content and MMS services Multimedia Messaging Service by being capable of transmitting usage data for example from MMSC Multimedia Messaging Service Center content proxies and application servers. It enables also usage based billing of VPNs Virtual Private Network and Internet connections allowing for example charging on the basis of QoS and bandwidth. With aid of Service Catalog function online rating of different and even complex product bundles is possible in the convergent mediation system . Policy Control enables dynamic controlling mechanism in IMS and other broadband services. Typically the Policy Control provides dynamic bandwidth assignments for the data sessions. Another typical use case is access control to certain sites based on subscriber profile. Furthermore together with Service Catalog the convergent mediation system provides powerful Policy Control which empowers operators to design their service offering efficiently.

Online mediation off line mediation and various charging options and other functionalities are processed and controlled by one common platform including all the needed functionalities for processing data.

Real time usage information allows OSS BSS systems to see in real time what services subscribers have used and how the network resources are being used. This information can be analysed to find more competitive tariff structures and reduce customer churn. It can also help in defining end user characteristics and planning how to better serve individual customers. Convergent Mediation applications such as balance management for customers cost and credit control and fraud detection can use the information for controlling service usage.

The convergent mediation system according to the embodiment has been designed to interface with any network element in access and core network and service delivery systems and to serve any OSS BSS system . It can be used for both packet and circuit switched networks by all types including GSM CDMA 3G 4G Universal Mobile Telecommunications System UMTS Wireless Local Area Network WLAN Terrestrial Trunked Radio TETRA IP Multimedia Subsystem IMS Voice over IP VoIP IP group calls Push To Talk PTT content service sessions multiplayer interactive game sessions. Convergent Mediation can be used by any type of operators including Network Operator Service Provider Virtual Network Operator VNO as well as Virtual Network Enablers VNE . It provides numerous off the shelf standard and proprietary interfaces to different OSS BSS systems. The convergent mediation system can handle any type of records generated by different types of network elements . Furthermore the embodiment can handle and process these records despite differences in their structure or delivery method.

Embodiments of the invention relate to a convergent mediation system for online processing and off line processing of data obtained from a communications network and or a service delivery platform .

Generally speaking in one of the general embodiments the convergent mediation system comprises a common platform for both of said online processing and off line processing of data and a system controller adapted to dynamically allocate the processing power of the common platform for the online processing and off line processing of data. When both online and off line processing are performed on a single platform the processing power of the platform may be directed to the use of online processes and off line processes according to the needs defined by the amount of data to be processed. This means also that the same hardware can be used for both of said processing types. As the online processing aims at low latency the online processing capacity should be sized according to the estimated peak load. On the contrary off line processing is not so time critical but should preferably be very efficient in terms of throughput. In the embodiment using a single software platform and common hardware resources it is possible to utilize some of the processing power both for online processing during peak load times and for off line processing during off peak times. Thus there is no more need to dimension the hardware resources according to the peak requirements of both online and off line processes and it is possible to save in investment.

In another of the general embodiments the convergent mediation system comprises a plurality of independent nodes adapted to form processing streams for the online data and off line data. Each of the processing streams comprises at least two independent nodes in sequence and a buffer between each of the sequential nodes . In the embodiment at least one but preferably all of the buffers in the online processing streams are formed by dedicated memory areas in random access memory. This embodiment provides fast processing which is still very fail proof.

In a further general embodiment the convergent mediation system comprises a plurality of independent nodes adapted to form processing streams for the online data and off line data. In this embodiment each of the processing streams comprises at least two nodes in sequence such that the first node in each of the online processing streams is an online interface node which is adapted to receive online data from the communications network and send a response to the communications network . Furthermore the system is adapted to selectively form the content of the response to the communications network in an online processing stream . This embodiment can provide an online stream such that at least part of the processing is performed before the system responds to the network or service delivery platform . A significant advantage provided by such an online stream over a conventional real time mediation is that there is no fraud window left due to the mediation system latency time as the service fulfilment continues only after said delayed response that is given after the response from the online processing stream .

The above general embodiments are independent from each other but can be used all in the same convergent mediation system as well. These general embodiments or any combination thereof can be complimented with one or several further embodiments and system features which are described in the following.

In an embodiment each of the independent nodes comprises a node application and a node base . The node application contains the logical rules according to which the independent node processes the data obtained from the communication network and the node base is adapted to provide basic functionalities for the processing node . The node applications and node bases are typically software components running in a computer system including a host or a plurality of hosts.

In an embodiment the basic functionalities provided by the node base include external interfaces of the processing node and an interface to the node application .

In an embodiment the node bases of all of the independent nodes are identical to each other. This embodiment contributes to a truly one platform architecture as all of the node applications are running on top of identical node bases .

In a corresponding fashion the system can also include a group or groups of processing nodes having also their node applications identical to each other.

According an embodiment the system comprises at least one online processing stream which includes at least three independent nodes in sequence and buffers between each of the sequential nodes such that the buffers are formed by dedicated memory areas in at least one random access memory.

According a further embodiment using an online interface node the system is adapted to perform an access control operation when selectively forming the content of the response to the communications network or the service delivery platform . The selectively formed content of the response is adapted to signify either a positive clearance allowing the communications network to provide a service or a negative clearance preventing the communications network from providing the service. In an embodiment the online interface node is responsive to the received online data to forward it to the next node in one of the online processing streams and wait for a response from the online processing stream before sending the response to the communications network .

The system can also be provided with an off line interface node which is used as the first node in at least one of the off line processing streams . This kind of an off line interface node is adapted to collect off line data from the communications network in the form of event records. Furthermore the system can be provided with combined interface nodes capable of both receiving data and collecting data. Then the combined interface node preferably includes a routine for identifying the type of processing online or off line required by the obtained data in order to select a proper stream to which to forward the data for processing. In an embodiment providing separate nodes for receiving data for online processing and collecting data for off line processing the system s interfaces have already been configured to perform the selection of the processing type on the basis of the route of incoming data.

In an embodiment the system comprises an internode transport layer including the buffers between each of the sequential nodes . Such an internode transport layer can comprise a plurality of buffers which can be sockets shared random access memories and or disk memories. In such embodiments it is preferable that the basic functionalities of the node base includes an interface to the internode transport layer allowing the processing node to read data from at least one of the buffers and write data in at least one of the buffers . Furthermore in an embodiment the node applications and the internode transport layer are independent from each other.

In a further embodiment using the internode transport layer the system is adapted to process an item of data under processing in a processing stream such that the internode transport layer keeps a copy of the item of data in a preceding buffer until a corresponding item of data has been successfully written in a succeeding buffer in the processing stream . Thus the system is adapted to remove any data from the buffer only after successfully performing the processing operation in the succeeding processing node in the processing stream . This prevents data losses due to process failures in the system . This is because the system can in case of a processing node shut down replace the shut down node in the processing stream with a new processing node which starts to process the data in the preceding buffer .

The system has further embodiments also in view of the dynamical allocation of the processing power. In this context the dynamical allocation may occur instantly or may be performed during certain intervals depending on the embodiment used. Such intervals may be during each night once a week or once a month for instance. The system may also be provided with triggers triggering the dynamical allocation or re allocation. The triggered allocation can be done instantly or performed during the next expected off peak time of the system for instance. In a preferred dynamical allocation embodiment the system performs the allocation or re allocation automatically without human intervention under the control of the program components of the system. Embodiments utilizing directions of a human operator are also possible.

In an embodiment with dynamic allocation the allocation is controlled by a system controller which is a computer process run in the mediation system . In an embodiment the functions of the system controller or at least part of them are performed by a Node Manager described in greater detail in context of specific examples part of this document.

In an embodiment the system controller is adapted to prioritize the online processing of data over the off line processing of data when allocating the processing power of the common platform . This provides for the low latency for the online processing .

In a further embodiment the system controller is adapted to monitor a reception rate of the obtained data and use the reception rate as a parameter in the dynamical allocation of the processing power. Such an embodiment can react quickly to sudden changes in the amount of received data.

In an embodiment the system controller is adapted to monitor a processing load caused by the online processing of data and use the processing load as a parameter in the dynamical allocation of the processing power. Such an embodiment can base the allocation decision on the actual processing load caused by the processed data. In a further embodiment the system may also produce estimates of such a processing load as a function of time of day or day of the week and allocate processing power based on such estimates too.

In an embodiment the system has a determined minimum reserve threshold and the system controller is adapted to use the minimum reserve threshold as a parameter in the dynamical allocation. In such an embodiment the system controller allocates more processing power for the online processing of data when the current processing power allocated to the online processing of data exceeds the current processing load caused by the online processing of data by a value less than the minimum reserve threshold. This embodiment helps the system in keeping a sufficient reserve processing power for possible online processing bursts. Further this embodiment can be provided with a determined maximum reserve threshold whereby the system controller is adapted to use the maximum reserve threshold as a parameter in the dynamical allocation such that the system controller allocates less processing power for the online processing of data when the current processing power allocated to the online processing of data exceeds the current processing load caused by the online processing of data by a value greater than the maximum reserve threshold. This embodiment ensures that the reserve processing power for possible online processing bursts is not excessive thus freeing the system resources for other processes e.g. off line processing of data. Indeed in an embodiment the system controller is adapted to allocate as much of the free processing power as is necessary to the off line processing of data wherein the free processing power refers to the processing power of the common platform not allocated to the online processing of data. This embodiment aims at maximizing the throughput of off line data without compromising low latency for online data processing.

In an embodiment the allocation of processing power is done by controlling the number of processing nodes performing online processing and or the number of processing nodes performing off line processing . In another embodiment the allocation of processing power is done by controlling the number of whole online processing streams and or the number of off line processing streams .

In a further embodiment the system controller is adapted to replace a defective node in a processing stream with a properly functioning processing node in case of a processing node malfunction situation. In an embodiment this function is performed by a Node Manager described in greater detail in context of specific examples part of this document.

An embodiment seeks to guarantee high availability of service by providing the system with parallel processing streams and controlling the system such that in case of a malfunction in a processing stream at least one of the parallel processing streams immediately takes the place of the defective processing stream . In an embodiment wherein at least one of the processing streams comprises parallel processing nodes the system is adapted to guarantee high availability of service such that in case of a malfunction of a processing node the parallel processing node immediately takes the place of the defective processing node .

According to embodiments the system comprises also an interface to an OSS BSS system for submitting the processed data to said OSS BSS system . In a further embodiment the interface to the OSS BSS system is a two way interface and the convergent mediation system is responsive to the data received from the OSS BSS system via said two way interface .

After the above discussion of some of the embodiments of our invention on a higher system level we will in the following discuss several specific examples and product embodiments that utilize some or all of the above system level features. Hence the following examples and embodiments can include the above embodiments in any combination and also in itself discloses several other embodiments and features that can be combined with the above described ones.

In the following arguments are presented for the profitability of a solution according to an embodiment of the invention together with presentation of some of the novel features of the embodiment.

Many service providers seek the possibility to introduce prepaid charging for data and voice services utilising their existing billing based systems that is by collection and processing of event records. It should be noted that this type of solution can be seen as a hot billing solution for prepaid charging and it is never online as it always has a fraud window. At the first glance this seems to be the easiest and most cost effective approach but a further analysis reveals several problems 

In brief service convergence means that all subscribers regardless of their payment method are offered the same services. Today most service providers use separate mediation and charging solutions for prepaid and post paid subscribers. This increases operator costs and the time it takes to launch new services. When both subscriber segments are supported by a same convergent mediation solution significant improvements are achieved in time to market for new services. There are technical reasons why there typically are separated environments for prepaid and postpaid subscribers 

Further an embodiment of the invention enables service providers to manage their mediation and charging needs with single solution for both prepaid and postpaid charging. This saves time for service providers when they implement new service configurations or modifications as they are done in one place. Graphical tools that the solution offers also make the configuration of new services easier and faster when everything can be visualised.

According to an embodiment of the invention the convergent mediation system supports cost control with balance management functionality. With the solution service providers are able to avoid postpaid users credit overruns. This is important especially in 3rd party services where the service provider needs to make payments to 3rd party partners according to service usage. Also end users value cost control but from a spending management point of view. With embodiments end users are able to manage their spending for example with service specific balances. The convergent mediation system is based on the concept of pre delivery charging and controlling. This means that a customer s validity can be verified before the service is delivered. Therefore as subscribers are authorised before their service usage there is no revenue leakage.

With embodiments end users are able to manage their spending for example with service specific balances. The solutions are based on the concept of pre delivery charging and controlling. This means that a customer s validity can be verified before the service is delivered. Therefore as subscribers are authorised before their service usage there is no revenue leakage.

The convergent mediation system with rating application provides advanced and flexible rating of any type of service for prepaid and postpaid accounts. Examples include rating of voice data multimedia messaging and content services carrying out product packaging bundles as well as enhancing marketing with promotions and bonuses for these services. Variables such as campaigns subscription types times and day types and specific pricing schemes can be combined in virtually any possible way. In addition specific pricing schemes can be calculated for each combination to reach a high level of sophistication. These advanced and attractive charging models will increase service usage and service revenue for operators and service providers.

Being competitive in the service provider market space requires more than a good service offering. It requires flexible and innovative charging models and careful consideration of customer segment price sensitivity.

Convergent rating with service convergence enables the same services for all subscribers. Service convergence is provided by the convergent mediation functionality bringing together the different services from various types of networks and services. This enables flexible rating rules for all services and linking of subscriber profiles product packages and bundles for competitive charging models.

Currently the common way to handle the rating and account management of prepaid and postpaid subscribers is by running two separate billing systems one for prepaid and one for postpaid billing. In the long run with the requirements for service and payment convergence this causes a huge challenge as the operator has to manage several systems and be able to apply the same billing and charging models for all services and payment types.

An embodiment of the invention overcomes the challenges of convergent charging. Convergent Mediation solution enables operators to make smooth transition from existing separated postpaid and prepaid system environments to fully convergent charging environment.

The convergent mediation system provides reliability and cost savings that are needed in today s billing and charging environments. When all the mediation requirements are managed in a single solution for both prepaid and postpaid subscribers cost savings are clear. With a single solution new mediation and charging rules can be configured in a single place. Embodiments of the present invention are reliable and the convergent mediation system can meet the high availability requirements that are needed in today s telecom environment.

An embodiment of the invention is also very hardware efficient. The solution performance is among the best in convergent mediation world. With the convergent mediation system according to such an embodiment operators and service providers are able to reduce their hardware costs.

An aspect of an embodiment of the invention is that the convergent mediation system closes the fraud window of a hot billing based solution while providing the flexibility and functionality of typical postpaid environment thus adding value to the service provider s investment.

With complex network and business support systems in a multiswitch system type of environment it is beneficial to be able to make cost and performance comparisons between different players. The embodiment enables a vendor independent choice. Operators and service providers need to consider the performance and cost efficiency. Due to these points the convergent mediation solution can be easily updated in a highly complex multi vendor environment. Adding new network element and OSS BSS interfaces is fast which allows rapid and cost efficient launching of new services.

A convergent mediation system according to the embodiment is truly independent from any network element and billing system vendor. The convergent mediation system is capable of processing online and off line data from any communications network or service delivery platform 3G 4G Universal Mobile Telecommunications System UMTS Wireless Local Area Network WLAN Terrestrial Trunked Radio TETRA IP Multimedia Subsystem IMS Voice over IP VoIP IP group calls Push To Talk PTT content service sessions multiplayer interactive game sessions etc. and of delivering it to any Operations or Business Support System regardless of operators or service providers network or OSS BSS vendor.

The convergent mediation system is easily expandable to any new network or service technology that arises. With the support of new and existing technologies the embodiments enable a phased approach for full convergent charging environment.

A convergent mediation system according to the embodiment is extendable from handling a small number of event records up to billions of events per day. Scalability can be reached simply by multiplying mediation processes e.g. balance check analysis aggregation rating within the host. If the processing power of a single host is not sufficient the mediation processes can be distributed to one or more additional hosts in which case the system automatically takes care of transferring the event record data to the host it is next processed in. The hosts are typically UNIX LINUX or suchlike efficient computers. Hosts from different system vendors can be mixed without restrictions.

Prior art batch based processing is very difficult to monitor with large networks. The solution according to the embodiment collects and stores all events and other data related to the mediation processes into a single centralised storage and allows a possibility to send them to e.g. a third party network management system. This allows easy centralised management and monitoring of the system independently of the size of the network.

According to the embodiment the convergent mediation system is highly available and scales up to the needs that even the largest service providers have for mediation and charging systems. The various embodiments of the present invention can be implemented in many kinds of networks and technology environments. When services are available for the subscribers and they are billed and charged accurately also the service provider s image becomes more reliable.

The convergent mediation system according to the embodiment has a functional structure that is based on totally new elements for processing events in an inventive environment. The processes can function independently of each other and the managing system. All data is buffered for any kind of error and system overload situations.

The system is designed so that there is no single point of failure. This means that as long as the host server is running and there is free space in the host s file system or shared memory neither the online data processing nor off line record processing is interrupted.

The convergent mediation system according to the embodiment is a system with online configuration that is available 24 7. It is ready to receive data items such as service requests or records from the network any time. All mediation processes of the convergent mediation system such as data analysis and correlation run independently of each other. Even if one of the processes is affected for example by a network error all the other processes continue running as before. The mediation processes of the convergent mediation system run independently of the process management system. They can function temporarily without system critical resources such as the system database . All data is automatically buffered to ensure that no event records are lost in any kind of error situation.

Users can define freely which processes to include in a convergent mediation process chain . There can be several process chains streams functioning concurrently. Each process is fully configurable making it possible to define accurate rules for usage data handling. The order of the mediation processes is fully configurable and same processes can be multiplied if needed.

The configuration of the process chains can be done without disturbing the ongoing processing and the user can decide when to activate the changes into the configuration. The version control of the configurations allows returning to an earlier working configuration version in case of problems.

Embodiments of the present invention provide online and offline mediation. They also provide an excellent ground for offering a convergent mediation solution for service providers who tackle the challenges of the convergent environment they face today. The present invention is based on two main modules or main streams online mediation stream and off line mediation stream as illustrated in the .

Operators can provide versatile charging models end users can be informed of the actual cost of service purchase and credit losses can be controlled. Chargeable online service can be offered to an unknown client. It is not practically necessary to give credit card number to unreliable party for charging Internet purchases.

The main modules can provide different processes like collection network interfacing validation enrichment filtering aggregation correlation decoding encoding error correction session control authorisation balance operations such as debit credit check reservation and microbalance rating re rating charging recharging usage history recording conversion and distribution. Furthermore an embodiment of the invention can also provide several additional functionalities such as auditing revenue sharing billing data reporting correction and collection pricing testing revenue assurance voucher management and top upping CRM service catalog account balance service subscriber and retention management. The varied functionality allows OSS BSS systems to receive usage data just as they want it.

Also arrangements for managing end user session online charging are presented. In an embodiment of the invention online charging is performed in a system independent online mediation system. It aims to provide a complete set of charging models and capabilities. These are obtained by combining and managing access media and service level charging under a pricing plan mechanism which enables the changing of charging rules within an active charging session.

An embodiment of the present invention makes it possible to construct a reliable convergent mediation system and method with effective control of services and fraud prevention. The inventive concept allows also several useful and advantageous embodiments which provide further advantages.

An embodiment of the invention supports different types of network elements such as MSC IN IN Prepaid content and multimedia servers SMSC MMSC mobile soft switches media gateway controllers routers LDAP servers packet analyzers VAS platforms Radius AAA servers FTP servers GGSN SGSN CG Push To Talk Over Cellular IMS platforms Ducont STARHOME INFO2CELL and In house service delivery platforms protocols such as Diameter Parlay Radius X.25 FTM FTAM SFTP SCP GTP SNMP LFAP DDP LDAP SQL CORBA HTTP HTTPS SS7 and data formats such as XML CSV ASN.1 TAP3 TLV XDR IPDR IAC AMA IACHASTA BCD straight swapped reversed telephony any separator supported variable length blocked structured positional . This means that one event or request may comprise e.g. access bearer service or media requests that are combined together in the convergent mediation system .

Some of the main functions of a convergent mediation solution according to an embodiment of the invention are described below. Each of these functions is configurable.

Convergent Mediation enables the connectivity to different type of networks and business support systems for prepaid charging and postpaid billing. An embodiment of the invention hides the network complexity from the charging point of view and links services subscribers and payment types in an intelligent manner.

From the charging point of view Convergent Mediation provides Online Delivery Control pre delivery charging and controlling meaning that

In addition the convergent mediation system provides online real time and batch mode connectivity for all services and it supports correlation and other typical mediation functionalities for different operation modes. The solution is vendor network and service independent and it enables change management and phase based solution deployment.

In an embodiment all of these features are built in features requiring no additional components to be introduced.

Off line Mediation function hides the complexity of networks from the billing and other BSS systems. It has full mediation capabilities for service providers with any type of network. The solution has flexible and modular architecture with a rich set of tools for system configuration. The tools enable quick and effective reconfiguration of business logic for changing charging of services and creating new services. It enables usage based charging of all services by separating the infrastructure and network architecture. Usage data is instantly billable and the billing can be based on transactions content service quality time volume or any combination of these.

The convergent mediation system includes a rating application designed primarily for rating modern operator services irrelevant of the payment method chosen by the subscriber. The rating function supports a number of rating scenarios from simple call rating to rating subscriber specific services with the usage history on a corporate level.

The convergent mediation system with rating application rates transaction based on both the information in the transaction itself and according to the predefined rules in the rating function.

The convergent mediation system provides balance management application for subscriber subscriber groups or service specific convergent accounts. With balance management service providers can offer the following prepaid and postpaid account functionalities from the charging point of view 

In addition to convergent accounts the balance management includes features for voucher handling and secure handling of monetary value. Therefore with the above mentioned convergent account functionality a service provider can replace the existing expensive and rigid legacy prepaid systems as well as the postpaid accounts in the billing system side.

The convergent account functionality offers service providers tools to offer their subscribers a possibility to pay for different telecom services the way they choose. At the same time it offers both subscribers and the service provider control for customer service usage with competitive charging models.

Convergent account functionality supports several balances per subscriber and it can handle grouping of balances as well as balance hierarchies. Additionally there are notification service features enabling low balance and Advice of Charge AoC type of notifications for the subscribers.

When business rules or business logic for new services are implemented or changed it should impact existing service charging operation as little as possible. In addition configuration should be easy enough to enable fast introduction of new services. The convergent mediation system offers several tools that enable fast and reliable configuration of new business logics and charging rules.

For creating business logic for mediation and charging processes the convergent mediation system offers a graphical tool that helps users to configure business logics in a controlled way. When using the tool the user is able to visualise the business logic which helps ensure that configuration is correct and optimised. The tool also allows the user to modify the business logics later if needed. A mediation and charging process stream typically requires business logic in order to process the event records for billing. Typical business logic includes filtering validation correlation and authorisation conversion rating and mapping functions.

In addition to business logic configuration integration to operator environment is essential part of the service implementation. Integration should be done so that there are minimum changes to existing billing prepaid and network equipment. Business logics are not tied to any particular interfaces so all network elements can share the same logic if required.

An embodiment of the convergent mediation system can provide productised support for over 400 different interfaces for both online and off line protocols.

Once all the integrations and business logic configurations are done it is always essential to test the logics to ensure that they work as planned. The convergent mediation system provides automated testing that is part of the business logic tool. It helps users to prepare test cases execute and compare tests and their results. This process helps operators to verify that the new configuration works and has not had an impact on existing functions.

Another aspect that smoothens the testing phase is Library management. It provides the deployment of pre configured mediation and charging streams for different services and interfaces. This way testing and comparing of existing streams for new services is straightforward. When the operator can reuse existing streams and logics time is saved when testing a new service implementation.

Service request tracking is another aspect that helps operators to debug and analyse their business logic implementations. Tracking helps operators to view graphical step by step request execution trace and analyse in depth analysis for testing and debugging results.

When operating in prepaid mode low latency and high availability are critical factors when measuring the success of service. The convergent mediation system is very focused on these two items. High availability is ensured by an N M configuration where N represents the number of nodes processing transactions and M the number of standby nodes in case of any of the active nodes goes down. In addition to node configuration all interfaces can be duplicated to ensure that no transactions or events are lost.

Scalability is another aspect that the convergent mediation system addresses. The system has been designed for online applications while maintaining extremely high throughput for off line events . The requirements for system performance include low latency and extremely high tolerance for parallel transactions. Together these two features ensure that the end user s Quality of Service QoS is not compromised and the system is able to serve masses of subscribers with sensible hardware even when the external systems might be slow.

Low latency is required in request response type streams for example when a user is waiting for authentication. The convergent mediation system achieves very low latencies by using shared memory transport mechanism between the processing nodes . The shared memory transport mechanism makes it possible to build large streams where the processing has been logically divided into the nodes and still simultaneously achieve high throughput by using the scalability features of the system .

According to an embodiment of the invention the convergent mediation system capabilities do not stop at running of the system. The system also provides reports on how services have been used and how accurate billing and charging are. This helps to analyse for example what were the popular services and when were they used. The reports can then be used to plan next service offering and how their charging will be done.

When a new subscription service package or charging model is created the customer care system normally sends an activation request to the management application programming interface API of Convergent Mediation Solution.

Embodiments store the charging rule data to the configuration database and further enable the charging rule provisioning towards control nodes in the network if necessary.

The convergent mediation system management API is an open interface to all applications that must have access to subscription hierarchies and balance information. The management API supports for example the following request types 

All subscription and balance management functions provided by the management API are also available via the user interface. However when using the UI to perform subscription or balance operations it is important to configure the convergent mediation system so that it sends the event records or notifications to external systems in a manner that ensures that systems such as the billing system or CRM database are maintained synchronised with the convergent mediation system.

An embodiment of the invention recognizes the incoming data whether it needs online or off line processing.

The convergent mediation system according to the embodiment is capable of interfacing with any network or service e.g. 3G 4G Universal Mobile Telecommunications System UMTS Wireless Local Area Network WLAN Terrestrial Trunked Radio TETRA IP Multimedia Subsystem IMS Voice over IP VoIP IP group calls Push To Talk PTT content service sessions multiplayer interactive game sessions or any combination of presented network technologies.

When receiving event records from the network the mediation solution checks them for duplicates and verifies their sequence. By doing this it ensures that the numerous event records stream into the system in correct order and that none of them are missing or delayed or tries to enter the system for the second time.

After collection the mediation solution carefully examines and analyses the contents of the event records. It checks that all values included in the event record fields are applicable and in a correct format. It can join fields and insert additional values to them when necessary.

The mediation solution according to the embodiment is able to enrich event records by completing them with information from external sources. It can for example fetch the information on which customer category a specified service user belongs to and add this information to the event record. Marking of customer category helps other processes such as billing.

In aggregation the mediation solution according to the embodiment merges partial event records produced by a single service usage and coming from the same network source. Aggregation thus allows the OSS BSS systems to receive only one billable record from each service usage.

Correlation involves combining event records also but the records to be correlated come from different sources. A GPRS session for example produces S CDRs Call Detail Record in SGSN and G CDRs in GGSN that the mediation solution is able to correlate into one output record.

The records to be correlated may come at the same time from access network and content platform which is the case in a content usage session. The mediation solution then completes the event records from content platform with the user identification fetched from access network. The correlated records contain all the information needed for content charging who the user was what services he used and for how long as well as the value of the services.

The rating functionality of the mediation solution according to the embodiment allows pricing of event records in the mediation system. Flexible rating criteria and various pricing models can be used as rating bases. Also subscriber specific rating is possible. The rated event records can be sent directly from the mediation solution to balance management and other applications without any intervention from billing system.

All records of the mediation solution according to the embodiment can be stored into a long term event database. The event records can be stored into the database during different mediation processes for example before and after aggregation correlation or rating.

The long term storage capability allows to view and fetch records from the database at all times and check how different mediation processes have modified them. The stored event data gives valuable information about subscribers network usage in the long run.

Before delivering the fully processed event records to the OSS BSS systems the mediation solution according to the embodiment converts them to formats compatible with these systems. The mediation solution is able to convert the records either to a standard format or to operators proprietary formats. Due to conversion an OSS BSS system receives all usage information from the network in a uniform predefined form. It should be noticed that the formatting of event records may be done also in any point or points through the processing chain stream of the mediation process.

The mediation solution according to the embodiment is able to simultaneously interface with multiple different OSS BSS systems. Even if it performs all its collection and other processes in real time it is able to deliver the processed records to the OSS BSS systems either through a configured real time protocol or a file interface.

The keywords of the convergent mediation system architecture are simplicity and straightforwardness. The truly one platform ideology and modular design of the solution according to an embodiment of the invention enables real time and distributable processes reliable operation low latency and high performance for both online processing and off line processing of data.

The convergent mediation system according to the embodiment includes mediation processes managers controlling the processes system database and web based user interface . Mediation processes such as balance check cost control collection analysis pre delivery control duplicate checking aggregation correlation and conversion are linked together to construct processing streams . Streams are fully customisable and there can be multiple streams simultaneously active.

According to the embodiment all processes are controlled by process managers which start up monitor stop and configure them when so instructed. This is presented in . Managers give configurations to the processes during start up. Once started the processes can function independently from the manager also in case the manager is temporarily unavailable.

The present architecture is an always on architecture wherein in the best case all the processes are doing work simultaneously.

Nodes are functional components specialised in different mediation processes such as balance check cost control collection aggregation pre delivery control validation correlation and formatting or a combination of these. Nodes are linked together to form processing streams for handling data items such as event records and service requests. Each stream both online mediation stream and off line mediation stream is fully configurable through the web user interface of the mediation solution according to the embodiment. presents the nodes and their interaction in the system in more detail. A node comprises its basic functionality in a node base which is used for transferring data between the nodes in system s internal format. In addition the node comprises a node application that performs the actual usage data processing.

Nodes run independently of each other. This means that even if one of them is temporarily unavailable the other nodes continue as before. This in addition to their independence from the manager adds to the reliability of the system. Also any data that cannot be transferred from one node to another due to for example a network failure is buffered . Buffers are file socket or memory based solutions. In a typical embodiment of the invention the online processing streams comprise memory based buffers due to the nature of online processing that requires very fast action. On the contrary the typical off line processing streams use file or socket based buffers .

While nodes take care of the actual processing of the events Node Manager makes sure they function in a controlled way . Node Manager configures the nodes into correct processing order starts them up monitors and stops them when so ordered. Before starting up a new node Node Manager retrieves its configuration information from the system database and configures the node . Since the node itself contains the configuration it is able to function properly even if Node Manager and system database are temporarily unavailable.

System database stores node configuration audit trail information as well as status information of nodes streams and Node Managers . Also orders for Node Managers are stored within the system database .

The convergent mediation system provides mediation and charging functionality for all voice and data services for both prepaid and postpaid subscribers with one single solution. The solution is connected to network over both online and file based interfaces irrespective of the technology used. It supports Diameter and IP interfaces and also SS7 based signalling interfaces. Correlation duplicate checking and other typical mediation functionalities are also available in the online charging side. When same modules are used for all aspects of the solution roll out of services is smoother. For voice control an embodiment of the invention can provide voice SCP if so required as part of Convergent Mediation Solution fulfilling a truly convergent mediation solution.

Another use case example for the convergent mediation system is Online Cost Control. It provides a prepaid like ability for postpaid subscribers to control their spenditure in telecom services. When there is control of usage also for postpaid users subscribers manage their spending and service providers can ensure the credit worthiness of their subscribers. Different limits can be subscriber specific and they are easy to control and manage with the tools that the solution provides.

The solution enables operators and service providers to offer new and innovative service concepts like family and business concepts. For example parents can control how much their children spend on telecom services while still paying their monthly bills as usual.

A third example of the convergent mediation system is IP prepaid. In IP prepaid all prepaid functionalities that are typically managed by IN switches are provided in an all IP environment that is based on the convergent mediation system. The solution has a convergent mediation layer that hides the different network technologies and environments from the rating and account functionalities. Then convergent rating and balance management functionalities provide all rating features that are needed in today s and tomorrow s rating requirements. Balance management holds the subscribers accounts which they can top up by using an existing top up mechanism. This way operators and service providers can extend their existing investment from their top up mechanisms while extending the rating functionality that they have.

According to an embodiment of the invention the subscription based functions contain at least following aspects. Multiple MSISDNs are associated with a single subscription. Further single subscription may access 0 . . . n services in 0 . . . n service domains. System supports activation of services provisioning to both all subscribers and to individual subscribers based on some predefined criteria. The system supports even removing of active services from subscriber s access both from all subscribers and individual subscribers based on some predefined criteria.

Another embodiment of the invention supports also following rating and charging related functions. System supports rating and charging based on time destination location volume bandwidth access technology quality or used value added service. System also supports sending information about chargeable events to operator accounting billing system. Examples of these are 

Furthermore the system supports flexible billing system that enables use of stored value cards credit cards or other similar devices. System supports indication of the price cost of the service. An example is Advise of Charge. Subscriber is able to make decision of acceptable charge either dynamically or based on personal profile settings. System supports rating and charging of subscriber that receives service event or call. Subscriber is able to accept the service dynamically or based on personal profile.

According to an embodiment of the invention the system supports off line rating and charging. This is typically collecting CDR files from the network elements. Further the system supports online rating and charging. This is typically subscriber authorization real time charging and control of network resource usage. Even more the system supports event based stateless charging functionality such as MMS message sending WAP page retrieval etc. The system supports also session based stateful charging functionality such as GPRS usage.

IMS enables rich conversational multimedia services delivered on a standard network infrastructure. In IMS all network usage data is by default available in real time. To charge effectively for IMS the access bearer network data has to be collected and possibly correlated with IMS usage data.

Convergent Mediation Solution offers an easy choice for charging of IMS services by off the shelf interfaces and highly configurable processing logic. Convergent Mediation implements both offline and online charging functions as specified by 3GPP. Implementation of new business logics with Convergent Mediation Solution as new services are rolled out offers the operator an ease on the service launch project for time and cost to support the billing of the service.

In this example a video sharing service is charged by collecting bearer data from GPRS network elements and service and session data from IMS network elements. It is assumed that an operator bills subscribers monthly for 3G service usage. The invoicing of the subscriber is handled by the billing system which receives all usage data from Convergent Mediation Solution . The underlying network architecture can serve both fixed line and mobile subscribers as IMS can offer services to both types of access networks

Convergent Mediation Solution hides the technical implementation of charging from the billing system by interfacing the network 

This means the identification of the GPRS tickets belonging to the same PDP context and forming a single billable item for the billing cycle. Typically total bytes in and out and duration of the connection are summed together.

Reprocessing of records is very common in the mobile mediation due to usage of lookup tables in the identification of the subscriber group or other details. As lookup tables might not always be synchronised with the information in the billing system the records where the subscriber was not identified are rejected. After the lookup table update the subscriber group is found and records are released to billing. Convergent Mediation solution also provides a record correction facility for more complex correction and reprocessing scenarios.

In the example above the use case was based on collection. Similar type of functionality can be based also for online processing. In such scenario the service usage is authorised before the actual usage takes place. Authorisation can include prepaid balance check and subscription validity for the used services.

In addition to charging functionality Convergent Mediation Solution enables Policy Control for IMS and broadband services. Charging and policy control functionalities are closely tied together and the solution leverages the same platform for both and thus keeps the total cost of ownership low.

The most logical way to charge an ISP or a corporate user for the usage of broadband or VPN service is to bill based on consumption of bandwidth. However without proper automation tracking down and calculating the usage of a VPN or broadband service is complicated and time consuming task.

An automated usage based billing of broadband or VPN services gives additional revenue as well as unifies the billing process of the operator. This is realised by taking advantage of the flexible and extensive network interfacing and data processing capabilities of Convergent Mediation Solution.

In providing information for the rating process Convergent Mediation Solution is able to provide details of for example bandwidth usage type of service volume of traffic and amount of connections. Because of this it enables the rating process to apply several different types of discounting options that can be applied for each type of service as well as for the total provided service in addition to any Service Level Agreement SLA discounting options.

In this example the operator needs to bill a subscriber for the usage of an international VPN connection. The network is based on IP and the VPN is based on MPLS. The operator expects to send a monthly bill via a corporate Customer Financial Management system.

Direct charging of the customer based on its usage of the network either by total volumes used or through the 95 percentile calculation method.

The service is charged based on a flat fee but the flat fee has a limit to usage. For example 3000 per month per 10 Mb s connection plus all usage exceeding total usage limit is charged based on price of 1 GB.

Convergent Mediation Solution receives usage records from routers of the VPN or broadband service and takes care of the following tasks 

Convergent Mediation Solution can be distributed so that the collection and aggregation functions are near the edge routers and a centralised processing server is located at a data centre. Distribution might be required since routers produce a wealth of information and the amount of data should be minimised close to network before sending it to the data centre.

According to an embodiment of the invention an overview diagram in shows a high level view of the different charging online and off line functions as described in the following.

The convergent mediation system provides all the functions of the online and offline charging systems as well as functions to communicate between the different charging systems mainly by generating records in the OCS that will be processed by the offline charging system .

The Charging Trigger Function CTF generates charging events based on network resource usage concurrently with the resource usage. The different network resources can be anything from network bearer level resources such as GPRS and PS gateways switches CN Domain MMS and WAP gateways Service Elements or for example IMS resources Subsystem .

The difference between the online and off line Charging Trigger Function is that the off line charging mechanism does not effect the service usage in real time. In online charging the mechanism has to provide functions to control the network resource usage in real time.

Depending on the network resources that are generating the charging events the information sent and the protocols that are used may differ between online and off line charging functions. However the following information may flow between the both charging systems and network resources that generate the charging events 

The Charging Data Function CDF creates Charging Data Records CDR based on the charging events received from the Charging Trigger Function . The CDRs may be generated based on following conditions 

The resulting CDRs are in a well defined content and format. The content and format of the CDRs depends upon the domain service or subsystem in question.

The Charging Gateway Function CGF receives the CDRs generated by one or more Charging Data Function s. The Charging Gateway Function acts as a gateway between the network and the Billing Domain. Following list contains the main functions of the Charging Gateway Function 

The interaction between the Charging Gateway Function and Billing Domain is based on passing CDR files from system to another. A common standard secure file transfer protocol e.g. SFTP is used including the transport specified for the selected protocol.

If the Charging Data Function and the Charging Gateway Function are not integrated or are separate implementations then the transport of CDRs between the functions are implemented by using e.g. the GTP protocol.

If the functions are integrated then it is possible to use some other proprietary protocol for communications between the functions.

According to an embodiment of the invention whether or not the Charging Data Function and Charging Gateway Function are integrated the CDRs are passed between them in near real time as soon as they have been closed by the Charging Data Function .

Once the CDRs have been received by the Charging Gateway Function they undergo a semantic or syntactical analysis and based on the analysis the Charging Gateway Function executes any of the following operations 

According to an embodiment of the invention Charging Gateway Function routes CDRs to different files that are kept open concurrently. The routing of the CDRs to different files can be based on different routing filters and those CDRs that don t match any routing filter are placed e.g. in the default CDR file that collects all non matching CDRs.

The routing of CDRs is based on CDR parameter information or the origin of the CDR. The file name contains indication of the used routing filter if possible.

According to an embodiment of the invention Charging Gateway Function implementation supports routing based on 

When CDR file is closed the next matching CDR is written to new CDR file that is next in the chain . The exact time when the new CDR file is generated physically may be any time between 

If there are no matching CDRs between the closure of the previous CDR file and configured file closure trigger time then an empty CDR file is generated. After CDR file closing the file is immediately ready for transfer to the Billing Domain .

The file transport between Charging Gateway Function and the Billing Domain is implemented with two different mechanisms 

Basic File Transport Mechanism is supported by all CGF implementations and complies with following requirements 

File Transfer IRP can be used optionally. If File Transfer IRP is used it may comply with 3GPP TS 32.341 3GPP TS 32.342 3GPP TS 32.343 and 3GPP TS 32.344 for instance.

According to an embodiment of the invention files are transferred to Billing Domain in push or pull modes or by using both modes at the same time.

In push mode the CDR files from Charging Gateway Function are written to the defined Billing Domain file store at time frequency controlled by the Charging Gateway Function . If the Charging Gateway generates concurrent CDR files based on some routing filters then it can send different files to different Billing Domains .

If the file transfer fails the Charging Gateway Function logs the event and raises an appropriate alarm.

In pull mode transfer the Billing Domain reads the CDR files from the Charging Gateway Function directories. The time interval of the file transfer is controlled by the Billing Domain . The Billing Domain requests files from the Charging Gateway Function at any given time or frequency. If the file transfer fails then any further actions are up to the Billing Domain . In this case the Charging Gateway Function also logs the event and raises appropriate alarms.

The CDR file format follows the principles standards described in the Charging Data Record CDR file format and transfer specification.

The Online Charging Function OCF consists of two distinct functions Session Based Charging Function SBCF and Event Based Charging Function EBCF .

The Session Based Charging Function is responsible for charging of network user session. For example voice calls GPRS PDP contexts or IMS sessions.

The Event Based Charging Function is responsible for event or content charging such as ring tone or logo downloads or other Value Added Service usage.

According to an embodiment of the invention the Rating Function RF determines the value of the network resource usage. Online Charging Function passes the charging event in a form recognized by the Rating Function and receives in return the rating output monetary or non monetary units . The Rating Function may handle wide variety of rateable services events etc.

The class A rating function is stateless and class B and C are statefull. This means that the class B and C rating functions can do the value reservation of counters and accounts.

The class C rating function supports a mechanism for account balance management function towards external account management servers.

Depending on the class of the rating function it supports the following function before and or after service consumption 

The Account Balance Management Function is the location of the subscriber s account balance within the online mediation system .

In addition to basic Online Charging Functions described above the online mediation system generates charging events to off line mediation system and act as Charging Trigger Function for the system. The online mediation system also includes Charging Gateway Function as described above and generates CDR files for the Billing or Mediation Systems in the Billing Domain .

The purpose of off line charging is to transform the charging information collected during the network resource usage to CDRs that are then further processed to the final billing information off line as in after the network resource usage has finished. The off line charging does not impact the network resource usage in any way.

In off line charging the charging event is processed as described above. Even though there are no real time requirements for any parts of the procedure the system should be capable of completing the whole process from detection of chargeable event up to transferring of the CDR to Billing Domain in near real time.

In off line charging the session based charging is done by collecting the initial interim and end charging requests by the Charging Data Function which then upon completion of the network resource usage passes the corresponding CDR s forward to Charging Gateway Function . The system should complete the processing of the chargeable event as close to real time as possible.

The purpose of online charging is to perform credit control before the network usage is permitted. For this reason the prepaid subscriber account has to exist in the online mediation system or external system so that the network usage can be billed before or during the network resource usage. All activities that are needed to assess the requested resource usage in monetary or other units and to debit these units from subscriber account must occur prior or during the resource usage. Depending on the situation the charging can be done in two different ways 

For online charging the event based charging must occur in real time. Depending on the implementation of the service the charging may occur immediately or by reserving an amount of units from subscriber account and then debiting returning the units after successful failed delivery of service.

In both cases the authorization of the charging event has to occur before delivering the service. The authorization may contain authorization for one or more chargeable event at a time.

In online charging the session based charging always involves reservation of units from the subscriber s account after successful authorization of the initial charging event. During the network resource usage the Network Element is responsible of supervising the reserved unit quota usage and of requesting additional interim charging events from the online mediation system when needed or terminating the session. Once the session is terminated the Network Element reports the actual quota usage to the online mediation system and the used unused quota units are debited returned from to the subscriber account.

The whole procedure of receiving and responding to a session based charging event must occur in real time. It also has to be noticed that one subscriber may have several concurrent services running on one user session at any given time.

Service identification is a function identifying the service s which the request e.g. CDR represents. Identification is based on the parameters i.e. fields values of the request.

Service identification is based on predefined identification rules. The rules are logical expressions referring to one or several parameters. The rule can define identification values by fixed or dynamic values. Dynamic values can be a relation of two parameters or an external value e.g. from database. All value types can be used in the same identification rule. The final identification value can be formed from several values by an arithmetic statement.

The result of service identification must be unambiguously one service identifier true or unsuccessful identification false . If the request represents more than one service the identifier is the service group product identifier which may include a list of detailed services of the request.

In situations when several Network Elements generate charging events that are for the same event session correlation has to occur either in the Online Charging System or the Billing Domain. For example IMS correlation functions are following 

When granting separate quotas it may be possible that the user s credit may be totally reserved when starting to use new services. The new service usage may then be denied even though the user still has credit left but reserved to other services . To avoid this kind of fragmentation of credit it is possible to create a pool of quota credit from which all services draw quota. The credit pool also holds service specific rating information so that it can define the amount of pooled quota credit versus requested quota credit. This can be done e.g. with Diameter or similar protocol.

The advice of charge functionality is designed to supply to mobile user information to allow real time estimate to be made about the amount charged from the user. The advice of charge functionality can be used for example to following services 

The embodiments mentioned above have also several common technological issues such as connectivity platform functionality scalability high availability and so on. The system supports both circuit and packet based protocols build on top of SS7 TCP UDP and SCTP. There is also an easily extendable protocol framework that can be used to implement different service protocol adapters parsers. Further the system supports file based protocols. Depending on the protocol the system supports reading single line multiline and structured records as well as single or multiple records from single file. According to an embodiment of the invention service protocols and I O network file protocol implementations are separated. In such an embodiment it is possible to use same service protocol implementation with different I O protocol implementations.

According to an embodiment of the invention the platform functionality of the system provide APIs Application Program Interface and tools for building deploying configuring testing and running node applications . Furthermore the system provides APIs for communication between node applications logging browsing and management of log files monitoring and for viewing monitoring information and collecting and displaying statistics. Further the system supports running node applications on different modes such as standalone parallel backup primary setups distributed to different hosts. Also the system supports task scheduling and Timer functions both on single node and on multiple replicated nodes . According to an embodiment of the invention the system provides APIs for sending alarms and notifications.

According to an embodiment of the invention the horizontal scalability is gained with the aid of deploying processing on 1 . . . n servers. Furthermore the system supports scalability by increasing the number of CPUs. The system supports also vertical scalability over 1 . . . n servers.

According to an embodiment of the invention the system supports hot node application updates without system restart. This is useful when e.g. updating node application to new version. The system supports also rollbacks for business logic changes runtime configurations and library updates. The system supports distributed session data management i.e. online data storage functionality. Furthermore the system supports fast recovery on error situations. For example automatic restarting of services when an error has occurred. The system supports a fail safe operation mode which is able to shutdown all unnecessary services and process only mission critical services. According to an embodiment of the invention the system supports failover between nodes without loss of transactions. The system supports load balancer communication and automatic failover and node start up and shutdown.

Following chapters describe in more detail what different functions a truly convergent mediation platform according to an embodiment provides to enable the implementation of the convergent charging functions as described earlier. The concept truly convergent mediation platform refers to a system that has a single platform for both online and off line mediation.

The truly convergent mediation platform is divided into two main subsystems the Management System used to manage and configure different Platform Application and Resource specific functions and the Transaction System that is used to execute the Application logic. According to the embodiment the convergent mediation system may include several Transaction Systems running different or duplicated parallel sets of Platform Applications and Resources. Different Transaction System can be either chained one after another to form an Offline Charging stream or form a request response type Business Logic Flow as required in Online Charging.

The Management System is divided into different sub views according to different sub systems that are being managed User Management Server Platform Management Application Management and Resource Management . On top of the management functions the Management System provides views for monitoring system functions reporting and audit trail functions .

Management System is the single entry point for all installed Platform Applications. It contains views for all common services functionalities and possibilities to add Application or Resource specific views to the system. According to an embodiment of the invention the Management System is one example and implementation of a user interface of the convergent mediation system . With the user interface an administrator can administrate simultaneously both online and off line processing of data. Therefore it is possible to configure and manage both online and off line streams by means of a user interface . It is also possible to define business logics and rating rules for both of the processing types by a single operation or series of operations affecting both the online nodes and off line processing nodes.

Through Application Management view user is able to do all Application management operations that are common to all Applications . These operations include 

Resource Management view is used to configure and deploy Resources that can be used by any Platform Application that has been deployed to the same Application Server with the Resource . It is able to do following actions through the Resource Management view 

Server Management view is used to update and configure the Application Server specific information. It is able to do following actions through the Server Management view 

The User Management view is used to update and configure User preferences and Application specific permissions.

The Deployment view consists of both physical and logical view of the different types of deployable components. For example it should be possible to view that on what physical hosts Application Servers have been deployed and what different Resources and Applications are parts of some defined Service Business Logic Stream.

The Monitoring view is used to access monitoring information of different Application Servers Applications and Resources . The view is used to configure different actions operations that can be executed after some defined monitored levels have been reached. It shall be possible to do following actions through the Monitoring view 

The Reporting view is used to view transaction event statistics and to create reports from the statistics data that is collected from the different Applications .

The Audit Trail view is used to view information about the management operations that are done to the convergent mediation platform Application Servers and Applications by different users.

Transaction System is the part of the convergent mediation platform that is responsible for different functionalities that are required to deploy and run the defined Applications and Resources . Transaction System may be separated as many different processes depending on the functionalities that are required. For example the Server Manager and Application Server may be two separate processes if required. According to an embodiment of the invention the Transaction System is one example and implementation of a combination of nodes and system manager of the convergent mediation system .

The Application Server is the component that loads the different Resources and Applications based on the configuration. The Application Server is responsible for providing the services that are required for running the Application and Resources . The Application Server also enables introducing deploying Application or Resource specific external in house libraries and parameter files that are required during the execution of the component. According to an embodiment of the invention the Application Server is one example and implementation of a node base functionality of the convergent mediation system .

Applications are the components that contain the application specific implementations of business execution logic. The Application may be an implementation of a big and complex function such as Rating or Account Balance Management or it may be an implementation of a simple Charging Data Function that collects data from Network Element and writes CDR files to the disk. The Application implementations can be for example Service Identification Credit Control Rating Correlation Authorization Validation Aggregation Formatting etc.

Resources are implementations of non application specific functionalities that can be used by any Application at any given time. The Resource implementations can be for example Database Connection Pools Queues Interface implementations Collectors Distributors etc.

Some Resources may have restrictions in the way they are used or whether they can be accessed by one or many simultaneous Applications at a time. It is the Application Servers responsibility to verify that the configuration being deployed is valid. According to an embodiment of the invention a combination of Applications and Resources is one example and implementation of a node application of the convergent mediation system .

Common Services is the set of APIs or services that implement the functionalities that are common to all Applications and Resource implementations. Depending on the service the service may be initiated from the Application or Resource side or the Application Server may initiate service information request towards the Applications and Resources .

Scheduler service is required to execute operations between pre defined intervals or in pre defined times. The Scheduler service is able to function correctly no duplicate operations no missed operation in a distributed environment and in situations when a failover has occurred and service requests have been re routed to another Application instance due to a failure in the primary Application Application Server or host.

Timer is a local service for executing operations between pre defined intervals or in pre defined times. Timer is typically used for operations that are not supposed to be persistent or distributed.

The Statistics service is used to collect statistics data from the deployed Applications and Resources as well as from the Application Server itself. The statistics data can be collected by an external tool such as the Management System or the data can be stored and forwarded to external statistics repository for reporting and analysis purposes.

The Configuration service is used to load Application Server Application and Resource specific configuration information from the configuration repository during the Application Server Application or Resource startup. The Configuration service also supports runtime configuration changes and notification of the changes to the interested components.

The Data Storage service is used to access the data repositories that have been configured to the Application Server . Notice that the access to the repositories is done by using shared Connection Pool Resources to avoid overloading the data repository connections connection count.

The Data Storage service implementation is database vendor or file system independent to enable more flexible solution.

The Logging service is used by all sub systems and components of the Convergent mediation platform . The Logging service provides runtime configurability of the logging levels to all Applications and Resources separately so that you can configure different logging levels to each deployed component if necessary.

The Error Handling service is used to unify the error processing and reporting mechanisms used in different components. The service enables reporting indications of error situations to monitoring and alarm systems if required.

The Error Handling service is also used to publish introduce the troubleshooting information to the Management System Troubleshooting view.

The Auditing Service is used to record information about management operations that have been done to change systems state and or configuration. The audit records are collected and stored in the audit repository for a defined time period to enable both troubleshooting and possible security checks.

The Connectivity services are used by different Resource implementations that provide either file or network I O based communications between Applications or between Applications and Network Elements or Business Support Systems . The Connectivity service is split to functional layers that can work independently of each other 

The I O layer and Protocol layer implementation can be bound together based on the service configuration. It is also possible to add and remove I O and or Protocol implementations when services are running.

The Alarm service is used to send alarms or runtime notifications to systems that have been configured to receive them.

The Notification service can be considered as a subset of Alarm service and as such does not provide any additional functionality.

This functionality should not be confused with the notifications that are sent to the users for example from the Account Balance Management Function when the balance of the account has gone under some pre defined threshold.

The Authorization service is used to ensure that user executing the operations has sufficient privileges to do so. The level of Authorization depends upon the security requirements of the Application .

The Transaction services provide tools for creating transaction information and provide means to define transaction boundaries. The transaction management functionalities in this context are not as comprehensive as is for example in the database applications and provide tools only for creating unique transaction ids and for creating start interim and end timestamp information for the transaction.

The Transaction service also provides statistics data that can be collected by the Statistics services if when required.

The Monitoring service provides the runtime interface for accessing the Application Server Application and Resource monitoring information that has been made available by the implementations. The Monitoring service provides tools and interfaces for 

The Heartbeat service is used retrieve information about the Application Server and the Application status. The information can be used to initiate failover switchover during planned downtime update or an Application Server Application or Resource failure.

The Runtime Management service provides access to the management operations that are exposed by the implementations. The operations can be executed through the Management System or they can be accessed using a standalone command line tool s . The operations that can be managed through the Runtime Management are 

The Messaging service is used by different Resources and Application when communicating within the same Application Server . The service enables finding and routing of the messages between the different components.

The Server Manager provides services for updating and managing the Application Server instance that it manages. The manager can be used to deploy new libraries to the Application Server and to initiate failover if required.

The Deployment service is used when uploading new Resource or Application library versions to the Application Server . The loading of the libraries is done by the Application Server based on the defined configuration but the physical deployment and storage of the libraries to the disk is done by the Server Manager .

The Management service is used to start and stop the Application Server remotely if required. The Management services can also be used to view and update the Application Server s local configuration and log files.

The Failover service is used to either initiate failover functions on the local host or to acknowledge the other configured host in the configured failover cluster that this managed Application Server is unable to continue service and that the backup host s have to initialize required failover functions locally.

The Update service is used when updating patching either the Application Server libraries or the Server Manager s libraries. The purpose of the Update service is to provide all the required functions that are needed so that all system update operations can be done remotely from the Management System .

Management Interfaces are the interfaces that can be accessed either from the Management System or the local command line management tool. Depending on the security requirements of the system the Management Interfaces may require authentication before they can be accessed. The authentication is done using the same service as in the Management System .

Examples of Distributing Services Resources and Applications According to an Embodiment of the Invention

In order to flexibly implement different convergent mediation services the system supports different kinds of Application and or Service distribution schemes. In this context a service is for example a GPRS charging service that includes different convergent charging applications such as Service Identification Credit Control and Rating. An Application is a standalone implementation of some convergent charging function as mentioned above.

A standalone application is for example an installation that consists of one Application Application running in one Application Server instance. Simplest type of Application would not even require any Resources and would only provide functionality that can be used through the Management Interfaces . presents an example of Service X that is implemented with one Resource Resource A that provides the connection between the Network Element NE and the Application Application . This could represent a simple Collection Application that just writes the collected data to disk for backup or further processing.

The Application Server is able to run multiple different Application instances that may use same resources such as database connection pools etc. It is also able to run Applications that require services from Applications that are running on the same Application Server .

According to an embodiment of the invention the High Availability issue is addressed on many levels of the business logic execution environment. presents different layers that contribute to the overall availability of the system according to the embodiment. Different aspects of High availability are hardware availability hardware clustering and failover data storage availability network availability Application availability and Service availability . In this context the Service availability is the key issue and the goal is to make Services available up to 99.999 of the time.

The Service Availability can be thought from the end user point of view for example so that when making a call the call can be made even if the charging of the call is not done online because of some business support system failure. So the service is up and running even though some parts of the whole rating and or billing chain or business logic are not functioning. The level of Service Availability and the strategies how to cope with different error situations depend on what the situation is. The customer must be able to configure the system so that they can guarantee the agreed level of service availability in all situations.

The convergent mediation platform is able to implement convergent charging applications that allow the system to function during planned or unplanned network hardware and software downtimes in a well designed and predictable manner.

It is also possible to prioritize the services and or parts of the system that are even more highly available. For example the system may be configured such that in case of failure database corruption hardware failure . . . or disaster earthquake flood . . . all emergency selected authority police army . . . calls are connected in all situations and all other non emergency calls and services are dropped.

The distribution of the convergent charging applications and logical functions also contribute to High Availability. highlight the ideas and effects of different availability issues as an example. As described in the service availability can be increased by adding distributed Application Servers preferably on dedicated hosts and by introducing a load balancing or failover mechanism to Network Element that can automatically re route the request from AS to AS in case of failure.

Failover is the term used about the situation when the Network Element or load balancer detects that a primary server or application is not available and re routes the service requests to a secondary server.

The failover time depends on the High Availability configuration of the system and or how long it takes for the secondary server to be able to service the requests send from the Network Element.

Recovery time is closely related to high availability. Recovery time is the total time required for a planned outage or the time required to fully recover from an unplanned outage.

The convergent mediation platform enables implementation of Convergent Charging Application that can minimize the expected recovery time by cutting down the amount dependencies to systems such as database for example.

The Convergent mediation platform enables implementation of such Convergent Charging Applications that minimize the amount of lost data in case of failure in the network hardware or the software components. The Convergent mediation platform provides tools for maximizing the data availability when needed.

It should be noted that the data availability and the service availability from end users perspective are different issues. Maximum data availability of an Application e.g minimizing the amount of lost data in all cases may also be ensured in the expense of service availability if so required.

The system configuration is stored and maintained in the System Database . There is one Node Manager installed in each host and started as an independent process. The configurations are changed and the system managed via the User Interface .

Upon the system start up Node Managers read the Processing Chain configurations from the system database and start up the Processing Chains. A Processing Chain includes a plurality of Nodes . Each of the system components executes independently once started. The Processing Chains process the data until they are shut down. The Node Manager shuts down the Processing Chains or Nodes upon user s request.

The usage data flows between the Nodes in internal data files or other data format used in disk based socket based or shared memory transport. When using disk based buffers each Node checks its input data sources constantly for new data files. When a new data file is detected it is immediately processed and delivered to the output destinations. Usage data is processed file by file. When an input file is processed and the possible corresponding output data file is created the input file is removed. This way no data is lost if a Node crashes during data processing. Each Node locks the input file it is reading. This way no other Node can erroneously read the same file. A corresponding mechanism is used in shared memory and socket based buffers.

At a crash recovery the Node will start writing to the beginning of the existing temporary data buffer. This ensures that no duplicate records are generated and no temporary data is left permanently in the buffer or cause memory leaks.

If a Processing Chain is distributed to several hosts the system will automatically take care of usage data transmission between hosts. This is done by an application that is divided into the sender and receiver processes which reside in the separate hosts.

There is a mechanism for discarding usage data that is identified to be invalid by the usage data processing logic. It is possible to feed the invalid usage data back to the data processing chain.

Restarting is tried a few times. If the first restart does not succeed the current block of input records for the Node is discarded as faulty data to a storage directory and the processing continues from the next record block in the queue.

Node Managers can send SNMP traps to inform Network Management System about the statuses of the Nodes and possible problems such as low disk space database and network connection trouble. The status information is also stored to the System Database from where the information is collected and shown in the User Interface.

Different types of Node Applications that are responsible of the usage data processing are listed in this chapter. Some of the Node Applications are common for most of the product installations and some are customer specific.

Online Interface Nodes receive data that needs online processing . These are for example checking a balance of a user or checking whether the user is authorized to get the requested service. Online Interface Nodes also handle a process of answering to the network element.

In an embodiment of the invention the buffers in phases and i.e. in online mediation streams are memory based i.e. random access memory. The memory based buffers have strong availability and low latency. It should be noted that the memory based buffers can be used also in off line mediation streams.

Collector Nodes collect usage data either as files or through a real time protocol. There are generic Collectors and Network Element specific Collectors.

Collector Nodes parse the usage data collected. It is possible to define rules how data is parsed in the application configuration. A typical Collector converts the usage data into internal format for the next Node in the Processing Chain. It is also possible that the Collector Node is the only Node in the Processing Chain in this case the Node collects parses processes and delivers the usage data. An example of this is a Node that acts as a protocol converter.

When Node Application operates based on the internal data format no data parsing and formatting functionality is needed. The Node Application receives data record by record from the internal data transmission mechanism.

Correlation may use external record storage for intermediate records. The correlation function is able to read records from multiple sources.

Distribution Nodes deliver usage data either as files or through a real time protocol record per record. There are generic Distribution Nodes and Business Support System specific Distribution Nodes.

The Delivery Nodes encode the data to the format the interfaced OSS BSS requires. For file based delivery file naming functionality is available. In case of file batch type delivery it is possible to schedule the delivery application.

In case of insufficient processing capacity of a mediation function or functions within a processing stream an embodiment starts up an identical copy of the node in question to scale up the processing capacity of the system. shows an example in which the node has insufficient performance in scenario A. In scenario B the node has been duplicated to run in nodes and which are running in parallel and sharing workload between them. Because the embodiment uses buffers between the consecutive nodes the parallel nodes and can use the same buffers from which to read and to which to write the processed data items such as event records. In such an arrangement the preceding node need not be modified when duplicating node as node can continue writing its output to the one and same buffer . In a corresponding manner node can read from the same buffer regardless of the number of nodes that write to the buffer .

If the processing capacity of a single host is the bottleneck the sharing of the workload can be done between hosts. describes an embodiment which is able to enhance processing capacity of the system in this way. In nodes and have been multiplied into nodes and running in one host and nodes running in another host all processing the event records or other data items in parallel. In online mediation process the buffers between the processing nodes i.e. online interface node processing node encode decode etc. are memory based.

The node duplication can also be used in dynamical allocation of the processing power of the system between online processing and off line processing . For example the system can duplicate an online stream in case a latency time of the online processing tends to increase. The duplicate stream may then be removed if the amount of online processing load decreases. Similarly the number of parallel off line streams may be increased for example during times of low online processing load and thereby the throughput of the system may be increased. The same principles apply also to host multiplication if the system has an auxiliary host available.

Buffers are placed between the nodes to ensure reliability of the mediation process. Reliability measures with the buffers include a certain processing order of event records within the node outgoing buffer and incoming buffer . In an embodiment event records are stored within the buffers as groups. Number of records in each group can dynamically vary during runtime from one record to any number of records as long as there is free storage space available. Event records are not deleted from incoming buffer before the node has processed all information relating to a record group and has written the processed event records to outgoing buffer thus ensuring data integrity in failure situations. In case of multiplied mediation process where one incoming buffer feeds several nodes the first node available for process takes the first available event record group for processing. The system is provided with a locking mechanism to ensure that each event record is processed by one of the multiplied nodes only. When a node takes an event record group for processing the node marks locks the event record group with under processing status. Hence the other nodes know that the particular group is reserved for another node and they can take the next one from the buffer for processing. As already described above the processing node removes the copies of the event records in a group from the incoming buffer only after processing and successfully writing the processed event records into the outgoing buffer . Thus no data is lost in case the processing node shuts down in an uncontrolled way due to failure of the node or external system and the lock of the input event record group is automatically released by the underlying UNIX operating system for instance. When the node recovers it removes any incomplete record groups in output buffer s and restarts processing from the start of the input record group. In case of multiple nodes reading from the same input buffer another node will take care of processing the interrupted input record group as soon as it is unlocked.

Buffers also guarantee that in case the system or a part of it breaks down the whole mediation process need not be started from the beginning. Instead the process can continue from the point wherein the break down happened. The system keeps an audit trail of records read and written by each node to ascertain that no records are lost or duplicated even if failure occurs.

An embodiment of the invention utilizes shared memory transport in online charging rating balance management and account update functionalities . The shared memory transport is useful in online mediation environment where the service usage message is processed at once and online e.g. within the active session. This kind of request response functionality requires extremely low latency in order to function properly. The normal buffering techniques i.e. file based buffering are not fast enough for online mediation. It would be possible to do without the buffers but as described above there are considerable advantages attainable by means of a buffering mechanism. Therefore in an embodiment the service usage messages are transported between the execute functions nodes node applications by memory based buffers also called shared memory transport or by a useful and fast enough protocol e.g. TCP.

Further in an embodiment of the invention off line data is processed as one way stream from network elements through the process of convergent mediation system to different OSS BSS elements . Typically there is a huge amount of off line data to be processed. Further a unit of off line data is typically much bigger than a unit of online data. At the same time online data should be processed as quickly as possible. This is required by the nature of online use prepaid . Typically the prepaid account has to be checked and credited before the service is given to the subscriber. This functionality is also called pre delivery control. The pre delivery control prevents all kind of fraudulent use. It should be noted that the online stream also generates data for off line processing in some cases for example information for billing. This does not affect the actual online processing i.e. the request response mechanism.

Furthermore in an embodiment of the invention the one platform technology provides a stream loopback functionality. This functionality enables visualizing and configuring the online mediation stream in the convergent mediation system . In an embodiment of the invention a node implements both collector and distributor functionalities to enable the request response type synchronous collection or front end interfaces.

According to an embodiment the architecture uses interactive nodes to manage the processes of online mediation . These nodes are called interface nodes . Further the interface nodes have the responsibility of carrying out the request response actions they are connected to network elements or devices near network elements or devices responsible of proxying or controlling the actual communication.

In some embodiments the node functionality is made by e.g. C Perl or Java languages. The embodiment fits for normal hardware platforms such like SunOS LINUXintel HP UX AIX and Itanium.

In another embodiment of the invention a shared memory transport is used. The transfer of records between nodes can also be through files in a buffer directory . Each file contains a number of records which are processed within a transaction. When transaction is at end the node flushes files and commits. Creating opening flushing and scanning for files is slow so the bigger the input files are the better the node s throughput is. Latency is however bad when using file based buffer mechanism .

To greatly improve the latency the records are passed between nodes in a more efficient way than files. Most efficient buffer mechanism for inter process communication is shared memory so an embodiment uses shared memory as a record buffer container .

According to an embodiment a buffer includes a record queue data area and memory allocator data. When a writer writes a record into the buffer it allocates memory from the data area stores the prepared record into the allocated data block and inserts information about the record into the record queue. The reader processes the records from the queue in order. When the writer runs out of data area memory it will free old processed records from the queue and data area. The data areas may be arranged such that each buffer has a single reader and writer. To enable scalability each reader and writer can access multiple buffers .

An embodiment of the invention allows threads and locking mechanism. To enable low latency processing of records the writer and reader nodes must be synchronized. According to an embodiment this problem is solved as follows the writer node holds a lock in the record queue for the next record it is going to write. The reader always tries to acquire a lock from the queue if it can acquire a lock it either means that a record is available for processing or that the writer node is dead since no lock is being held. If the writer is dead reader will sleep until a writer becomes available. Due to the locks used through the shared memory the reader process is woken up immediately when the writer has finished writing a record.

In embodiments wherein the readers are able to read from multiple input buffers and so try to acquire a lock from multiple buffers simultaneously a multithreading support is added to Node Base . Each input buffer has its own reader thread which will signal the main Node Base thread when there are records to be processed.

The performance of the shared memory transport has been tested for several types of nodes such like C Perl and Java based nodes. Some performance tests were executed to find out the throughput and latency of the architecture . Two streams were tested one with separated decoders and encoders one with a single business logic node. Note that no actual encoding decoding is done the collector simply generates records and sends them through the stream and calculates the time it took for the record to come back.

In both streams the interface node initiates the test by generating 2 records for the Stream A and 5 records for the Stream B. Those records will then cycle through the stream when the record arrives back to the interface node the node will write a new record. In effect there is a total of 2 or 5 records in the stream being processed at all times. Adding more records causes queues which does not improve performance but does increase latency.

The streams were run for a short while and performance was measured. Average latency for a batch of 1000 5000 records the number of records per CPU second used for the interface and the business logic nodes and the whole stream throughput in records per real time second.

In order to measure the latency the interface node inserts the current time into the record before writing it out and when the record arrives back into the interface node it reads the timestamp from the record and compares it to the current time.

According to an embodiment of the invention the scalability of the shared memory transport implementation can be used with multiple IN OUT streams between the nodes to enable faster response times per transaction and higher throughput in overall. Also nodes are able to start in any order if some of the nodes have been stopped or crashed. A recovery for shared memory buffer can be done when a node has crashed. Further inspecting buffers from command line flushing buffers to files makes the operability of the mediation system easier. Node Base supports also multithreading. This means that Node Base allow reader threads to process the records themselves instead of synchronizing with a main thread. Furthermore a configuration of the shared memory mode through user interface and XML is possible. By these means it is possible to enable disable per link configure buffer size inform fault detection etc. The fault detection notices when any node in the stream fails pausing the processing and resuming when stream is back in working order.

An embodiment of the invention enables a functionality of stream loopback. To be able to visualize and configure the online mediation stream there is provided a node that can act as a Collector and Distributor to enable request response type synchronous communication between the Network Elements and the online collection front end interfaces . The loopback feature is implemented by defining an interface node . The interface node contains both a collector and a business logic node and further it can read records from input buffer but it also can efficiently read and send records to an outside system. This allows a creation of streams that have multiple interfaces to outside systems . This is also presented in .

The following example describes one kind of minimal online mediation type of stream build on top of the one platform architecture . This example shows one possible implementation to build a stream using node architecture that is capable of providing high enough performance and low latency that is required for the convergent mediation system . In the example there are three components involved client application online stream and AAA functionality.

The node application creates a Diameter credit control like traffic for multiple sessions. Each session is started with ccr init request. It is followed by ten ccr update request. The sessions are ended with ccr final request. This makes a total of 12 messages for each session. The average packet size is 200 bytes. One client establishes one physical connection to stream. The window size is 10 there is a maximum of 10 messages in processing concurrently.

Online Stream implements microbalancing credit control application . When it receives a ccr init request for a session it will request new quota from accounting system AAA functionality and store the reserved quota to session cache non persistent . Each ccr update request decrement the quota in the session cache. The cc final request will return the unused quota to accounting system.

AAA functionality is a Java echo server application. It simulates accounting systems quota reservation and return by echoing back the ccr init and ccr final packets received from the stream .

An embodiment of the invention executes separate thread and when there is something to process the node base is notified. This could be a service provided by the node base e.g. we could have a callback defined where node developer may include a blocking operation. When callback function returns the node base will invoke the process method with the main thread.

An embodiment of the invention has a high availability feature which is shown in this setup as two interface nodes installed on two hosts. For example two hosts can be physically located far away from each other for disaster control. Network elements are connected to both hosts. The nodes are in active active mode meaning that both nodes receive traffic all the time. The traffic is distributed based on the subscriber IMSI therefore the traffic of one IMSI should always go to the same node. However in case of interface node failure NE detects these as described in diameter documentation all the traffic will be routed to other surviving node. The traffic will be routed back once the crashed node is up and running. The business support system has two interfaces primary and secondary. Secondary is only used if primary is down detected as described in diameter documentation .

Additionally there is at least one delivery where the interface node generates mid call charging events to the business logic flow 

An embodiment of the invention presents the following setup examples. Two interface nodes share the local cache for micro balancing e.g. the user session state identified by the IMSI is known by both nodes . If the other interface node crashes the other one is able to function independently. When the failed node is back on line the system is able to start operating normally. The system updates are possible so that the service level is not affected. Interface nodes can be updated independently. If a shared resource such as a local cache in memory database or session control ordinary database requires an update the system update is done without affecting service level. One solution would be to add new interface nodes that use the new shared resource. The new traffic e.g. new user sessions is routed to new updated nodes. The old nodes are not removed from the system until the old traffic has been handled.

A further embodiment of the invention provides the following session control issues. Session control is basically a persistent and clustered scheduler. It has the following requirements. The scheduled event is executed only once in the cluster e.g. if you scheduled a job that should be invoked every minute it is invoked once per minute in one node only . Scheduler makes sure that all the events get executed even if they were a bit late. However there is configurable misfire threshold that defines how old missed jobs are still triggered. Jobs rejected due to misfire threshold raise an alarm. Scheduler supports one time only and recurring tasks. The scheduler supports rescheduling if there is a temporary error e.g. in resources. When there is a temporary error in one of the nodes the scheduler should route the jobs to currently working node and execute scheduled and re scheduled tasks there until the failing node has recovered from the errors.

An embodiment provides a visual picture for the operator as to how the logic is implemented. Using lot of branching makes the logic more like process flow

Adding new custom functionalities to the embodiment with visual appearance can be extended with function libraries. These libraries are for example c c implementations which introduce functions with visual appearance specific signature. Signature is very generic and doesn t limit the number of parameter nor returned values but it only supports string and integer type of parameters.

Function library contains user interface definitions including input and output parameter introduced for each function. Based on these definitions user interface lets the user to select record field values or node parameters and input parameters and set temporary field or global variable to which return values are stored.

The above description is only to exemplify the invention and is not intended to limit the scope of protection offered by the claims. The claims are also intended to cover the equivalents thereof and not to be construed literally.

