---

title: Secure command method and device for remote maintenance terminal
abstract: A method executes at least one instruction in an on-board maintenance device from a remote system connected to the maintenance device via a communication network. The method includes receiving at least one datum representative of at least one command having a correspondence with the at least one instruction. The method also includes filtering the at least one received datum. In response to the filtering, if the at least one received datum represents a valid command, the method includes converting the at least one received datum to identify the at least one instruction.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08244413&OS=08244413&RS=08244413
owner: Airbus Operations SAS
number: 08244413
owner_city: Toulouse
owner_country: FR
publication_date: 20090116
---
The present invention relates to maintenance operations and functional tests performed in aircraft and more particularly to a secure command method and device for a remote maintenance terminal so that functional tests on the assembly line or during operation of an aircraft can be carried out from a remote station.

To optimize the reliability of aircraft and increase their profitability on line maintenance operations are frequently performed between the flying phases.

In general such operations for maintenance operators for example consist in analyzing data stored in memory during flight in modifying certain parameters of the aircraft or certain software data and or in launching test software applications. The analyzed data are often obtained from transducers and stored in memory in a central diagnostic and storage device accessible via a man machine interface of MCDU type initials for Multi Control Display Unit in English terminology or of OMT type initials for Onboard Maintenance Terminal in English terminology . This interface via which interactive operations can be launched makes it possible to analyze data stored in memory to access parameters of the aircraft and more generally to execute test and maintenance functions. By way of illustration the Airbus A320 A330 and A340 are equipped with MCDUs and the Airbus A380 is equipped with an OMT Airbus A320 A330 A340 and A380 are trademarks .

Access to aircraft maintenance systems is generally limited to fixed physical stations provided on board in the cockpit. Thus when the aircraft is on the ground a maintenance operator can board the aircraft to access and analyze the data stored in memory to modify the parameters thereof if necessary and to launch test applications.

In order to optimize task sequencing the current devices generally require the ongoing presence of an operator in order to verify that the operations have taken place properly.

Similarly during aircraft assembly the teams of the final assembly sequences rely on interactive maintenance tools to perform all or part of the functional tests of the airplane.

However despite the performances of the maintenance stations means for automating certain tests do not exist.

In fact although certain maintenance stations provided on board aircraft can be connected to a communication network for exchange of data between the aircraft and remote equipment the network connection does not permit remote control of the applications implemented on board the aircraft or transmission of applications for security reasons.

The object of the invention is therefore a method for executing at least one instruction in an on board maintenance device from a remote system connected to the said maintenance device via a communication network this method comprising the following steps 

receiving at least one datum representative of at least one command associated with the said at least one instruction 

Thus a vehicle such as an aircraft adapted to employ the method according to the invention has at its disposal means for accessing the interactive maintenance tools remotely without reducing its level of security. In addition such a method offers optimized service to the operators of final assembly sequences for the conduct of functional tests by providing the possibility of developing means for automating tests.

In addition since the operators are able to connect a mobile terminal and to use all or some of the automatic test routines the method according to the invention offers the possibility of performing non regression functional tests on the production flow up to delivery.

Advantageously the method additionally comprises a step of verifying a signature of the said at least one received datum permitting authentication thereof.

According to a particular embodiment the method additionally comprises a preliminary step of storing in memory the said correspondence between the said at least one datum and the said at least one instruction.

Advantageously the said filtering step is an iterative filtering step based on at least two distinct criteria for optimizing the processing times.

According to a particular embodiment at least one of the said at least two criteria is associated with the protocol for transmission of the said at least one datum. Similarly according to a particular embodiment at least one of the said at least two criteria is related to the encoding of the said at least one datum representative of the said at least one command.

Advantageously the method additionally comprises a step of transmitting at least one information item related to execution of the said at least one instruction making it possible to transmit a result in response to a command. Preferably to permit authentication of the said at least one information item the method additionally comprises a step of signing the said at least one information item.

Another object of the invention is a device comprising means adapted to employment of each of the steps of the method described in the foregoing as well as an aircraft comprising such a device.

Device for example is connected to control transducers not illustrated of the engines and actuators of the landing gear and control surfaces.

An on line remote maintenance station located in a maintenance center for example is connected to device by a communication network and port .

Thus when aircraft is on the ground during assembly or operation thereof a maintenance operator is able by means of remote station to analyze the data of the aircraft to modify the parameters thereof and or to monitor the execution of maintenance application modules implemented in aircraft .

In addition to its standard functions device comprises means for employing the invention that are advantageously based on a software architecture comprising substantially the three following modules which may be implemented within a single software application or in the form of independent modules 

