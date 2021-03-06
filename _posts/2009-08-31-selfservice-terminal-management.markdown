---

title: Self-service terminal management
abstract: A self-service terminal comprises at least one customer transaction module, a terminal controller, a management component, and a network connection coupled to the terminal controller. The customer transaction module is operable to (i) implement a function associated with a customer transaction, and (ii) provide status information relating to the module. The terminal controller is coupled to the customer transaction module and includes (i) a management component for retrieving status information from the customer transaction module and (ii) a Web services interface for providing access to the retrieved status information to a remote device. The network connection is coupled to the controller and provides the remote device with access to the Web services interface.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08870064&OS=08870064&RS=08870064
owner: NCR Corporation
number: 08870064
owner_city: Duluth
owner_country: US
publication_date: 20090831
---
A common type of self service terminal is an automated teller machine ATM . An ATM is a networked computing device that includes a plurality of interconnected modules for performing functions relating to customer transactions and machine maintenance. Many of these modules include a processor programmed to perform functions associated with that module and to track state of health information about that module.

A central processing core typically executes a platform and an application. The platform which includes an operating system manages the modules in the ATM and translates industry standard commands for example in CEN XFS format from the application to specific commands for each module. The application conveys appropriate industry standard commands to the platform to provide customer transactions and also to provide management facilities for service personnel such as printer paper replenishers banknote replenishers or technicians .

A remote management system typically manages a network of ATMs each ATM providing status information to the management system asynchronously in the event of a failure being detected or in response to a request for information from the remote management system.

The remote management system typically dispatches service personnel in the event of a failure being detected at an ATM and provides the service personnel with an indication of the type of failure that was detected. However this information may be out of date by the time it is received by the service personnel and it may also not contain the full information provided by the ATM because the data received by the remote management system is typically transformed into a new format for conveying to the service personnel.

It would be advantageous if the service personnel could obtain up to date information about errors in an ATM and also at least as much information as the ATM provided to the remote management system. This would avoid service personnel making an unnecessary site visit to an ATM that rectified itself subsequent to sending a fault message to the remote management system. By being able to check the more detailed ATM status information a service person would be able to obtain any required part to fix a problem with an ATM prior to a site visit.

Accordingly the invention generally provides methods systems apparatus and software for managing networked devices.

In addition to the Summary of Invention provided above and the subject matter disclosed below in the Detailed Description the following paragraphs of this section are intended to provide further basis for alternative claim language for possible use during prosecution of this application if required. If this application is granted some aspects of the invention may relate to claims added during prosecution of this application other aspects may relate to claims deleted during prosecution other aspects may relate to subject matter never claimed. Furthermore the various aspects detailed hereinafter are independent of each other except where stated otherwise. Any claim corresponding to one aspect should not be construed as incorporating any element or feature of the other aspects unless explicitly stated in that claim.

According to a first aspect there is provided a self service terminal comprising a customer transaction module operable to i implement a function associated with a customer transaction and ii provide status information relating to the module a terminal controller coupled to the customer transaction module and including i a management component for retrieving status information from the customer transaction module and ii a Web services interface for providing access to the retrieved status information to a remote device and a network connection coupled to the controller to provide a remote device with access to the Web services interface.

As used herein a Web service means a software system designed to support interoperable machine to machine interaction over a network. A Web service has an interface described in a machine processable format specifically a Web Services Description Language WSDL . Other systems interact with the Web service in a manner prescribed for example using SOAP Simple Object Access to Protocol messages typically conveyed using HTTP Hyper Text Transfer Protocol with an XML eXtensible Mark up Language serialization in conjunction with other Web related standards. The source of this definition is http www.w3.org TR ws gloss .

The remote device may be a portable computer such as a personal digital assistant PDA or a cellular radiofrequency telephone cellphone carried by service personnel. Provided the remote device has Web access and the device and or user has any necessary security clearance or authorization it can be used to obtain status information directly from the Web services interface without having to go through the remote management system.

