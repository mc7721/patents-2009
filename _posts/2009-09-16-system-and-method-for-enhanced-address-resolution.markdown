---

title: System and method for enhanced address resolution
abstract: As Mobile Subscribers increasingly employ their Wireless Devices to perform an ever expanding array activities an element that may reside in various portions of a messaging infrastructure and which efficiently and flexibly supports enhanced message address resolution capabilities.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09264292&OS=09264292&RS=09264292
owner: Sybase 365, Inc.
number: 09264292
owner_city: Reston
owner_country: US
publication_date: 20090916
---
This application claims the benefit of U.S. Provisional Patent Application Ser. No. 61 097 296 filed on 16 Sep. 2008 which is herein incorporated by reference in its entirety.

The present invention relates generally to telecommunications services. More particularly the present invention relates to capabilities that enhance substantially the value and usefulness of various messaging paradigms including inter alia Short Message Service SMS Multimedia Message Service MMS Internet Protocol IP Multimedia Subsystem IMS etc.

As the wireless revolution continues to march forward the importance to a Mobile Subscriber MS for example a user of a Wireless Device WD such as a mobile telephone a BlackBerry a computer etc. that is serviced in some way by a Wireless Carrier WC of their WD grows substantially.

One consequence of the growing importance of WDs is the resulting ubiquitous nature of WDs i.e. MSs carry them at almost all times and use them for an ever increasing range of activities.

Over the past many years various factors including the ubiquitous nature of WDs have driven a steady annual increase year over year in the number of SMS MMS etc. messages that have been exchanged by and between WDs. That steady increase shows no sign of abating. For example as reported by the industry group CTIA see ctia.org on the World Wide Web in the U.S. there were over 363 billion SMS messages sent during 2007 up from 158 billion SMS messages sent during 2006 and there were over 2.7 billion MMS messages sent during 2006 representing a 100 increase over 2005 .

As the volume of SMS MMS etc. messaging has increased in the past and at present continues to increase it has become more and more important for all of the different entities that process messages e.g. WCs intermediaries enterprises Content Providers CPs Service Providers SPs etc. to route messages in the most efficient expeditious flexible etc. manner possible.

A message may contain among other things a destination address i.e. the address to where the message should be delivered e.g. for a Peer to Peer P2P SMS message perhaps the Telephone Number TN of the recipient MS WD for an Application to Peer A2P SMS message perhaps a Short Code SC that is associated with a particular service such as for example an advertising campaign etc.

The routing of a message may involve a number of operations including possibly inter alia the resolution of the message s destination address i.e. the authoritative identification of the entity e.g. WC landline carrier etc. that at the moment that the message is being routed services or that is otherwise associated with the address.

In the past the resolution of a message s address may have entailed multiple possibly inter alia expensive time consuming etc. lookup operations against one or more internal and or external data repositories. Worldwide the introduction of Mobile Number Portability MNP regimes Number Resource Optimization NRO programs such as TN pooling etc. complicated significantly the operation administration etc. of such lookup operations. Additionally in high message traffic environments the resolution of a message s address may have employed specialized e.g. large data set high volume etc. facilities such as for example IBM s Transaction Processing Facility TPF .

The challenges that were described above highlight the need for a more generalized infrastructure that offers possibly among other things enhanced address resolution capabilities.

The present invention provides such an infrastructure and addresses various of the not insubstantial challenges that are associated with same

One embodiment of the present invention offers a method for resolving an address wherein a a message address is received b various processing steps are completed including passing the message address through a double hash operation with open addressing for collision resolution yielding a reference c using the reference to directly retrieve from an address repository an entry for the message address and d recovering from the retrieved entry an identity of an entity e.g. WC that services the message address.

These and other features of the embodiments of the present invention along with their attendant advantages will be more fully appreciated upon a reading of the following detailed description in conjunction with the associated drawings.

