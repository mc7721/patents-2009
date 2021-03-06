---

title: Methods and systems for inter-processor communication under a multiprocessor environment
abstract: A method is provided for sending and receiving data between a first processor including a first cache memory and a second processor including a second cache memory via a shared memory. The method includes classifying, by the first processor, a transfer data area that stores data transferred between the first and second processors in the shared memory as a first area filling one cache line and a second area not filling one cache line, copying, by the first processor, data in the second area into a divided data area in the shared memory, the divided data area being aligned with a cache line in the first cache memory, and processing, by the second processor, the data in the first area and the data in the divided data area as data from the first processor.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08504781&OS=08504781&RS=08504781
owner: Canon Kabushiki Kaisha
number: 08504781
owner_city: Tokyo
owner_country: JP
publication_date: 20091012
---
The present invention relates to an inter processor communication technology under a multiprocessor environment.

There is a communication offload technology for executing communication processing by a main processor and another processor to advance high speed communication processing and load reduction. In such a multiprocessor processing a shared memory is arranged between the processors and communication is performed between the processors via the shared memory.

For example a shared memory is arranged between a main system on the main processor side in which an application is operated and a subsystem on the communication offload processor side. The main processor writes transfer data into the shared memory and delivers address information in a memory area where the transfer data is written to the communication offload processor by inter processor communication. The communication offload processor reads the transfer data using the delivered address information and executes sending and receiving processing to an external device.

When the multiprocessing system executes data transfer between the processors via the shared memory the system is required to suitably process data cached in a cache memory included in each processor. If the system does not suitably process to write the data cached in the cache memory into the shared memory there is a possibility that the data in the shared memory is overwritten so that the system cannot be normally operated.

For example a cache memory having a configuration having a plurality of cache lines having a fixed length e.g. 32 byte length is considered. In such a cache memory when data cached in the cache memory of each processor is written into a shared memory a system needs to perform control so that other data does not exist on the cache lines to be written. This is because a cache writing operation is performed per cache line. If this restriction is not protected the cache writing operation overwrites the other data area existing on the same cache line. In order to prevent this overwriting it is necessary that an application prepares data in which a transfer data writing area in a shared memory is aligned with a cache line in a cache memory or processes to copy the data to an aligned area. Such processing becomes complicated. Further a conventionally used application not having such processing is inapplicable for a multiprocessor environment as it is.

Further when the system transfers data between processors via a shared memory it can be also considered that a cache function is made to be turned off.

However when the cache function is made to be completely turned off the performance of the system decreases and communication throughput decreases greatly.

Japanese Patent Application Laid Open No. 8 305633 and U.S. Pat. No. 6 466 988 Japanese Patent Application Laid Open No. 2000 194680 discuss a data transfer system using a shared memory under a multiprocessor environment.

The system discussed in Japanese Patent Application Laid Open No. 8 305633 performs an operation for invalidating data corresponding to a reference area cached in a cache memory included in a self processor when the system refers to a data area belonging to another processor. The system discussed in U.S. Pat. No. 6 466 988 Japanese Patent Application Laid Open No. 2000 194680 automatically synchronizes content of a cache memory included in each processor by including a coherence function in a cache memory on the system.

As for aforementioned description complicated processing is necessary for preventing overwriting data in a shared memory. Further there is a possibility that a conventionally used application that is not a multiprocessor system is inapplicable to the multiprocessor environment as it is.

The present invention is directed to a method capable of applying an application to a multiprocessor environment without conscious of alignment to a cache line in a transfer data area in the application.

According to an aspect of the present invention a method is provided for sending and receiving data between a first processor including a first cache memory and a second processor including a second cache memory via a shared memory. The method includes classifying by the first processor a transfer data area that stores data transferred between the first and second processors in the shared memory as a first area filling one cache line in the first cache memory and a second area not filling one cache line copying by the first processor data in the second area into a divided data area in the shared memory the divided data area being aligned with a cache line in the first cache memory and processing by the second processor data in the first area and data in the divided data area as data from the first processor.

According to another aspect of the present invention a method is provided for sending and receiving data via a shared memory between a first processor including a first cache memory and a second processor including a second cache memory. The method includes classifying by the first processor a transfer data area that stores data transferred between the first and second processors in the shared memory as a first area filling one cache line in the first cache memory and a second area not filling one cache line securing by the first processor a divided data area aligned with a cache line in the first cache memory in the shared memory writing by the second processor data transferred between the first and the second processors into the first area and the divided data area in the shared memory and processing by the first processor data written into the first area and the divided data area in the shared memory as data from the second processor.