The self service terminal may comprise a plurality of customer transaction modules. Customer transaction modules may include a card reader motorized dip or swipe a media dispenser cash voucher ticket or the like a media depository checks banknotes coins slips tickets vouchers or the like a printer receipt statement or the like a PIN entry device encrypting keypad encrypting touch sensitive panel or the like or the like.

The self service terminal may comprise a plurality of service personnel modules such as a journal printer a service operator panel or the like.

The terminal controller may execute a platform including an operating system for controlling the customer transaction modules and any service personnel modules.

The self service terminal may be an automated teller machine ATM an information kiosk a financial services center a bill payment kiosk a lottery kiosk a postal services machine a check in and or check out terminal such as those used in the retail hotel car rental gaming healthcare and airline industries.

According to a second aspect there is provided a self service terminal comprising a media dispense module operable to implement a media dispense function and including i a processor executing a a management component operable to obtain status information relating to the media dispense module and b a Web services interface for providing access to the obtained status information to a remote device and ii a network connection for communicating directly with a remote transaction controller and a media deposit module operable to implement a media deposit function and including i a processor executing a a management component operable to obtain status information relating to the media deposit module and b a Web services interface for providing access to the obtained status information to a remote device and ii a network connection for communicating directly with a remote transaction controller.

The network connections may comprise dedicated network cards for each module. Alternatively the network connections may be provided by dedicated communication stacks each communication stack being associated with a serial port such as a USB port to provide the transport layer and a single network card used by the serial ports.

Using dedicated network cards or the like allows a self service terminal to operate as an ultra thin client with each module communicating with the remote transaction controller directly instead of with a controller within the self service terminal.

Using a serial bus such as USB allows a single network card to be used but this means that the modules all rely on the single network card for external communication so any hardware fault with this single network card will leave the modules without any communication link.

According to a third aspect there is provided a distributed self service terminal comprising customer transaction modules at a first location and a transaction controller at a second location remote from the first location the customer transaction modules including a media dispense module operable to implement a media dispense function and including i a processor executing a a management component operable to obtain status information relating to the media dispense module and b a Web services interface for providing access to the obtained status information to a remote device and ii a network connection for communicating directly with the remote transaction controller and a media deposit module operable to implement a media deposit function and including i a processor executing a a management component operable to obtain status information relating to the media deposit module and b a Web services interface for providing access to the obtained status information to a remote device and ii a network connection for communicating directly with the remote transaction controller.

The remote transaction controller may control a plurality of media dispense modules each media dispense module being located in a different geographical location. For example each media dispense module may be more than one kilometer from the other media dispense modules.

The remote transaction controller may control a plurality of media deposit modules each media deposit module being located in a different geographical location. For example each media deposit module may be more than one kilometer from the other media deposit modules.

Some distributed self service terminals may only include media dispense modules. Other distributed self service terminals may only include media deposit modules.

This aspect of the invention enables a single controller to control a plurality of different customer fulfillment stations each customer fulfillment station being geographically remote from the other customer fulfillment stations.

According to a fourth aspect there is provided a method of providing access to management information relating to a self service terminal the method comprising receiving a request for management information from a remote device via a Web Service executing on a controller within the self service terminal translating the request to a format compatible with a management component executing on the self service terminal retrieving the requested management information from a module within the self service terminal via the management component and providing the requested management information to the remote device.

The method may include the further step of requiring a request for information via the Web Service to fulfill a security criterion.

The security criterion may include the request for information i originating from a known source for example a registered IP address and or ii including a correct username and passcode combination and or iii originating from a person registered to receive the type of information requested.

According to a fifth aspect there is provided a method of providing access to management information stored in a self service terminal the method comprising receiving from a remote device a request for management information in a format compatible with a Web services interface ascertaining if the received request fulfils a security criterion transforming the received request into a different format in the event that the request does fulfill the security criterion communicating the transformed request to a device manager receiving a response from the device manager transforming the response into a format compatible with a Web services interface and relaying the transformed response to the remote device.

