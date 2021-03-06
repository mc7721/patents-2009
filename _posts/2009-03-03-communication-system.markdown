---

title: Communication system
abstract: A cooperating system includes a web server and a communication service control server, where information of an error in a communication network is not notified until the web server makes an inquiry to the communication service control server. To solve this problem, a communication system is configured to include a session control server for controlling communication sessions from/to a plurality of terminals, an application server for communicating with the session control server, a web server for communicating with the application server, and a network for coupling the session control server, the application server and the web server. The application server is configured to transmit status related information including information on each communication session status of the plurality of terminals to the web server. The web server is configured to detect each communication session status of the plurality of terminals based on the received status related information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08364827&OS=08364827&RS=08364827
owner: Hitachi, Ltd.
number: 08364827
owner_city: Tokyo
owner_country: JP
publication_date: 20090303
---
The present application claims priority from Japanese patent application JP 2008 145830 filed on Jun. 3 2008 the content of which is hereby incorporated by reference into this application.

This invention relates to a communication system and more particularly to a communication system in which SIP session control is used.

The third generation mobile network system aims to provide various multimedia services of high quality and high speed. The multimedia services include voice data video and the like. The 3rd Generation Partnership Project 3GPP has been promoting standardization of an All IP based mobile communication network to provide a multimedia service using an internet protocol IP technique on a packet switching network.

A session control system in the All IP based mobile communication network is called an IP multimedia subsystem IMS . The IMS has been used in the session control technique in the next generation network NGN .

A session initiation protocol SIP is used as a session control protocol For example see IETF RFC3261 SIP Session Initiation Protocol 4 . The SIP is a protocol for performing session control of the IP multimedia communication specified for internet engineering task force IETF .

A voice over IP VoIP is a representative service using the SIP. The VoIP is a technique which transmits receives voice information on the IP network. The VoIP communication using the SIP requires a setting of a virtual speech path a session between communication devices which transmit receive voice information. Voice data which is IP packetized is transferred through the set virtual speech path. In the VoIP communication the SIP controls initiation maintaining and termination of sessions between the communication devices.

Media information such as attributes of the voice data is determined at the session initiation. The media information is notified using a session description protocol SDP included in a SIP message. The SDP describes various pieces of session information an IP address a port number a media type for example .

Further an application programming interface API is being considered for being able to use a communication service provided by a provider from a Web service provided by a third party.

The Parlay Group is a group that specifies an open API which does not depend on a network or a vendor. The Parlay Group is planning to use Parlay X as the open API. Parlay X specifies APIs for the purposes of the usage in a Web service environment and the Web service of which usage is not limited to an implemented language. The Parlay X provides Web developers with abstracted communication APIs.

The APIs specified in the Parlay X include for example 3rd party call control 3PCC which provides a two party speech service by initiating from a Web application side. For example see 5th Draft ES 202 504 2 Parlay X 3.0 Part 2 Third Party Call online August 2007 .

The Parlay Group cooperates with the European telecommunications standard institute ETSI and the 3generation partnership project 3GPP . The Parlay X is published by the three groups and defines a standard open interface however how the Parlay X is implemented is not specified.

In the Parlay X usage of APIs for each service is specified. A request message including session initiation session termination and call information query to a communication system from a Web application server and a response to the message are specified for the APIs to be used for the 3PCC.

However ways for implementation such as transmitting intervals for the request message and the response message are not specified. Accordingly in a case where the communication is terminated while the 3PCC service is provided a way to notify that a server which provides with the Web application terminates the communication from the communication system is needed. For example although when the communication is terminated the termination cannot be notified to the communication system to the Web server. Thus even though the communication is terminated communication network resources are consumed more than necessary or billing mistakes occur because the Web server cannot detect the termination of the communication.

The object of this invention is to provide a method for a Web server to detect termination of communication sessions.

A representative aspect of this invention is as follows. That is there is provided a communication system comprising a session control server for controlling communication sessions from to a plurality of terminals an application server for communicating with the session control server a Web server for communicating with the application server and a network for coupling the session control server the application server and the Web server. The application server is configured to transmit status related information including information on each communication session status of the plurality of terminals to the Web server. The Web server is configured to detect each communication session status of the plurality of terminals based on the received status related information.

According to an embodiment of this invention a Web server is able to detect termination of communication sessions on a communication system side.