The present invention will now be described with reference to the accompanying drawings. In the drawings generally like reference numbers indicate identical or functionally similar elements. Additionally generally the left most digit s of a reference number identifies the drawing in which the reference number first appears.

The following detailed description of the present invention refers to the accompanying drawings that illustrate exemplary embodiments consistent with this invention. Other embodiments are possible and modifications can be made to the embodiments within the spirit and scope of the invention. Therefore the detailed description is not meant to limit the invention.

Note that in this description references to one embodiment or an embodiment mean that the feature being referred to is included in at least one embodiment of the present invention. Further separate references to one embodiment in this description do not necessarily refer to the same embodiment however neither are such embodiments mutually exclusive unless so stated and except as will be readily apparent to those skilled in the art.

Under one embodiment aspects of the present invention may form an integral part of a MPI which may among other things support the expeditious resolution of message addresses within possibly inter alia a MICV.

Reference is made to U.S. Pat. No. 7 154 901 entitled INTERMEDIARY NETWORK SYSTEM AND METHOD FOR FACILITATING MESSAGE EXCHANGE BETWEEN WIRELESS NETWORKS and its associated continuations for a description of a MICV a summary of various of the services functions etc. that are performed by a MICV and a discussion of the numerous advantages that arise from same.

As illustrated in and reference numeral a MICV is disposed between possibly inter alia multiple WCs WC WC WC on one side and multiple SPs SP SP on the other side and thus bridges all of the connected entities. A MICV thus as one simple example may offer various routing formatting delivery value add etc. capabilities that provide possibly inter alia 

1 A WC and by extension all of the MSs that are serviced by the WC with ubiquitous access to a broad universe of SPs and

2 A SP with ubiquitous access to a broad universe of WCs and by extension to all of the MSs that are serviced by the WCs .

Generally speaking a MICV may have varying degrees of visibility e.g. access etc. to the MS MS MS SP etc. messaging traffic 

1 A WC may elect to route just their out of network messaging traffic to a MICV. Under this approach the MICV would have visibility e.g. access etc. to just the portion of the WC s messaging traffic that was directed to the MICV by the WC.

2 A WC may elect to route all of their messaging traffic to a MICV. The MICV may possibly among other things subsequently return to the WC that portion of the messaging traffic that belongs to i.e. that is destined for a MS of the WC. Under this approach the MICV would have visibility e.g. access etc. to all of the WC s messaging traffic.

While the discussion above referenced a MICV it will be obvious to one or ordinary skill in the art that aspects of the present invention may be found within any of the various entities that process messages for example possibly inter alia WCs intermediaries such as a MICV enterprises CPs SPs etc.

To help illustrate aspects of the present invention consider the simplified MPI that is presented in and reference numeral . Aspects of a MPI may exist within any or all of possibly inter alia a MICV a WC an enterprise a SP a CP etc. In brief a MPI may interact with Entities E E E E such as possibly inter alia elements or components of a MICV or a WC or an enterprise or a CP or a SP or a etc. to 

1 Receive incoming SMS MMS etc. messages over any combination of one or more communication paradigms or channels including possibly inter alia IP Signaling System Number 7 SS7 etc. .

3 Send outgoing SMS MMS etc. messages over any combination of one or more communication paradigms or channels including possibly inter alia IP SS7 etc. 

1 A Gateway . Behind the fa ade of a single consolidated Gateway a dynamically updateable set of one or more software processes running on one or more computer hardware devices not explicitly depicted in the diagram handle incoming traffic and outgoing traffic. Incoming traffic is accepted and deposited on an intermediate or temporary Incoming Queue IQ IQ IQ in the diagram for subsequent processing. Processed artifacts are removed from an intermediate or temporary Outgoing Queue OQ OQ OQ in the diagram and then dispatched.

2 Incoming Queues IQ IQ . A dynamically updateable set of one or more IQs operate as intermediate or temporary buffers for incoming traffic.