The different format may be a CEN XFS format an OPOS format a CUSS format a proprietary format or any other convenient format.

These aspects of the invention have the advantage of allowing service personnel to query a self service terminal directly for example via a Web browser on a portable device to obtain status information that is up to date and without loss of information as a result of having to change the format of the status information. By using Web services it is possible to view the same information on remote devices computers cellular telephones and the like having different operating systems without having to write a dedicated client application for each device.

These and other aspects will be apparent from the following specific description given by way of example with reference to the accompanying drawings.

Reference is first made to which is a simplified block diagram of a self service terminal in the form of an ATM according to one embodiment of the present invention.

The ATM comprises a plurality of modules for enabling transactions to be executed and recorded by the ATM . These ATM modules include customer transaction modules and service personnel modules. The ATM modules comprise an ATM controller a customer display a card reader writer module an encrypting keypad module a receipt printer module a cash dispenser module a journal printer module for creating a record of every transaction executed by the ATM a network connection module for accessing a remote authorization system not shown via an IP network and an operator panel module for use by a service operator such as a field engineer a replenisher of currency of printer paper or the like or the like .

Some of the customer transaction modules such as the ATM controller are also used by the service personnel for implementing management functions. However some of the modules are referred to herein as service personnel modules such as the journal printer module and the operator panel module because they are never used by ATM customers.

Reference will now also be made to which is a simplified block diagram of the ATM controller module of the ATM . The controller module comprises a BIOS stored in non volatile memory a microprocessor associated main memory used by the microprocessor storage space in the form of a magnetic disk drive and a display controller in the form of a graphics card. The graphics card controls the customer display and the display portion of the operator panel module .

In use the main memory is loaded with a platform including an ATM operating system kernel and drivers for the modules in the ATM an ATM application a Web services interface and a management agent in the form of an SNMP simple network management protocol agent .

The platform monitors the condition of each module within the ATM state of health monitoring and stores status information relating to the modules such as logs and tallies of module activity.

The ATM application is responsible for controlling the operation of the ATM . In particular the ATM application provides the sequence of screens used in each customer transaction referred to as the transaction flow and obtains authorization for transactions from a remote transaction authorization system not shown . The ATM application also provides a sequence of screens on the operator panel module for service personnel who are maintaining replenishing or otherwise operating on the ATM .

The management agent monitors the status information relating to the modules in the ATM and sends a message to a remote management centre not shown if the status of certain components within the modules change. This type of message is typically referred to as a trap or an event and is asynchronous. The SNMP agent can also provide status information in response to a request from the remote management centre not shown .

The ATM application the Web services interface and the SNMP agent communicate with the platform via a CEN XFS interface. CEN is the European Committee for Standardization and XFS is the eXtensions for Financial Services standard. XFS eXtensions for Financial Services is an industry standard protocol for communicating financial information. The current version of this CEN XFS standard is the CEN XFS v.3.10 specification which can be downloaded from ftp ftp.cen.eu PUBLIC CWAs other WS XFS CWA15748 . This lists the format and structure of the commands features and device classes that comply with the XFS standard.

The platform includes an XFS manager that receives XFS commands from the ATM application and routes these commands to service providers not shown associated with the appropriate modules for operating on the received XFS command. The XFS manager and the service providers together illustrated in as ellipse form a management component for retrieving management information from the modules in the ATM .

The Web services interface accesses a WSDL Web Services Description Language file that includes information about the type of requests that the Web services interface can supply and the format needed to submit those requests. In this embodiment the WSDL file includes commands corresponding to the complete set of CEN XFS commands although not necessarily in the same format as the CEN XFS commands because the CEN XFS commands assume that a C interface is used. By providing corresponding but different commands the Web services interface can receive commands that are not compliant with a C interface. The Web services interface includes an interface to the platform that complies with the CEN XFS interface so it can convert a received command to the corresponding CEN XFS command. The Web services interface therefore provides a new set of commands that it can convert to CEN XFS commands and convey to the XFS Manager.

