---

title: Method and system for efficiently using buffer space
abstract: A method and system for transferring iSCSI protocol data units (“PDUs”) to a host system is provided. The system includes a host bus adapter with a TCP/IP offload engine. The HBA includes, a direct memory access engine operationally coupled to a pool of small buffers and a pool of large buffers, wherein an incoming PDU size is compared to the size of a small buffer and if the PDU fits in the small buffer, then the PDU is placed in the small buffer. If the incoming PDU size is compared to a large buffer size and if the incoming PDU size is less than the large buffer size then the incoming PDU is placed in the large buffer. If the coming PDU size is greater than a large buffer, then the incoming PDU is placed is more than one large buffer and a pointer to a list of large buffers storing the incoming PDU is placed in a small buffer.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07924859&OS=07924859&RS=07924859
owner: QLOGIC, Corporation
number: 07924859
owner_city: Aliso Viejo
owner_country: US
publication_date: 20090319
---
This application is a continuation of U.S. application Ser. No. 10 931 851 filed Sep. 1 2004 now U.S. Pat. No. 7 522 623.

The present invention relates to network systems and more particularly to efficiently using buffer space.

Storage area networks SANs are commonly used where plural memory storage devices are made available to various host computing systems. Data in a SAN is typically moved from plural host systems that include computer systems servers etc. to a storage system through various controllers adapters.

Host systems often communicate with storage systems via a host bus adapter HBA may also be referred to as a controller and or adapter using an interface for example the PCI bus interface. PCI stands for Peripheral Component Interconnect a local bus standard that was developed by Intel Corporation . The PCI standard is incorporated herein by reference in its entirety. Most modern computing systems include a PCI bus in addition to a more general expansion bus e.g. the ISA bus . PCI is a 64 bit bus and can run at clock speeds of 33 or 66 MHz.

PCI X is another standard bus that is compatible with existing PCI cards using the PCI bus. PCI X improves the data transfer rate of PCI from 132 MBps to as much as 1 GBps. The PCI X standard was developed by IBM Hewlett Packard Corporation and Compaq Corporation to increase performance of high bandwidth devices such as Gigabit Ethernet standard and Fibre Channel Standard and processors that are part of a cluster.

Various other standard interfaces are also used to move data from host systems to storage devices. Internet SCSI iSCSI is one such standard as defined by the Internet Engineering Task Force IETF maps the standard SCSI protocol on top of the TCP IP protocol. iSCSI incorporated herein by reference in its entirety is based on Small Computer Systems Interface SCSI which enables host computer systems to perform block data input output I O operations with a variety of peripheral devices including disk and tape devices optical storage devices as well as printers and scanners.

A traditional SCSI connection between a host system and peripheral device is through parallel cabling and is limited by distance and device support constraints. For storage applications iSCSI was developed to take advantage of network architectures based on Fibre Channel and Gigabit Ethernet standards. iSCSI leverages the SCSI protocol over established networked infrastructures and defines the means for enabling block storage applications over TCP Transmission Control Protocol IP Internet Protocol networks. iSCSI defines mapping of the SCSI protocol with TCP IP.

Networks are generally defined as having layers of protocol. The iSCSI and TCP IP protocol suite consist of 4 protocol layers the application layer of which iSCSI is one application the transport layer TCP the network layer IP and the link layer i.e. Ethernet . A complete description of the TCP IP protocol suite is provided in TCP IP Illustrated Vol. 1 by W. Richard Stevens and Volume 2 by Gary R. Wright and W. Richard Stevens published by Addison Wesley Professional Computing Series. The following provide a brief overview of TCP iSCSI and RDMA protocol standards.

TCP is a network protocol that provides connection oriented reliable byte stream service. This means that two nodes must establish a logical connection before sending data and that TCP maintain state information regarding the data transfer. Reliable means that data is guaranteed to be delivered in the same order that it was sent. A byte stream service means that TCP views data to be sent as a continuous data stream that is sent in any way it sees fit and delivers it to the remote node as a byte stream. There is no concept of a data frame boundary in a TCP data stream.

The iSCSI architecture is based on a client server model. Typically the client is a host system such as a file server that issues a read or write command. The server may be a disk array that responds to the client request.

 Exchange The operations needed to do a iSCSI data read or write. An exchange consists of three operational phases command phase data movement phase and response phase.

 Target Typically a disk array is the target that accepts a read or write command and performs the requested operation.