3 WorkFlows WF WF . A dynamically updateable set of one or more WFs remove incoming traffic from an intermediate or temporary IQ e.g. IQ IQ perform all of the required processing operations and deposit processed artifacts on an intermediate or temporary OQ e.g. OQ OQ . The WorkFlow component will be described more fully below.

4 Outgoing Queues OQ OQ . A dynamically updateable set of one or more OQs operate as intermediate or temporary buffers for outgoing traffic.

5 A Real Time Query Facility RTQF . When it is necessary to retrieve information about a destination address e.g. a destination TN a RTQF may employ any combination of one or more channels such as SS7 User Datagram Protocol UDP IP Electronic Numbering ENUM Transmission Control Protocol TCP IP etc. to query one or more sources including possibly inter alia publicly available repositories administrative or regulatory bodies such as for example the North American Numbering Plan NANP Administration NANPA WCs landline carriers etc. to complete such retrievals. Reference is made to U.S. Pat. No. 7 154 901 entitled INTERMEDIARY NETWORK SYSTEM AND METHOD FOR FACILITATING MESSAGE EXCHANGE BETWEEN WIRELESS NETWORKS and its associated continuations for a description of how such a facility may provide possibly among other things support for the authoritative determination of a servicing WC given a TN a for any country i.e. any TN numbering scheme around the world and b that fully accounts for complexities such as MNP and NRO regimes.

6 A CAR . A consolidated repository that maintains possibly inter alia raw processed etc. authoritative address resolution data. A CAR may leverage a backstorage repository for possibly inter alia interim long term etc. storage.

7 An Administrator . An Administrator provides possibly inter alia management or administrative control over all of the different system components e.g. IQs IQ IQ WFs WF WF OQs OQ OQ CAR CAR Backstorage RTQF etc. a facility through which configuration information for possibly inter alia one or more system components may be dynamically updated etc. An Administrator may provide as one example a Web based interface it will be readily apparent to one of ordinary skill in the relevant art that numerous other interfaces e.g. a data feed an Application Programming Interface API etc. are easily possible.

Under one embodiment aspects of the present invention may form an integral part of a MPI and support the resolution of TNs. Such an embodiment may possibly inter alia accept as input a TN as for example the destination address of a message and return as output a value that identifies the carrier e.g. WC landline carrier etc. that at that moment in time services or that is otherwise associated with the TN.

Such an embodiment may leverage the E.164 recommendation from the International Telecommunication Union ITU . The E.164 recommendation describes a worldwide public telecommunication numbering plan and defines the particulars e.g. format etc. of an individual TN. Among other things the E.164 recommendation 

2 Indicates that the first digit of an E.164 compliant TN s will identify the TN s geographic zone. For example the first digit of the E.164 compliant TN 17035551234 is one indicating that the TN resides in North America geographic zone 1 . As well the first digit of the E.164 compliant TN 442074841338 is four indicating that the TN resides in Europe geographic zone 4 .

Consequently the universe of E.164 compliant TNs is bounded by the theoretical maximum size of 10 15 or 1 000 000 000 000 000 TNs.

As illustrated by and reference numeral if one selects a 64 bit data value as a consolidated store i.e. e.g. as an individual entry in a CAR and one allocates 50 bits of the available 64 bits to key i.e. address such as TN storage then one can store a maximum of 2 50 or 1 125 899 906 842 624 addresses i.e. TNs . Such an allocation can encompass the entirety of E.164 compliant TNs.

As illustrated by and reference numeral the balance of the 64 bit data value i.e. 64 bits 50 bits 14 bits provides 2 14 or 16 384 different values which in the instant example are identifiers that indicate the carrier e.g. WC landline carrier etc. that services or that is otherwise associated with an address e.g. TN .

A CAR configured as described above may be populated with information from one or more classes of data. For example for geographic zone one NANP compliant TNs information may come from possibly inter alia 