In this embodiment the Web services interface can be accessed via a dedicated Web page that can be loaded into a Web browser. The dedicated Web page includes predefined commands conforming to the format provided by the WSDL file .

As the platform receives status information from the various modules within the ATM the platform may store this information.

In addition to storing status information the platform can also query the status of devices dynamically through their service provider interfaces to check their status prior to attempting to carry out a command. The platform can also receive asynchronous events unsolicited from the service provider when something changes and is reported through an event. In response to such an asynchronous event the Web services interface would cause the platform to query the service provider not shown separately to retrieve the information required to obtain the current device state information.

Reference will now be made to which is a block diagram illustrating an ATM network including two ATMs which can be considered to be identical for the purpose of this description a transaction authorization system remote from the ATMs a management system which is also remote from the ATMs and a portable device in the form of a cellphone carried by a service person and used to access data from the ATMs .

The cellphone accesses the ATM modules via the Web services interface as will now be described with reference to which is a flowchart illustrating steps implemented by the ATM in providing access to data from the ATMs .

Initially the remote management system may receive a trap from the SNMP agent indicating that there is a fault with for example the receipt printer module . The remote management system then forwards a notification by SMS messaging to a service person carrying the cellphone that the ATM is experiencing problems with the receipt printer module . This SMS message is received by the cellphone and displayed to the service person.

The service person then uses a Web browser executing on the cellphone to access a URL Uniform Resource Locator associated with the Web services interface and hosted by the ATM controller . The URL retrieves content that is customized for navigation by devices having small displays such as cellphone .

The Web service interface receives this request step and prompts the service person to enter a valid username and passcode combination step to fulfill a security criterion. If an invalid username and passcode combination is entered then the Web service interface denies access to the service person step . If a valid username and passcode combination is entered then the Web service interface provides the cellphone s Web browser with a set of selectable options step .

These selectable options include performing status requests on modules within the ATM . In this example the service person requests the current status of the receipt printer module . The Web service interface receives this request transforms the request into CEN XFS format and communicates the transformed request to the platform step .

The platform specifically the XFS manager in the platform sends the request to the appropriate service provider not shown separately and receives a response which it communicates to the Web service interface . The Web service interface receives this response step which it transforms and sends to the Web browser step on the cellphone .

The service person can then review the status of the receipt printer module and decide whether it is necessary to visit the ATM or not. For example the ATM may have reset the receipt printer module causing the fault to be rectified in which case the service person may not need to make a site visit to the ATM . If the service person decides to visit then he she may ascertain if a part of the receipt printer module is likely to be faulty and may bring a spare part for the receipt printer module or a replacement receipt printer module .

Another embodiment of the present invention will now be described with reference to which is a block diagram of a distributed self service terminal system . The distributed self service terminal system is in the form of a distributed ATM system .

The distributed ATM system comprises a network ATM controller coupled to a plurality of customer fulfillment terminals by an IP network and also coupled to a transaction authorization system .

Each customer fulfillment terminal comprises a customer display a card reader writer module an encrypting keypad module a receipt printer module a cash dispenser module and a journal printer module for creating a record of every transaction executed by the customer fulfillment terminal .

Each of these modules to includes a dedicated network connection which enables each module to communicate directly with the network ATM controller and a dedicated Web services interface. However these components are only illustrated for one representative module the cash dispense module as shown in .

Reference will now be made to which is a block diagram illustrating the cash dispense module in more detail.

The cash dispense module comprises a pick unit for picking banknotes from an inserted currency cassette loaded with banknotes a presenter unit for presenting picked banknotes to a customer a dispenser controller for controlling the operation of the cash dispense module and a network connection having a unique IP address. The dispenser controller includes a Web services interface which communicates with the network ATM controller .

In use when a customer inserts a card into the card reader writer module then the card reader writer module reads details from the inserted card and communicates these read details in encrypted form to the network ATM controller via the network connection not shown within the card reader writer module .