According to the first example illustrated in the software architecture adapted for employment of the invention is implemented in the maintenance device. As illustrated maintenance device in this case comprises maintenance application modules . Although all of these modules are represented here in the form of a single element it must be understood that in general they are separate modules. The maintenance application modules are connected to the network in order to receive and or transmit data.

Maintenance device additionally comprises a communication module a filtering module and a conversion module . Communication module is preferably a secure communication module.

Communication module is connected to the network via a standard link such as an Ethernet link for receiving and or transmitting data. Such a link may be hard wired or wireless. Communication module is also connected to filtering module which in turn is connected to conversion module .

According to the second example illustrated in the software architecture adapted for employment of the invention is implemented in a device separate from the maintenance device. As illustrated maintenance application modules are implemented in a maintenance device separate from device comprising communication module filtering module and conversion module .

The purpose of communication module or is to receive the data transmitted via the network to which it is connected and to transmit data over this same network.

Advantageously the exchanged data are signed. It is recalled here that the signature makes it possible to authenticate the source of a datum as well as the integrity of data.

In complementary manner it is possible to encipher the data in order that they are comprehensible only to the recipient.

According to a particular embodiment the communication module and the remote station each comprise keys for adding a signature to the transmitted data and for verifying such a signature. In this way it is possible to authenticate the data source and to verify that the exchanged data are correct and reliable.

The signature mechanisms employed are preferably standard algorithms based on hash functions such as the MD5 or SHA 1 algorithms.

The purpose of filtering module or is to filter the data received from the network in order to transmit only the correctly formatted data to the conversion module meaning that only the information items comprehensible to the conversion module are transmitted thereto.

The filtering module is preferably based on the screen principle or in other words on an interactive mechanism according to which a plurality of filter levels is used to optimize the processing time. It is therefore composed of a plurality of elements for progressively finer filtration of the received data in order to pass only the data corresponding to valid commands generated by remote stations.

The filtering module requires that a command format be defined so that only a certain type of network frames is processed. The format and the associated transport protocol may be defined in the form of parameters accessible to the filtering module. For example such parameters may specify that the commands are received in the form of Ethernet frames indicate the sources authorized to transmit such commands impose a maximum frame lifetime beyond which the frames are no longer considered and indicate the characters that can be validly used to encode a command in a frame.

Firstly each frame is analyzed by verifying for example the physical source and destination addresses and respectively especially the MAC addresses acronym for Media Access Control in English terminology the protocol type and the signature of the complete frame. The data of the frame are not analyzed in this first step.

If the physical source and destination addresses and respectively the protocol type and the signature are not in conformity with the parameters of the filtering module the frame is rejected.

In contrast if the physical source and destination addresses and respectively the protocol type and the signature are in conformity with the parameters of the filtering module a second filtering step is performed.

It should be noted here that the first filtering step may be applied to data other than those cited or else to fewer data.

The second step consists for example in analyzing the data header . In particular this second filtering step may consist in verifying the IP version initials for Internet Protocol in English terminology the header length the service type the total data length the identification used to reconstitute the fragments the lifetime also known as TTL initials for Time To Live in English terminology the protocol and the source and destination addresses and respectively.

Once again if not all of these information items are in conformity with the parameters of the filtering module the frame is rejected. In contrast if all of these information items are in conformity with the parameters of the filtering module a third filtering step is performed.

It should be noted here also that the second filtering step may be applied to data other than those cited or else to fewer data.

The third step consists in this case of analyzing the characters of the useful data of the frame. This step therefore makes it possible to verify that the characters necessary for construction of the command cannot be used to construct the executable code. Advantageously all the characters of the useful data must be chosen from the ASCII table within the values between 032 and 090 as illustrated in .

If a character of the useful data does not belong to the values between 032 and 090 of the ASCII table the frame is rejected. On the other hand if all of the characters of the useful data belong to the values between 032 and 090 of the ASCII table the frame is transmitted to conversion module or .

Naturally the third filtering step may be applied to other criteria especially to more restrictive criteria.

The purpose of conversion module or is to establish an interface between the application modules of the maintenance device and the network.

This module is preferably developed in such a way that only the commands linked to instructions corresponding to types of applications hosted on the maintenance software platform of the aircraft will have any action. This means that this module knows the instructions that may be executed by each application. In other words a list of instructions or instruction sequence is preferably stored in memory beforehand. Such a list defines a set of configurations of possible strings of instructions. This list may also define the prohibited combinations.

This configuration is constructed in such a way that the string of instructions of an application is known a priori. This permits the conversion module to verify that the commands that it receives and the string of associated instructions is in conformity with what the application is supposed to execute. This verification permits the conversion module to reject any unexpected string and thus ensures that dangerous operations cannot be executed.