In a typical iSCSI exchange an initiator sends a read or write command to a target. For a read operation the target sends the requested data to the initiator. For a write command the target sends a Ready to Transfer Protocol Data Unit PDU informing the initiator that the target is ready to accept the write data. The initiator then sends the write data to the target. Once the data is transferred the exchange enters the response phase. The target then sends a response PDU to the initiator with the status of the operation. Once the initiator receives this response the exchange is complete. The use of TCP guarantees the delivery of the PDUs.

Typically logical units in the target process commands. Commands are sent by the host system in Command Descriptor Blocks CDB . A CDB is sent to a specific logical unit for example the CDB may include a command to read a specific number of data blocks. The target s logical unit transfers the requested data block to the initiator terminating with a status message indicating completion of the request. iSCSI encapsulates CDB transactions between initiators and targets over TCP IP networks.

iSCSI PDUs may vary greatly in size from a few bytes to hundreds of kilobytes. Normally the size of the data will be known before it is received and a host computing system can allocate buffers of proper size and assign them to be used when data is received. However under the iSCSI standard data may also be transferred along with a command before a receiving host system can allocate receive buffers.

When this occurs data may be transferred to unassigned pre allocated small or large buffers. The choice to use small or large buffers has efficiency tradeoffs depending on the size of data received. The use of small buffers only is efficient for small PDUs as there is little unused space in the buffers. However when large amounts of data are transferred to small buffers the buffers are linked by a scatter gather list which requires intense processing.

If only large pre allocated buffers are used then the large buffers are under utilized when small PDUs are received. This results in wastage of buffer space.

Therefore there is a need for a system and method for efficiently using buffer space to handle variable iSCSI PDU sizes.

In one aspect of the present invention a method for transferring iSCSI protocol data units PDUs to a host system is provided. The method includes comparing an incoming PDU size with a size of a small buffer in a small buffer pool placing the incoming PDU in the small buffer if the PDU fits in the small buffer determining if the incoming PDU will fit in a large buffer from a large buffer pool and placing the incoming PDU in the large buffer if the incoming PDU will fit in the large buffer.

The method also includes placing the incoming PDU in more than one large buffer if the incoming PDU size is greater than a large buffer and creating a pointer to a list of buffers that are used to store the PDU.

In yet another aspect of the present invention a host bus adapter with a TCP IP offload engine for transferring iSCSI protocol data units PDU is provided. The HBA includes a direct memory access engine operationally coupled to a pool of small buffers and a pool of large buffers wherein an incoming PDU size is compared to the size of a small buffer and if the PDU fits in the small buffer then the PDU is placed in the small buffer.

If the incoming PDU size is compared to a large buffer size and if the incoming PDU size is less than the large buffer size then the incoming PDU is placed in the large buffer. If the coming PDU size is greater than a large buffer then the incoming PDU is placed is more than one large buffer and a pointer to a list of large buffers storing the incoming PDU is placed in a small buffer.

In yet another aspect of the present invention a TCP IP offload engine TOE for transferring iSCSI protocol data units PD is provided. The TOE includes a pool of small buffers and a pool of large buffers wherein an incoming PDU size is compared to the size of a small buffer and if the PDU fits in the small buffer then the PDU is placed in the small buffer.

This brief summary has been provided so that the nature of the invention may be understood quickly. A more complete understanding of the invention can be obtained by reference to the following detailed description of the preferred embodiments thereof concerning the attached drawings.

To facilitate an understanding of the preferred embodiment the general architecture and operation of a system using storage devices will be described. The specific architecture and operation of the preferred embodiment will then be described with reference to the general architecture.

System according to the present invention can be used for both initiator and target applications i.e. can be used on a host bus adapter or with a redundant array of inexpensive disks RAID controller . RAID controller is coupled to plural storage devices for example and .

System provides hardware assistance to improve the speed of iSCSI read and write transactions as well as a full hardware implementation of a TCP IP protocol stack to assure full gigabit operation. System also includes an embedded gigabit Ethernet MAC to connect a PCI based host to a LAN not shown .

The present invention provides a hardware implementation of a full network protocol stack. Application Programming Interfaces APIs to this protocol stack are made available to allow host software to take advantage of the hardware acceleration for straight network applications.

The present invention may be used on a PCI development board with a Field Programmable gate Array FPGA . The chip may also be integrated into an Application Specific Integrated Circuit ASIC with an embedded serialize de serializer SERDES and internal programmable random access memory RAM .