On receiving these details the network ATM controller instructs the encrypting keypad module via the Web services interface not shown to receive a PIN from the customer to encrypt the received PIN and to communicate the encrypted PIN back to the network ATM controller via the encrypting keypad s network connection not shown .

The network ATM controller also instructs the encrypting keypad module via the Web services interface not shown to receive a transaction request from the customer in this example a cash dispense request and to communicate this received transaction request back to the network ATM controller via the encrypting keypad s network connection not shown .

The network ATM controller then obtains authorization for this transaction from the transaction authorization system . If approved the network ATM controller instructs the dispenser controller in the cash dispense module via the network connection and the Web services interface to dispense the requested amount of cash. Once this has been completed and the customer has removed the presented banknotes then the dispenser controller notifies the network ATM controller that the customer has taken the cash.

On receiving this notification the network ATM controller instructs the card reader writer module via its network connection and Web services interface neither of which is shown to eject the customer s card for retrieval by the customer thereby concluding the transaction.

Since each module includes its own network connection and Web services interface a service person and or a management centre may access management information stored on each module by sending a request to the Web service interface for that module. This may be implemented simultaneously with a customer transaction. This allows a service person to check the status of a module or information relating to module usage without having to visit the ATM. For example a service person may query a module where the module has a Web services interface or the ATM where the ATM has a Web services interface to obtain the number of print operations performed by a printer since the print head was last changed the number of pick operations performed by a pick unit within a dispense module since the pick unit was last serviced the amount of receipt paper remaining in a printer or the like.

It should now be appreciated that these embodiments have the advantage that an interface compatible with Web technologies can be used to provide access to to information usually retrieved using an interface requiring a specific programming language to be used such as C or C . This enables a new interface to be provided that is dislocated from the original SST or module interface.

By allowing a service person to retrieve information directly from the SST in real time up to date information is available that is not diluted or truncated by subsequent data transformation.

By providing modules with common Web service interfaces it is easier and less expensive to integrate these modules into SSTs.

By using Web services client applications can be provided for execution by Web browsers so that the same client can be used on different platforms different operating systems and the like.

By using Web services as a layer above the XFS Manager conventional applications can still communicate directly with the XFS Manager to control the ATM without requiring any changes to these conventional applications.

Various modifications may be made to the above described embodiments within the scope of the invention for example in other embodiments instead of using a Web browser as the presentation client on a portable device a customized client could be provided. The customized client could include additional security requirements and may have a richer graphical interface.

In other embodiments a management agent other than an SNMP agent may be used. For example Windows Management Instrumentation WMI may be used a proprietary management agent may be used or the like.

In the above embodiments the Web services interface supports CEN XFS commands whereas in other embodiments the Web services interface may support OPOS a retail industry standard CUSS a travel industry standard a proprietary application programming interface API such as the NCR trade mark Device Status Manager or any other convenient protocol or standard.

In the above embodiments the Web services interface supports financial industry terminals whereas in other embodiments a single application may be provided that can access and obtain state of health information from terminals used in the financial retail gaming healthcare and travel industries. Since each terminal provides a Web services interface each terminal can translate generic commands to the specific command format used in that industry.

In other embodiments multi level role based security with different levels of access may be provided using the Web services interface. For example replenishers accessing consumable stock levels may have one level of access whereas cash in transit CIT personnel accessing cash levels may have a different level of access and engineers accessing device status values and executing commands such as remote reboot may have a third level of access.

In other embodiments a different security criterion may be implemented to that described above. For example X509 certificates biometric recognition or validation or the like. These could be used to authenticate a service person such as an engineer to the Web service interface .

The steps of the methods described herein may be carried out in any suitable order or simultaneously where appropriate. The methods described herein may be performed by software in machine readable form on a tangible storage medium or as a propagating signal.

The terms comprising including incorporating and having are used herein to recite an open ended list of one or more elements or steps not a closed list. When such terms are used those elements or steps recited in the list are not exclusive of other elements or steps that may be added to the list.