1 Static Data. Examples of this class of data may include for example Easily Recognizable Codes ERCs such as toll free TNs premium rate TNs etc. the Local Exchange Routing Guide LERG etc.

2 Dynamic Data. Examples of this class of data may include for example broadcasts from one or more Number Portability Administration Centers NPACs real time data feeds from carriers e.g. WCs landline carriers etc. results returned to a RTQF etc.

3 Other. Examples of this class of data may include for example manual updates corrective entries etc.

It will be obvious to one or ordinary skill in the art that a wide number of equivalent classes of data may be available for each of the other geographic zones two through nine.

It will be obvious to one or ordinary skill in the art that numerous alternatives to the architecture that was described above are easily possible. Among other things one might support different perhaps mixed key address types e.g. TNs SCs IP addresses E Mail addresses etc. one might employ a different e.g. 128 bit etc. data value as a consolidated store i.e. as an individual entry in a CAR one might employ a different e.g. WC landline carrier etc. indicator scheme one might associate additional information beyond a e.g. WC landline carrier etc. indicator to a key address etc.

Returning to it will be readily apparent to one of ordinary skill in the relevant art that within a MPI numerous other components and or numerous alternative component arrangements beyond that which was described above are easily possible. For example 

1 A Gateway may maintain one or more repositories including possible inter alia a Message Detail Record MDR repository into which selected details of all administrative processing etc. activities may be recorded. Among other things such a repository may be used to support scheduled e.g. daily weekly etc. and or on demand reporting with report results delivered to for example an Entity E E through possibly inter alia any combination of one or more channels such as the World Wide Web WWW via for example a dedicated Web site wireless messaging SMS MMS etc. Electronic Mail E Mail messages Instant Messaging IM conventional mail telephone Interactive Voice Response IVR facility etc.

2 The different repositories that are depicted in including inter alia a CAR CAR Backstorage details of administrative processing etc. activities etc. are logical representations of the possibly multiple physical repositories that might be implemented. The physical repositories may be implemented through any combination of conventional Relational Database Management Systems RDBMSs such as Oracle through Object Database Management Systems ODBMSs through in memory Database Management Systems DBMSs through in memory data structures or through any other equivalent facilities.

Within a MPI flexible extensible and dynamically updatable configuration information may allow a WF component to be quickly and easily realized to support any number of activities. For example WFs might be configured to support various internal processing steps please see below to support the generation and dispatch of response etc. messages to support various billing transactions to support the generation of scheduled and or on demand reports etc. The specific WFs that were just described are exemplary only it will be readily apparent to one of ordinary skill in the relevant art that numerous other WF arrangements alternatives etc. are easily possible. Under different embodiments of aspects of the present invention aspects of one or more WF chains within a MPI may be implemented using the Java programming language.

An illustrative internal processing sequence that may be realized as a WF might include the following steps 

2 Based on a set of flexible extensible and dynamically configurable rules extract various data elements from the incoming message and preserve the data elements in a message protocol etc. neutral Internal Message Object IMO .

3 Based on a set of flexible extensible and dynamically configurable rules process the IMO. For example through possibly inter alia the CAR resolve possibly among other things the message s destination address to identify possibly inter alia a destination WC .

4 Using a set of flexible extensible and dynamically configurable rules complete a route selection process. Such a process may include or consider possibly inter alia any number of data elements or fields in an IMO system configuration information such as defined delivery paths constraints such as Day of Week DoW Time of Day ToD etc. factors such as current system loads and Quality of Service QoS levels paradigms such as Least Cost Routing LCR etc. Such a process may include one or more defined hooks to support possibly inter alia various billing events. The generated Route Selection may be preserved by possibly inter alia recording it in a MDR repository.

5 From the IMO construct an outgoing message and based on possibly inter alia the Route Selection deposit the outgoing message on an OQ. Various of the particulars of the outgoing message may be preserved by possibly inter alia updating one or more entries in a MDR repository.