As a representative example a detailed description of a communication method using 3rd party call control 3PCC is given.

A network according to this embodiment includes IP network N and access networks NA NB and NC access network N .

The IP network N and the access network N are connected via access gateway apparatuses AGWs A B and C . The IP network N and the access network N may be connected by other communication apparatuses such as a router instead of the AGWs . Each AGW transfers IP packets transmitted received between the terminals and the IP network N. The IP network N at least comprises one SIP server .

A Web server comprises a user interface function for initiating a 3PCC service a function necessary for initiating the 3PCC service and a mutual communication function between the Web server and a SIP application server .

The SIP application server comprises a function for controlling execution of an IMS application a SIP application .

Note that shows one SIP server one Web server and one SIP application server as an example. However a plurality of these servers may be installed in the communication network in a case where this invention is implemented.

The Web server comprises interfaces IFs A and B which accommodate lines A and B a CPU a memory and a database DB . Each element is connected by a bus .

The memory stores a program which executes protocol processing and a program which executes the mutual connection function between the Web server and the SIP application server . Note that the memory may store IMS further additional programs.

The CPU is a processor which executes the programs stored in the memory . In descriptions hereinafter the processes the Web server execute are actually performed by the CPU by executing any one of the programs stored in the memory .

The program which executes the protocol processing includes a program SOAP control module and a program user interface control module . The SOAP control module provides a function to transmit receive signals between the Web server and the SIP application server . The user interface control module provides a function to transmit receive signals between the terminals and the Web server .

The program which executes the mutual connection function includes a processing program which performs timer reception and a session information table in which information for each session is stored. Note that the database may include the session information table .

The Web server includes the timer reception processing program and the session information table . Accordingly the Web server can control a transmission period of a call information query request by using a time value received from the SIP application server . Details will be described later with reference to .

In a case where the Web server receives a message transmitted from the SIP application server the Web server checks the session information table and updates the session information table based on information included in the message.

The session information table at least includes a Parlay X call session identifier a SIP AS IP address a 3PCC identifier and a timer .

The Parlay X call session identifier holds an identifier for uniquely identifying the communication session between the Web server and the SIP application server . This Parlay X call session identifier is the same one as a Parlay X call session identifier in which will be described later.

The SIP AS IP address holds an identifier for identifying the SIP application server corresponding to the Parlay X call Session Identifier .

The 3PCC identifier holds an identifier for identifying a communication session between the SIP application server and the terminals connected through the 3PCC service provided by the SIP application server . This is the same one as the 3PCC identifier which will be described with reference to later.

The timer holds a transmission period a timer value of a call information query request that the Web server transmits to the SIP application server .

The session information table includes the timer value . Accordingly the Web server can quickly detect termination of the communication session or the end of the communication between terminals.

The SIP application server comprises interfaces IFs A and B which accommodate lines A and B a CPU a memory and a database DB . Each element is connected by a bus .

The memory stores a program SIP protocol control module HTTP protocol control module and SOAP control module which executes protocol processing a program a SIP user agent control processing module 3PCC control processing module which executes processing to achieve the 3PCC server a program a session timer notification routine which executes timer notification processing a session information table in which information for each session is stored and a processing program which performs protocol translation SOAP SIP . Note that the memory may store further additional programs.

The CPU is a processor which executes the programs stored in the memory . In descriptions hereinafter the processes executed by the SIP application server are actually performed by the CPU by executing any one of the programs stored in the memory .

The program which executes protocol processing includes a program the SIP protocol control module for providing a function for transmitting receiving signals between the SIP application server and the SIP server and a program the HTTP protocol control and the SOAP control module for providing a function for transmitting receiving signals between the SIP application server and the Web server .

The program which executes processing to providing the 3PCC server includes the program which performs the SIP user agent processing and the program which performs 3PCC control.

The program which performs 3PCC control is a program for controlling communication between more than two terminals. For example the program holds association information of the communication session between the terminal A and the SIP application server and the communication session between the terminal B and the SIP application server in order to make possible communication between the terminal A and the terminal B through the 3PCC control processing. Furthermore the session timer notification routine the session information table used for storing the information on the each session and the processing program which performs the protocol translation SOAP SIP are included. Note that the database may include the session information table .