Further features and aspects of the present invention will become apparent from the following detailed description of exemplary embodiments with reference to the attached drawings.

Various exemplary embodiments features and aspects of the invention will be described in detail below with reference to the drawings.

As for exemplary embodiments a communication offload system which processes communication processing of a layer lower than a transmission control protocol internet protocol TCP IP by a communication offload processor and reduces load of an application processor is described.

The system of the present exemplary embodiment is a communication apparatus connecting with an external communication apparatus via a wired local area network LAN or a wireless LAN and capable of performing a TCP IP packet communication with the communication apparatus .

The communication apparatus is a multiprocessor system including an application processor and a communication offload processor .

The application processor is a first processor used for processing a server message block SMB a mail application and the like. The application processor functions as a main processor of the communication apparatus .

The communication offload processor is a second processor used for processing TCP IP a communication driver and the like. The communication offload processor functions as a sub processor of the communication apparatus . That is the communication offload processor bears communication processing of a layer lower than the TCP IP so that load of the application processor can be reduced.

A shared memory is a memory capable of being referred to and written from both the application processor and the communication offload processor .

A cache memory is a first cache memory of the application processor and includes a plurality of cache lines having 32 byte length. For example a whole capacity of the cache memory is 1 MB. The application processor can write receive data into from the shared memory by writing receiving data into from the cache memory .

A cache memory is a second cache memory of the communication offload processor and includes a plurality of cache lines having 32 byte length. For example a whole capacity of the cache memory is 1 MB.

The communication offload processor can write receive data into from the shared memory by writing receiving data into from the cache memory . When writing receiving data into from the shared memory are performed via the cache memories and an area corresponding to an area used in the shared memory is secured in the cache memories and . That is the same area is secured in the cache memories and and the shared memory and data written into a predetermined area in a cache memory by the processor is written into a corresponding area in the shared memory. In the case of reading when the processor reads data in the predetermined area in the shared memory the processor writes the read data into the corresponding area in the cache memory and processes the data.

An interrupt control circuit controls an interrupt signal to the communication offload processor and an interrupt signal to the application processor . A user interface is an interface for performing a user operation and result outputting a display or the like . A communication interface sends and receives data via the wired LAN or the wireless LAN .

Here the application processor and the communication offload processor are operated by an individual operating system OS and each OS may have the same type or a different type. A general Berkeley software distribution BSD socket application programming interface API is mounted on the application processor side and an entity of the socket is mounted on the communication offload processor side. Each processing below is executed based on processing of the OS of each processor. However each processor may include a hard configuration unit for executing each processing. For example in the processing in each processor may include a hard configuration for executing each step in .

The shared memory can be divided into a cache area and a non cache area. In order to simplify the description the cache area and the non cache area are set to have the same arrangement when seeing from the application processor and the communication offload processor .

The application processor can send an interrupt signal to the communication offload processor . Similarly the communication offload processor can send an interrupt signal to the application processor .

The interrupt signal may be connected so as to enable to directly transmit to a partner processor or the interrupt control circuit may be arranged for relaying the interrupt signal.

The following is a processing when a user operates the user interface of the communication apparatus and transfers data to the communication apparatus . The application processor performs writing data into the shared memory and reading data from the shared memory via the cache memory . Further the communication offload processor performs writing data into the shared memory and reading data from the shared memory via the cache memory . That is when these processors write data into the shared memory a content of the cache memory or is reflected to the shared memory . Further when these processors read data from the shared memory a content of the shared memory is reflected to the cache memory or .

In transfer data preparation step S the application processor prepares transfer data on the shared memory in an application layer. An area where the transfer data is prepared is made to be a transfer data area.

In SEND call step S the application processor causes a pointer in the transfer data area to be one of arguments and calls SEND which is one of a socket API.

In additional information preparation step S the application processor secures an additional information area in the non cache area on the shared memory . The application processor uses the additional information area as an argument information area for delivering other argument information of the SEND to the communication offload processor and a return value area for receiving a return value from the communication offload processor .

In alignment analysis step S the application processor subjects the transfer data area and the cache line in the cache memory to an alignment analysis. The transfer data on the shared memory is set in the transfer data area. The application processor classifies the transfer data area into an area A a first area filling a whole of a cache line and an area B a second area not filling refer to . That is the application processor determines whether data is stored from a head of the cache line or from a middle of the cache line for every cache line. An area where a whole of one cache line becomes a transfer data area is classified to an area A and an area where only a part of one cache line becomes a transfer data area is classified to an area B refer to in . In the area B includes both an area including a head of the transfer data area and an area including an end of the transfer data area. However there is a case that a head of the transfer data area agrees with a head of a cache line or a case that an end of the transfer data area agrees with an end of a cache line. In these cases the area B is either of the area including the head of the transfer data area the area including the end of the transfer data area or not existed.