The specific processing activities that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing activities are easily possible and indeed are fully within the scope of the present invention.

The processing activities that were described above may be implemented through and consequently supported by any combination of a number of technologies etc. For example 

1 An IMO may be implemented through any combination of a number of facilities including possibly inter alia flat files in memory data structures etc. For example within a Java environment an IMO might be implemented as a Java Message Service JMS object with possibly inter alia various data elements or fields realized as individual JMS object properties.

2 The flexible extensible and dynamically configurable rules that were described above e.g. for data element extraction for IMO processing for route selection processing etc. may be implemented through any combination of a number of facilities including possibly alia conventional programming constructs such as for example C Java C Perl etc. regular expressions custom or proprietary solutions etc.

During Step 3 of the processing activities that were described above a CAR may be queried to determine the entity e.g. WC that currently services or that is otherwise associated with a message s destination address e.g. TN . Given the very high volume of messaging traffic that would likely flow through a MPI the CAR along with the WF elements that surround the CAR and interact with it would need to efficiently handle many tens of thousands of lookup operations each second.

Consequently aspects of the present invention employ an innovative highly efficient double hash operation with optional open addressing for the resolution of collisions as an access mechanism to a CAR. A Java class FastHashTable which may be included as part of a Java based MPI WF chain that includes such a hash mechanism that is destined to operate within a 64 bit processing environment and which follows aspects of as described above may contain possibly inter alia 

2 As illustrated by and reference numeral a set of private variables including for example a CAR i.e. table .

4 As illustrated by and reference numeral a put method that accepts a key e.g. address such as TN and a value e.g. carrier indicator and which after completing one or more hash operations and key comparison operations appropriately updates a CAR to store preserve the presented key and value.

5 As illustrated by and reference numeral a get method that accepts a key e.g. address such as TN and after completing one or more hash operations and key comparison operations returns the value e.g. carrier indicator that is associated with the key.

6 A series of support routines. See for example and reference numeral and and reference numeral . Of interest and note are for example the central method doubleHash and the subordinate methods firstHash and secondHash which implement the double hash operation that was described above.

It will be readily apparent to one of ordinary skill in the relevant art that 1 numerous other constants variables methods etc. may be defined within a Java class as described above and 2 numerous other Java classes each with their own elements arrangements etc. are easily possible.

To help illustrate aspects of the operation of the Java class that was described above consider the application program log file snippets that are presented in and reference numeral and and reference numeral . In the instant example log file snippets SCs are employed as keys i.e. addresses but it will be clear to one of ordinary skill in the art that other key types such as inter alia TNs etc. are also possible.

1 Reference numeral captures various of the processing activities that may take place as a new entry consisting of the key e.g. address such as SC 100002 and the value e.g. carrier indicator is added to a CAR through the command 

Following completion of the processing activities the CAR would contain at index e.g. position an entry containing the key 100002 and the value 13.

2 Reference numeral captures various of the processing activities that may take place as a new entry consisting of the key e.g. address such as SC 999930 and the value e.g. carrier indicator 22 is added to a CAR through the command 

Following completion of the processing activities including inter alia multiple hash operations the CAR would contain at index e.g. position an entry containing the key 999930 and the value 22.

1 Reference numeral captures various of the processing activities that may take place as a CAR is queried for the key e.g. address such as SC 100002 through the command 

After locating the key 100002 at index e.g. position of the CAR the value i.e. 13 that is associated with that key is returned and preserved in the variable returnValue.

2 Reference numeral captures various of the processing activities that may take place as a CAR is queried for the key e.g. address such as SC 999930 through the command 

After locating the key 999930 at index e.g. position of the CAR through inter alia multiple hash operations the value i.e. 22 that is associated with that key is returned and preserved in the variable returnValue.

1 Performance. For example a physical realization of aspects of the present invention in support of the resolution of TNs a included a 16 Gb CAR capable of housing the entirety of E.164 compliant TNs and b serviced over 80 000 inquiries each second.