The SIP application server includes the session timer notification routine and the session information table . Accordingly the SIP application server can notify the Web server of the transmission period a timer value of the call information query request.

In a case where the SIP application server receives a message transmitted from the SIP server the SIP application server checks the session information table and updates the session information table based on information included in the message.

The session information table at least includes a Parlay X call Session Identifier a Web server IP address a 3PCC identifier a timer T a timer T status and a timer T .

The Parlay X call session identifier holds an identifier for uniquely identifying the communication session between the Web server and the SIP application server . The identifier is generated when the SIP application server receives a request for a SIP session initiation from the Web server and the identifier is held in the Parlay X call Session Identifier . The detail will be described later with reference to .

The Web server IP address holds an identifier for identifying the Web server corresponding to the Parlay X call Session Identifier .

The 3PCC identifier holds an identifier for identifying a communication session between the SIP application server and the terminals connected through the 3PCC service provided by the SIP application server . The identifier is generated when the SIP application server initiates a SIP session and is held in the 3PCC identifier . The detail will be described later with reference to .

The timer T and the timer T hold transmission periods timer values of messages inquiring about communication session status to each terminal. Note that although two party communication is assumed in this embodiment the number of timers increases according to the number of connected communication terminals in a case where more than two parties are communicating.

The status holds communication session status. Note that the status includes session initiating busy terminating participating in a three party communications and logging out.

The timer T holds a transmission period a timer value of the call information query request that the Web server transmits to the SIP application server . The timer T is obtained by a method see which will be described later and held in the session information table .

The session information table includes the timer T . Accordingly the SIP application server can notify the Web server of the transmission period of the call information query request. Thus the Web server can quickly detect termination of the communication session.

The SIP server includes interfaces IFs A and B which accommodate lines A and B a CPU a memory and a database DB . Each element is connected by a bus .

The memory at least holds a SIP server function a session status management table and a SIP protocol control program which executes protocol processing. Note that the memory may store further additional programs.

The CPU is a processor which executes the programs stored in the memory . In descriptions hereinafter the processes the SIP server execute are actually performed by the CPU by executing any one of the programs stored in the memory .

The session status management table at least includes association information of a To header a From header a call ID a timer T and status which are all included in a SIP message.

The SIP server holds the session status management table . Accordingly the SIP server is able to store the transmission period the timer value of transmitting receiving a message for checking whether the communication between the SIP application server and the terminals is normally performed. Therefore the termination of the communication session can be detected when the value of the timer T expires without receiving the message from the terminal A for example. Note that in the first embodiment the SIP application server detects the termination of the communication session. The case of the SIP server detecting the termination of the communication session will be described in a third embodiment.

A message for example an HTTP message is transmitted received between the terminal A and the Web server . The message requesting for the initiation of the 3PCC service is transmitted from the Web server to the terminal A S . The message includes an identifier of the terminal A and an identifier of a terminal the terminal B for this case of the connection destination. Note that the 3PCC service is provided by the 3PCC control module the SIP User Agent control module and the SIP protocol control module .

The Web server receiving the message transmits a message make Call Session Request for requesting the session initiation to the SIP application server S . The message includes the identifier of the terminal A the identifier of the terminal B and an identifier of the Web server .

The SIP application server which received the message for requesting the session initiation initiates the 3PCC service S .

In addition the SIP application server generates an identifier for uniquely identifying the communication session between the Web server and the SIP application server and searches for an entry from the Parlay X call Session Identifier in the session information table using the generated identifier as a search key. In a case where the searched entry is not found the SIP application server generates a new entry and registers the generated identifier in the Parlay X call Session Identifier of the generated entry . In a case where the searched entry is found the SIP application server notifies the Web server of an error.

Moreover the SIP application server registers the identifier of the Web server included in the received message for requesting the session initiation in the Web server IP address of the entry .

Furthermore the SIP application server generates an identifier for identifying a communication session connected through the 3PCC service and registers the generated identifier in the 3PCC identifier of the entry .

The SIP application server generates a new entry and transmits a response message make Call Session Response to the Web server after registering each identifier in the generated entry S .

After initiating the 3PCC service the SIP application server transmits receives a message for initiating a communication session between the SIP server and the terminal A S to S and checks whether the terminal A is available to communicate. In addition the SIP application server transmits receives a message for initiating a communication session between the SIP server and the terminal B S to S and checks if the terminal B is available to communicate.