In a particular embodiment the conversion module uses a table of correspondence between the command names and the effective functions or in other words instruction sequences in order to associate one or more instructions with the names of commands received from the remote station. It should be noted here that the instructions may assume a plurality of forms. They may be for example pointers directed at functions or else commands interfaced with the operating system of the maintenance device. The instructions make it possible in particular to simulate an action entered by a user via the interface of the maintenance device.

Correspondence table in this case comprises two columns one column containing the command names and one column containing the list of instructions associated with each command.

Row illustrates an example of a command to test a flight management device known as FMU initials for Flight Management Unit in English terminology . The name of the command that can be used by a maintenance operator from a remote station in this case is TEST FMU. As illustrated this command corresponds to execution of the instruction sequence comprising the instructions Set Param a b c AutoTest FMU and AutoTest FMU.

After a command has been analyzed and declared to be in conformity the conversion module transmits the corresponding instructions to the application in question. The application executes the instructions and in general returns a response. This response is received by the conversion module which constructs a response message preferably signed.

By way of illustration and returning to the example illustrated in the mode of operation for execution of instructions corresponding to the TEST FMU command is the following 

the sequence of instructions corresponding to the filtered command is identified being in this case the instructions Set Param a b c AutoTest FMU and AutoTest FMU 

these instructions are transmitted by a software layer of API type initials for Application Programming Interface in English terminology to the intended applications as if the command had been generated by keystrokes at a fixed station 

the applications in question execute the instructions according to the command and transmit the results to the conversion module via the software layer of API type and

the conversion module forms a response message for example by constructing a screen page or part of a screen page comprising the results signs the response message to attest as to the origin and integrity of the information furnished and transmits the response message to the remote station via the communication network.

It is also possible in the case of automatic tests to use a software application implemented in the remote station to generate a string of commands in order to create a complete test scenario.

After data that may correspond to one or more names of commands have been received step the signature of the received data is verified step according to a standard algorithm. The validity of the data is then tested step . If the data are valid a filtering step is performed step and a new validity test is performed step . If the data are valid the instructions corresponding to the data are identified step .

The identified instructions are then executed by the associated applications step and the result of execution of these instructions is formulated and signed step before being transmitted to the remote station step .

A device adapted for employment of the invention or part of the invention is illustrated in . Device is for example a calculator or a microcomputer.

a permanent memory ROM the acronym for Read Only Memory in English terminology which may be provided with the programs Prog Prog and Prog 

a volatile memory or cache memory RAM the acronym for Random Access Memory in English terminology which is provided with registers capable of recording variables and parameters created and modified in the course of execution of the aforesaid programs and

a screen for visualizing data and or for acting as a graphical interface with the user who will be able to interact with the programs according to the invention by means of a keyboard and of a mouse or of another pointing device such as a light pen a touch screen or a remote controller 

a hard disk which can be loaded with the aforesaid programs Prog Prog and Prog and with processed data or data to be processed according to the invention and

a memory card reader capable of receiving a memory card and reading or writing therein processed data or data to be processed according to the invention.

The communication bus permits communication and interoperability between the different elements included in device or connected thereto. The representation of the bus is not limitative and in particular the central unit is capable of communicating instructions to any element of device directly or via another element of device .

The executable code that in each program permits the programmable device to employ the process according to the invention may be stored for example on hard disk or in read only memory .

According to one variant memory card may contain data especially signature keys as well as the executable code of the aforesaid programs which code will be stored on hard disk once it has been read by device .

According to another variant it will be possible for the executable code of the programs to be received at least partly via interface to be stored in a manner identical to that described in the foregoing.

More generally it will be possible for the program or programs to be loaded into one of the storage means of device before being executed.

Central unit will command and direct the execution of the instructions or portions of software code of the program or programs according to the invention which instructions are stored on hard disk or in read only memory or else in the other aforesaid storage elements. During boot up the program or programs stored in a non volatile memory such as hard disk or read only memory are transferred into random access memory which then contains the executable code of the program or programs according to the invention as well as registers for storing in memory the variables and parameters necessary for employment of the invention.

The communication apparatus containing the device according to the invention may also be a programmed apparatus. This apparatus then contains the code of the computer program or programs resident for example in an application specific integrated circuit ASIC .

It should be noted that the maintenance application modules just as all software applications installed on board in aircraft are developed in accordance with strict aeronautical standards which make it possible to guarantee a certain level of security and to demonstrate a level of prediction of the behavior of the system.

By way of illustration the hosting platform of the maintenance application modules for which the desired software quality assurance level is DAL C may be developed in such a way that the level of control of the on board code ensures in particular the integrity of the generated information items as an example the hosting platform is developed according to the DO 178B aeronautical standard .

Thus the employment of the invention in such a context makes it possible to guarantee a certain level of integrity of the data and results transmitted to the remote station.

Naturally to satisfy specific needs a person skilled in the art of the invention will be able to apply modifications in the foregoing description.