2 Value add services. For example as noted previously a Gateway may maintain one or more repositories e.g. a databases into which selected details of all administrative processing etc. activities may be recorded to support the subsequent generation of scheduled e.g. daily weekly etc. and or on demand reports. Additionally aspects of the present invention including possibly inter alia the extraction of data elements from an incoming message the processing of an IMO etc. may support enhanced troubleshooting problem investigation etc. capabilities within a MPI and those capabilities may as just one example be associated with different offered QoS levels and possible charges for same e.g. one may pay more for the faster etc. routing of a message and pay less for the slower etc. routing of a message .

3 Flexibility and extensibility. For example dynamically configurable sets of rules for as an example the extraction of data elements from an incoming message the processing of an IMO etc. contribute significantly to a responsive open etc. MPI.

During the processing steps that were described above one or more billing transactions may optionally be completed e.g. for each request that is received for various of the processing steps that are performed for each response returned etc. A billing transaction may take any number of forms and may involve different external entities e.g. a WC s billing system a carrier billing system service bureau a credit or debit card clearinghouse etc. . A billing transaction may include possibly inter alia 

1 The appearance of a line item charge on the bill or statement that for example an Entity may receive from their WC. Exemplary mechanics and logistics associated with this approach are described in pending U.S. patent application Ser. No. 10 837 695 entitled SYSTEM AND METHOD FOR BILLING AUGMENTATION. Other ways of completing or performing line item billing are easily implemented by those skilled in the art.

The report etc. messages that were described above may optionally contain an informational element e.g. a relevant or applicable factoid etc. The informational element may be selected statically e.g. all generated messages are injected with the same informational text randomly e.g. a generated message is injected with informational text that is randomly selected from a pool of available informational text or location based i.e. a generated message is injected with informational text that is selected from a pool of available informational text based on the current physical location of the recipient of the message as derived from as one example a Location Based Service LBS facility .

The report etc. messages may optionally contain advertising e.g. textual material if a simple paradigm such as SMS is being utilized or multimedia images of brand logos sound video snippets etc. material if a more capable paradigm such as MMS is being utilized. The advertising material may be selected statically e.g. all generated messages are injected with the same advertising material randomly e.g. a generated message is injected with advertising material that is randomly selected from a pool of available material or location based i.e. a generated message is injected with advertising material that is selected from a pool of available material based on the current physical location of the recipient of the message as derived from as one example a LBS facility .

The report etc. messages may optionally contain promotional materials e.g. still images video clips etc. .

While the discussion that was just presented included a double hash operation with optional open addressing for the resolution of collisions it will be apparent to one of ordinary skill in the relevant art that numerous other operations including inter alia one way functions digest calculations etc. and or collision resolution mechanisms including inter alia chaining the use of buckets etc. are easily possible and indeed are fully within the scope of the present invention.

The discussion that was just presented described a single CAR. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that numerous other CAR arrangements including inter alia multiple CARs organized in a distributed fashion organized hierarchically etc. are easily possible for reasons of inter alia performance reliability size administration etc. and indeed are fully within the scope of the present invention.

The discussion that was just presented included TNs. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that numerous other addresses or identifiers such as possibly inter alia SCs IP addresses E Mail addresses IM handles Session Initiation Protocol SIP addresses etc. are easily possible and indeed are fully within the scope of the present invention.

The discussion that was just presented referenced two specific wireless messaging paradigms SMS and MMS. These paradigms potentially offer an incremental advantage over other paradigms for example native support for SMS and MMS is commonly found on a WD that a potential MS would be carrying. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that numerous other paradigms such as possibly inter alia IMS etc. are fully within the scope of the present invention.

The foregoing disclosure of the preferred embodiments of the present invention has been presented for purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. It will be readily apparent to one of ordinary skill in the relevant art that numerous alternatives to the presented embodiments are easily possible and indeed are fully within the scope of the present invention.