In a case where the terminal A and the terminal B are both determined to be available to communicate the SIP application server transmits to terminal A media information necessary for communicating with the terminal B S to S . The communication between the terminal A and the terminal B is possible through the above described processes S .

When the communication is possible the SIP application server determines a transmission period T and T of a message INVITE for checking communication session status to the terminals . The message is for checking whether the communication session status of the terminals connected through the 3PCC service is normal. Moreover the transmission period T is a transmission period see of a message for checking the communication session status between the SIP application server and the terminal A. The transmission period T is a transmission period see of a message for checking the communication session status between the SIP application server and the terminal B.

The transmission periods T and T of the message for checking the communication session status are determined by using procedure specified in IETF RFC4028. The procedure specified in IETF RFC4028 makes possible periodical update of the communication session by using SIP INVITE or SIP UPDATE. shows an example of a sequence diagram for the periodical update of the communication session by using the SIP INVITE.

More specifically in a case where communication sessions are initiated between the terminals and the SIP application server the transmission periods T and T of the message INVITE for checking the communication session status by transmitting receiving the smallest value of the period and the like of updating the communication session. Note that the transmission periods T and T may have different values.

With the transmission periods of the transmission periods T and T whether the communication session status is normal can be checked by transmitting receiving the SIP message between the SIP application server and the terminal . Note that the message transmitted received for periodically checking the communication session status is normal between the SIP application server and the terminal and may be often called a keep alive message.

After the transmission periods T and T are determined the SIP application server searches for an entry from the session information table using the 3PCC identifier as a search key and sets the timer value T and the timer value T of the searched entry. Moreover the SIP application server sets busy in the status of the searched entry.

The Web server transmits a call information query request get Call Session Information Request for checking the communication session status to the SIP application server S . The SIP application server which received the call information query request transmits a response message get Call Session Information Response including the communication session status to the Web server S . Accordingly the Web server can detect the communication session status.

The message specified by the Parlay X is transmitted in S and S. In this embodiment the message is transmitted at least once after the communication session is initiated between the terminals. Note that the message may be transmitted before the communication session is initiated.

S to S and S and S in show transmission reception of the message keep alive message for checking the communication session status of the terminal A. S to S and S to S in show transmission reception of the message keep alive message for checking the communication session status of the terminal B.

In addition the timer T shows the transmission period the interval between the S and S of the keep alive message between the SIP application server and the terminal A. Similarly the timer T shows the transmission period the interval between the S and S of the keep alive message between the SIP application server and the terminal B. Note that the sequence S to S shows a process generally performed when the 3PCC service monitors the communication session status.

The processes of S to S are the same as that of . However information included in the message transmitted received between the Web server and the SIP application server differ because the timer T of the session information table and the timer of the session information table are added. The difference will be described.

After the timer T and the timer T are determined the SIP application server initiates the session timer notification routine to obtain the timer T using the timer T and the timer T of the session information table S . Hereinafter the session timer notification routine is described with reference to .

The SIP application server checks the timer T and the timer T of the session information table to obtain the session timer . More specifically the SIP application server compares the timer T and the timer T and determines a value smaller than the timer value as a session timer. Accordingly the Web server then is able to inquire of the SIP application server about the communication session status based on the obtained session timer. Note that the obtained session timer is preferably a comparable value as the timers T and T so that communication load caused by the query request from the Web server to the SIP application server can be suppressed.

After the session time is obtained the SIP application server searches for an entry from the session information table using the 3PCC identifier as a search key . In a case where the searched entry is found the SIP application server registers the obtained session timer in the timer T of the searched entry and S and ends the routine. In a case where the searched entry is not found the SIP application server ends the routine.

The Web server transmits the call information query request get Call Session Information Request to the SIP application server S . Note that S is the same one as the message transmitted in S in .

The SIP application server which received the call information query request searches for a entry from the session information table using the Parlay X call Session Identifier included in the call information query request as a search key and reads the status and the timer T from the searched entry.

In a case where the timer T is not set to the searched entry the SIP application server transmits the response message get Call Session Information Response including the communication session status to the Web server S .

In a case where the timer T is set to the searched entry the SIP application server transmits the response message get Call Session Information Response including the read communication session status and the timer T to the Web server S .