In divided data copy step S the application processor performs a memory copy of data in the area B to the divided data area which is an area on the shared memory and aligned with a cache line of the cache memory refer to .

In transfer information writing step S the application processor writes transfer information into a transfer information area which is a non cache area in the shared memory . The transfer information can identify the area A the divided data area and an additional information area.

In cache eviction step S the application processor writes data in the area A and the divided data area into a transfer data area in the shared memory from the cache memory .

In notification step S the application processor issues an interrupt signal to the communication offload processor and notifies completion of transfer preparation.

In the aforementioned description the notification step S can be realized by issuing the interrupt signal by the interrupt control circuit but can be realized by other methods. For example the notification step S can be realized by using a register capable of being written from the application processor and being referred to from the communication offload processor . In this case the application processor changes the register to be a predetermined value and the communication offload processor detects that the value of the register is changed to the predetermined value. Further the notification step S can be also realized by a processing in which the application processor changes a predetermined area in the shared memory to a predetermined value and the communication offload processor detects that the predetermined area is changed to the predetermined value.

In interrupt processing step S the communication offload processor detects that the application processor completes the preparation of transfer data by the interrupt signal.

In transfer information reading step S the communication offload processor reads the transfer information from the transfer information area. In cache invalidation step S the communication offload processor invalidates the area A and the divided data area which are identified by the transfer information in the cache memory .

In SENDMSG call step S the communication offload processor executes sending processing by making the area A and the divided data area as transfer data and the additional information area as the other arguments and calling SENDMSG which is one of the socket API.

The SENDMSG is one of the API of a socket which can send data in a divided area. The SEND can be used instead of the SENDMSG. In order to use the SEND the communication offload processor once copies the data in the area A and the divided data area makes one continuous data area and then executes the SEND.

When the SENDMSG or SEND is called the communication offload processor executes a TCP IP processing S and a driver processing of a wired wireless LAN S and performs data sending S to the communication apparatus . That is when the SENDMSG or SEND is called the communication offload processor reads the transfer data from the shared memory and writes the transfer data into the cache memory . Then the communication offload processor sends data in the area A and data in the divided data area which are written into the cache memory as transfer data. In step S the communication offload processor writes a return value which is a value after processing SENDMSG or SEND into a return value area in the additional information area.

In step S the communication offload processor issues an interrupt signal to the application processor and notifies completion of sending processing.

In step S the application processor cancels blocking of the task which has called the SEND by the interrupt signal issued from the communication offload processor in step S. In step S the application processor delivers the return value to the application layer.

In the aforementioned processing a suitable communication offload under a multiprocessor environment can be realized using inter processor communication via the shared memory .

Further in the aforementioned processing the communication apparatus may secure an argument information area of the SEND and a return value area in the cache area on the shared memory and make it to be a transfer data area including this cache area. In this case the communication offload processor writes a return value and performs processing for writing caching data in the return value area into the shared memory . Then before the application processor refers to data in the return value area the communication offload processor invalidates the caching data in the return value area.

Then processing when a user operates the user interface of the communication apparatus and receives data from the communication apparatus will be described.

In received data area preparation step S the application processor prepares a received data area a transfer data area for receiving data in the application layer on the shared memory .

In RECV call step S the application processor causes a pointer in the received data area to be one of arguments and calls RECV which is one of the socket API.

In additional information preparation step S the application processor secures an additional information area in a non cache area on the shared memory . The application processor uses the additional information area as an argument information area for delivering another argument information of the RECV to the communication offload processor and a return value area for receiving a return value from the communication offload processor .

In alignment analysis step S the application processor subjects a received data area on the shared memory and a cache line in the cache memory to an alignment analysis. The application processor classifies the received data area into an area A filling a whole of the cache line and an area B not filling refer to . That is the application processor determines whether the application processor secures from a head of the cache line as the received data area or from a middle of the cache line as the received data area. Then the application processor classifies an area where a whole of a cache line becomes a received data area as an area A and an area where only a part of a cache line becomes a received data area as an area B refer to .

In divided data area securing step S the application processor secures a divided data area where data in the area B is copied in an area which is on the shared memory and aligned with the cache line in the cache memory refer to .