In conventional systems the main memory is coupled to the CPU via a system bus or a local memory bus not shown . The main memory is used to provide the CPU access to data and or program information that is stored in main memory at execution time. Typically the main memory is composed of random access memory RAM circuits. A computer system with the CPU and main memory is often referred to as a host system.

System includes an embedded processor that is used to process SCSI requests into iSCSI exchanges to transfer SCSI based data. Processor also generates completion messages for host .

iSCSI processor includes hardware state machines firmware which synchronizes incoming byte streams from TCP finds iSCSI PDU boundaries sends data to host via SCSI direct memory access engine module SDE .

System also includes network operation processors that include plural state machines for different network protocols for example TCP IP and Ethernet for both traffic entering and leaving system . The state machines handle most of the data transfer without host CPU involvement.

Local memory interface is used by various system components to access external memory in this illustration RAM .

Encryption de cryption engine is used to encrypt de crypt data while data is moved in and out of host using system . Standard encryption de cryption techniques may be used.

Two DMA engines or modules are used by NOPs to move data to and from host . Inbound DMA module is used to move data from system i.e. from local memory to host memory. Buffer queue manager maintains small and large buffers that are used by Inbound DMA engine . Outbound DMA engine is used to move data from host memory to system for transmission to the network.

SCSI DMA Engine SDE provides iSCSI processor with a DMA channel from Local RAM to Host memory. SDE includes a byte packer function that takes unaligned or less than 8 byte buffers and packs them into 8 byte words before sending them to Host .

System also includes request queue managers the term manager and module are used interchangeably throughout this specification and that are used to pass commands to chip to perform a specific operation. SCSI request queue manager is used for initiating SCSI based transfers while module is used for TCP IP Ethernet or any other protocol standard.

Completion queue managers and are used to send completion messages to host . These messages are generated to report status of inbound i.e. from the network to system and then to host to outbound i.e. from host to the network via system transfers. SCSI completion manager handles SCSI completion messages while non SCSI messages are handled by module .

Register interface provides host access to plural system status and control registers as well as a channel to access local memory .

PCI PCI X interface block and PCI interface provide a PCI PCI X interface between host and system . BIOS Read only memory is also provided to store invariant instruction sequences such as start up instruction sequences or basic input output operating system BIOS sequences instructions.

Data enters leaves system through a serial de serializer SERDES that converts incoming and outgoing data into a serial and non serial format.

Small buffer pool A includes fixed size small buffers while large buffer pool B contains fixed size large buffers. Host or system may define the term small and large .

When a PDU is received from the network to be transferred to host SDE compares the length of the data to the size of a small buffer in pool A and a large buffer in pool B. If the PDU is small enough to fit completely in a single small buffer it is transferred to a next small buffer available in pool A.

If the PDU is too large to fit in a single small buffer but small enough to fit in a single large buffer the PDU is transferred to the next large buffer in pool B.

Finally if the PDU is too large to fit in a single large buffer it is transferred to plural large buffers and the addresses of those large buffers are placed in one or more small buffers which may be linked creating a scatter gather list. After transfer of the data to host it is notified with a status indicating which transfer method was used i.e. a small buffer a large buffer or a group of large buffers with the address in a small buffer .

Turning in detail to in step S a PDU is received by system . The PDU is received from the network. In step S SDE compares the size of the incoming PDU with the size of a small buffer in the small buffer pool A. If the PDU can fit in the small buffer then the PDU is placed in the small buffer in step S and data is transferred. Host is notified in step SA.

If the PDU in step S does not fit in the small buffer then in step S SDE determines whether the PDU can be placed in a single large buffer. If it can be placed in a single large buffer then in step S the PDU is placed in a large buffer and host is notified in step SA.

If the PDU in step S cannot fit into a single large buffer then in step S the PDU is placed in more than one large buffer. A scatter gather list may be created and a pointer pointing to the list is placed in a small buffer. In step S data is transferred and host is notified of the pointer to the scatter gather list not shown .

It is noteworthy that buffer pools A and B may be of fixed or variable size and an optimum size may be used to efficiently transfer data.

In one aspect of the present invention optimal size buffer is used for intermediate storage. Also using an appropriate size buffer based on PDU size reduces extra processing.

Although the present invention has been described with reference to specific embodiments these embodiments are illustrative only and not limiting. Many other applications and embodiments of the present invention will be apparent in light of this disclosure and the following claims.