In a case where the Web server receives the response message the Web server searches for an entry from the session information table using the Parlay X call Session Identifier included in the response message as a search key and reads the searched entry. In a case where the searched entry is not found the Web server generates a new entry and registers the Parlay X Session Identifier the SIP AS IP address the 3PCC identifier and the timer based on the communication session status and the timer T included in the received response message. In a case where the searched entry is found the Web server registers the timer T included in the received response message in the timer of the searched entry.

With the above described processes the Web server is able to periodically transmit the call information query request get Call Session Information Request to the SIP application server based on the value registered in the timer . Consequently the Web server can quickly detect communication errors such as termination of the communication session.

The initiation process of the 3PCC service and the check process of the communication session status performed when the 3PCC service is continued are similar to those of . Here it is assumed that the communication session of the terminal A is terminated with some reason.

The SIP application server is not able to receive the keep alive message transmitted received in the period T between the SIP application server and the terminal A. Consequently the SIP application server determines the communication session status as terminated because the SIP application server did not receive a response to the message INVITE S and S for a certain period of time. The SIP application server searches for an entry from the session information table using the 3PCC identifier as a search key and updates the status of the searched entry to terminated S .

The Web server transmits the call information query request get Call Session Information Request in a period of the timer to the SIP application server S .

The SIP application server which received the call information query request searches for an entry from the session information table using the Parlay X call Session Identifier included in the call information query request as a search key and reads the status and the timer T from the searched entry. The SIP application server transmits a response message get Call Session Information Response including the status terminated for this case and the timer T to the Web server S .

The Web server which received the response message including the status terminated for this case checks the status terminated included in the response message. In this case the Web server determines that the communication session is terminated because the status is terminated . The Web server transmits a request end Call Session Request for terminating the 3PCC service to the SIP application server .

The SIP application server which received the request for terminating the 3PCC service transmits a response message end Call Session Response to the Web server S and performs the termination process of the communication session S and S . Moreover the SIP application server deletes the entry of status being terminated from the session information table after an expiration of a certain time from the termination process of the communication session.

The Web server periodically transmits a call status query request to the SIP application server using the timer value the T in this embodiment notified by the SIP application server . Accordingly the Web server is able to quickly detect a failure of the communication session.

Next a second embodiment is described with reference to the drawings. In the first embodiment the SIP application server notified a timer value which is a period inquiring the communication session status. Meanwhile in the second embodiment a Web server requests a SIP application server for the communication session status.

The Web server requests the communication session status. Accordingly the SIP application server is able to notify the Web server that the communication session status between terminals is being terminated .

A communication network in the second embodiment is same as that of the first embodiment. Accordingly the description is omitted see . Hereinafter only differences between the first and the second embodiments are described.

In the second embodiment a memory includes a processing program for inquiring presence information instead of the timer reception processing program .

The Web server includes the presence information query function . Accordingly the Web server is able to request the SIP application server for notification of the presence information. Note that in the second embodiment the presence information query function is initiated after the initiation of a 3PCC service.

In the second embodiment a memory includes a processing program for performing presence information notification instead of the session timer notification routine .

The SIP application server includes the presence information notification function . Accordingly the SIP application server is able to notify the Web server of the presence information to which the communication session status is added.

The session information table includes a monitor showing whether the SIP application server is monitoring communication session status instead of the timer T . Note that in a case where the monitor is set to be on and the communication session status is changed to terminated from busy the SIP application server notifies the Web server of termination of the communication session using the presence information notification function .

Next a 3PCC service initiation sequence in the second embodiment is described with reference to . Hereinafter among the procedures shown in the description of the same procedures as those of shown in and are omitted.

The Web server transmits the call information query request get Call Session Information Request for checking the communication session status to the SIP application server S .

The SIP application server which received the call information query request searches for an entry from the session information table using the Parlay X call Session Identifier included in the call information query request as a search key and reads the status from the searched entry. The SIP application server transmits a response message get Call Session Information Response including the status to the Web server S .

Note that the processes of S S S and S to S are same as those of the first embodiment. A message keep alive message for checking the communication session status between the SIP application server and a terminal A is transmitted received at the period of the timer T. A message keep alive message for checking the communication session status between the SIP application server and a terminal B is transmitted received at the period of the timer T.

The Web server which received a response message S checks that the status included in the response message is busy and transmits a request subscribe Presence Request for notifying the communication session status to the SIP application server S .