In transfer information writing step S the application processor writes transfer information in a transfer information area which is a non cache area in the shared memory . The transfer information can identify the area A the divided data area and the additional information area.

In cache eviction step S the application processor writes back data cached in the area A and the divided data area in the cache memory to the shared memory or cancels the cached data .

In first notification step S the application processor issues an interrupt signal to the communication offload processor .

Here it is described that the first notification step S can be realized by issuing the interrupt signal by the interrupt control circuit . However the step can be realized by other methods. For example the step S can be realized by using a register capable of being written from the application processor and referred to from the communication offload processor . In this case the application processor changes the register to be a predetermined value and the communication offload processor detects that the value of the register is changed to the predetermined value.

Further the first notification step S can be also realized by a processing in which the application processor changes a predetermined area in the shared memory to a predetermined value and the communication offload processor detects that the predetermined area is changed to the predetermined value.

In interrupt processing step S the communication offload processor detects that the application processor completes the preparation for receiving by the interrupt signal.

In transfer information reading step S the communication offload processor reads the transfer information from the transfer information area.

In cache invalidation step S the communication offload processor invalidates the area A and the divided data area which are identified by transfer information in the cache memory .

In RECVMSG call step S the communication offload processor makes the area A and the divided data area as a received data area and the additional information area as the other arguments. The communication offload processor calls RECVMSG which is one of the socket API and executes receiving processing.

The RECVMSG is one of the API of the socket which can receive data to a divided area. Further the RECV can be used instead of the RECVMSG. In order to use the RECV the communication offload processor once receives the data in one continuous data area by the RECV copies the received data to the area A and the divided data area and executes it.

When the RECVMSG or RECV is called the communication offload processor executes a TCP IP processing S and a driver processing of a wired wireless LAN S and performs data receiving processing S from the communication apparatus . The data received in the data receiving processing S is stored in a received data area transfer data area in the cache memory . The data in the area B is copied to the divided data area. Data in the received data area transfer data area and data in the divided data area in the cache memory are written into the shared memory .

In step S the communication offload processor writes a return value which is a value after processing the RECVMSG RECV into a return value area in the additional information area.

In second notification step S the communication offload processor issues an interrupt signal and notifies completion of receiving processing to the application processor . In step S the application processor cancels the blocking of a task which has called the RECV by the interrupt signal. In step S the application processor copies the receiving data written in the transfer data area and the divided data area to the cache memory . The application processor copies the data in the divided data area which is copied in the cache memory to the area B. In step S the application processor makes the data in the received data area transfer data area in the cache memory as receiving data and delivers the receiving data and the return value to the application layer.

In addition the application processor copies the data in the divided data area which is copied to the cache memory to the area B and makes the data in the received data area transfer data area as the receiving data. However the application processor may make data in the area A and the divided data area as the receiving data and deliver it to the application layer.

Here the second notification step S is realized by issuing the interrupt signal by the interrupt control circuit but can be realized by other methods. For example the second notification step S can be realized by using a register capable of being written from the application processor and referred to from the communication offload processor. In this case the application processor changes the register to be a predetermined value and the communication offload processor detects that the value of the register is changed to the predetermined value.

In addition the second notification step S can be realized by a processing in which the application processor changes a predetermined area in the shared memory to a predetermined value and the communication offload processor detects that the predetermined area is changed to the predetermined value.

By the aforementioned processing a suitable communication offload can be realized in a multiprocessor environment utilizing an inter processor communication via the shared memory .

Further in the aforementioned processing the communication apparatus may secure the argument information area of the RECV and the return value area in the cache area on the shared memory and perform transfer by inter processor communication including this cache area. In this case after writing a return value in the communication offload processor the communication apparatus performs a processing for writing back the cached data in the return value area to the shared memory . Then before referring to the data in the return value area in the application communication processor the communication offload processor invalidates the cached data in the return value area.

Accordingly a fault that data in a shared memory is overwritten to an application and causes a problem can be avoided by the comparatively easy processing. Since a cache function is not completely turned off lowering a communication throughput can be reduced. Since it is not necessary to execute an alignment processing to a cache line in a transfer data area in an application a conventionally used application which is not a multiprocessor system can be used continuously by diverting.

Since a high grade function e.g. a coherence function is not necessary a communication subsystem can be realized using a low price processor. Since a whole of transfer data does not need to be copied a time required for inter processor communication processing can be reduced.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims priority from Japanese Patent Application No. 2008 265180 filed Oct. 14 2008 which is hereby incorporated by reference herein in its entirety.