The SIP application server which received the request searches for an entry from the session information table using the Parlay X call Session Identifier as a search key. The SIP application server transmits the response message subscribe Presence Response to the Web server after updating the monitor status of the searched entry to on S .

The processes of S to S and S are same as those of the first embodiment. Here it is assumed that an error is occurred in the terminal A.

In S the SIP application server searches for an entry from the session information table using the 3PCC identifier as a search key because the keep alive message is not received. The SIP application server updates the status of the searched entry to terminated . Moreover the monitor of the searched entry is checked. In a case where the monitor of the searched entry is on the SIP application server transmits the Web server of the message notify Subscription Request for notifying that the communication session is terminated S .

The Web server which received the message transmits the response message notify Subscription Response including a request for terminating the 3PCC service to the SIP application server S . Then a session termination process is performed see S to S in .

According to the second embodiment the SIP application server can quickly detect the change in the status of the session information table from busy to terminated because the Web server includes the presence information query function . In addition the SIP application server determines that the communication session is terminated and notifies the Web server of the termination of the communication session. Consequently the Web server can quickly detect the termination of the communication session.

In the third embodiment a presence server is connected to a network N. Moreover in the third embodiment the presence server at least includes a watcher function. The watcher function is a function for monitoring status of specified terminals.

The presence server comprises interfaces IFs A and B which accommodate lines A and B a CPU a memory and a database DB . Each element is connected by a bus .

The CPU is a processor for executing programs stored in the memory . The memory stores a program for performing presence notification not shown a processing program necessary for storing presence information a watcher function for example and a table a watcher information table .

The watcher information table at least includes association information of presentity a watcher and status . The presentity shows an entity providing the presence information.

The presence server includes the watcher information table . Accordingly the presence server can detect the communication session status of terminals. Consequently the presence server can determine that the communication session is terminated and notify the Web server of the termination of the communication session. Hereinafter only differences between the second and the third embodiments are described.

The SIP AS information table includes information on a 3PCC call Session Identifier and a presence server which corresponds to the 3PCC call Session Identifier . Accordingly the Web server can obtain information on which communication session the presence server holds.

The Web server includes the SIP AS information table . Accordingly the Web server can associate the status of the presence server with the 3PCC session. Consequently the Web server can obtain the communication session status based on the information transmitted from the presence server .

Next a sequence when an error occurs at the initiation of the 3PCC service in the third embodiment is described with reference to . Hereinafter among the procedures shown in the description of the same procedures as those of shown in and are omitted.

The Web server transmits a request subscribe Presence Request for notifying communication session status to the presence server S when the Web server finds the communication session status busy S . Here the Web server searches for an entry from the SIP AS information table using the 3PCC call Session Identifier as a search key. In a case where the searched entry is not found the Web server generates a new entry and registers an identifier of the presence server . In a case where the searched entry is found the Web server updates the information on the searched entry.

The presence server which received the request transmits a response subscribe Presence Response to the request to the Web server S .

Subsequently the presence server transmits a request SUBSCRIBE for notifying presence information including communication session status a terminal A and a terminal B to a SIP server S . The SIP server which received the notification request for the presence information transmits a response 200 OK to the notification request for the presence information S .

Here it is assumed that the SIP server detects termination of the communication session of for example the terminal A by the keep alive message S . In this case the SIP server notifies the presence server of the presence information NOTIFY including the termination of the communication session of the terminal A S .

The presence server which received the notification transmits a response to the notification of the presence information to the SIP server S . The presence server transmits a notification message notify Subscription Request including the presence information of the terminal A to the Web server S .

The Web server performs session termination after transmitting the response notify Subscription Response to the notification message to the presence server S .

According to the third embodiment the Web server associates the presence server with an identifier of the communication session during initiation. Accordingly the Web server can manage the associated presence server and the identifier of the communication session during initiation. Consequently the Web server can quickly detect the change in the communication session status from busy to terminated .

In addition load on the SIP application server can be reduced by comprising the presence server as compared to the second embodiment. Moreover costs can be reduced using the current presence server without adding a new presence notification function to the SIP application server .

While the present invention has been described in detail and pictorially in the accompanying drawings the present invention is not limited to such detail but covers various obvious modifications and equivalent arrangements which fall within the purview of the appended claims.

