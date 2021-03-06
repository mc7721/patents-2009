---

title: Method and apparatus for performing energy-efficient network packet processing in a multi processor core system
abstract: A method and apparatus for managing core affinity for network packet processing is provided. Low-power idle state of a plurality of processing units in a system including the plurality of processing units is monitored. Network packet processing is dynamically reassigned to processing units that are in a non-low power idle state to increase the low-power idle state residency for processing units that are in a low-power idle state resulting in reduced energy consumption.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08239699&OS=08239699&RS=08239699
owner: Intel Corporation
number: 08239699
owner_city: Santa Clara
owner_country: US
publication_date: 20090626
---
This disclosure relates to and in particular to energy efficiency in a multi processor core system and in particular to energy efficient network packet processing.

Typically a computer system having a plurality of processor cores handles a high workload by distributing the workload amongst all of the processor cores. However as the workload decreases each of the plurality of processor cores may be underutilized.

In order to reduce power consumption by the plurality of processor cores when workload is low an operating system may adjust the number of processor cores used based on the system utilization level. The unused processor cores are placed in a low power idle state parked and can remain at the low power idle state for long consecutive intervals. The operating system continues to distribute the workload amongst the processor cores that are not in the low power idle state.

Although the following Detailed Description will proceed with reference being made to illustrative embodiments of the claimed subject matter many alternatives modifications and variations thereof will be apparent to those skilled in the art. Accordingly it is intended that the claimed subject matter be viewed broadly and be defined only as set forth in the accompanying claims.

A computer system may include a network interface controller adapter card that receives a network packet from the network and forwards the received network packet for processing to one of a plurality of processor cores. The workload that is distributed amongst the processor cores may include the processing of network packets received by the network interface controller.

For example in the computer system the processing of network packets may be distributed amongst the processor cores such that the processing of the same traffic flow for example network packets having the same source address and destination address is performed by the same processor core. When workloads are low the operating system may use only a subset of the plurality of the processor cores and put the other processor cores in low power idle state. However if a received network packet to be processed for a particular traffic flow is assigned to a processor core core affinity setting for the traffic flow that is in a low power idle state the processor core is woken up from the low power idle state. As a result processor cores that are in a low power idle state do not have the opportunity to stay in the low power idle state for a long time.

An embodiment of the present invention dynamically adjusts the core affinity settings for network packet processing based on whether the operating system has put any of the processor cores into a low power idle state.

An embodiment of the present invention will be described for a computer system having a network interface controller that supports Receive Side Scaling RSS used by Microsoft s Windows Operating System OS . However the invention is not limited to RSS. In other embodiments the network adapter may support Scalable Input Output I O used by the Linux operating system that includes a scheduler which has a power saving mode feature or any other operating system that includes a power saving mode.

The processor may be a multi core processor such as Intel Pentium D Intel Xeon processor or Intel Core Duo processor Intel Core i7 Processor or any other type of processor. In the embodiment shown the system includes two multi core processors each having at least two processor cores cores . In one embodiment each multi core processor includes four cores .

The memory may be Dynamic Random Access Memory DRAM Static Random Access Memory SRAM Synchronized Dynamic Random Access Memory SDRAM Double Data Rate 2 DDR2 RAM or Rambus Dynamic Random Access Memory RDRAM or any other type of memory.

The ICH may be coupled to the MCH using a high speed chip to chip interconnect such as Direct Media Interface DMI . DMI supports 2 Gigabit second concurrent transfer rates via two unidirectional lanes.

The ICH may include a storage Input Output I O controller for controlling communication with at least one storage device coupled to the ICH . The storage device may be for example a disk drive Digital Video Disk DVD drive Compact Disk CD drive Redundant Array of Independent Disks RAID tape drive or other storage device. The ICH may communicate with the storage device over a storage protocol interconnect using a serial storage protocol such as Serial Attached Small Computer System Interface SAS or Serial Advanced Technology Attachment SATA .

In another embodiment the network interface controller may be included in an ICH that does not include a storage I O controller or may be included on a separate network interface card that is inserted in a system card slot in the system .

In the embodiment shown the miniport driver and filter driver are components of a Microsoft Windows operating system model WDM . The WDM includes device function drivers which may be class drivers or miniport drivers. A miniport driver supports a particular type of device for example a specific network interface controller . A filter driver is an optional driver that adds value to or modifies the behavior of the function driver miniport driver .

The Network Driver Interface Specification NDIS is a library of functions accessed via an application programming interface API for network interface controllers . The NDIS acts as an interface between layer 2 link layer and layer 3 network layer of the 7 layer Open Systems Interconnect OSI . The library functions include Object Identifiers OIDs .

The network interface controller may use a hashing function in the hash function unit to compute a hash value over a hash type for example one or more fields in the headers within the received network packet. A number of least significant bits of the hash value may be used to index an entry in an indirection table that identifies a processor core to handle processing of the received data packet and one of a plurality of receive queues to store the received data packet. The network interface controller can interrupt the identified processor core .

In an embodiment as each network packet is received by the network interface controller the flow associated with the network packet is determined. The flow of a Transport Control Protocol TCP packet may be determined based on the value of fields in the TCP header and the Internet Protocol IP header included in the packet. For example a flow identifier for the flow can be dependent on a combination of the IP source address and IP destination address included in the IP header and the source port address and destination port address included in the TCP header in the received network packet.

The plurality of hardware receive queues are provided to store received network packets. In order to ensure in order packet delivery for a particular flow each of he hardware receive queues may be assigned to a different flow and also to one of the plurality of processor cores . Thus each of the plurality of hardware receive queues is associated with one of the plurality of a core processors via the indirection table .

In the embodiment shown the network interface controller has eight receive queues . However the number of receive queues is not limited to eight. In other embodiments there may be more or less receive queues . Received network packets are stored in one of the plurality of receives queues . Packet processing of each of the receive queues may be affinitized to a specific processor core . In an embodiment of the present invention the core affinity settings for packet processing is dynamically adjusted based on the number of processor cores that are in a power saving idle state parked .

Table 1 below illustrates an example of an indirection table with an initial assignment of receive queues to processor cores in a system having eight cores and eight receive queues in order to distribute receive packet processing amongst all of the processor cores .

The distribution of receive queues to core processors is dynamically modified based on operating system OS core parking status which is handled by the OS kernel. For example when workload is low the OS kernel may park a portion of the core processors by putting them into a low power idle state. For example in an embodiment with eight core processors 6 of 8 core processors may be parked and the other portion for example 2 of 8 of the core processors may be used. Thus interrupts from the network interface controllers are only sent to the un parked cores and the parked cores remain at low power idle states resulting in a reduction in energy consumption.

For example in an embodiment if Windows 7 server core parking feature selects to use three cores and parks the remaining cores when the workloads are low the network interface controller is modified to run network interrupt and packet processing also on the selected three cores. This results in an increase in the lower power idle state residency for the parked cores.

In an embodiment a 10 Gigabit network interface controller has multiple Receive Side Scaling Receive RSS Rx queues each affinitized to a specific core. The network interface controller gets the configuration of OS core parking settings via the filter driver and modifies the RSS indirection table based on the OS core parking configuration.

At block the filter driver periodically requests OS parking status from the OS kernel . For example in an embodiment the filter driver requests the OS core parking status using an Application Program Interface API command provided by the OS kernel to query parking status of each of the processor cores . In an embodiment the filter driver periodically requests OS parking status based on the number of network packets that have been received for example after every about 1000 network packets have been received

In an alternative embodiment the filter driver accesses the CPU directly to obtain the current power state of each processor core . For example the Intel Core i7 supports low power states at the core level for optimal power management. The core power states include C0 C1 C3 and C6. C0 is the normal operating state and C1 C3 and C6 are low power states with different levels of reduced power consumption. For example in the C3 low power state all the clocks are stopped and the processor core maintains all of its architectural state except for the caches.

The current power state of each processor core is stored in one or more registers in the CPU that are accessible by the filter driver . In order to determine whether a particular core is parked the filter driver periodically reads the registers storing the power state for the cores and infers whether the core is parked based on the distribution of the power state type read for the core over a time period. For example if within a time period the registers are read n times and a core is in low power state each time the core is parked . If during the time period the core is in a high power state n times the core is not parked . If during the time period the power state of the core differs with the number of times that the power state is low power state being greater than the number of times that power state is high power state the core is inferred to be parked .

At block having received the parking status of each of the processor cores the filter driver determines if the parking status of any of processor cores has changed. If not processing continues with block to continue to periodically request parking status of processor cores .

If so the filter driver generates new data to be stored in the indirection table in the NIC based on the parking status. The filter driver uses an OID GEN RECEIVE SCALE PARAMETERS Object Identifier OID to modify the RSS parameters of the NIC based on the parking status of the processor cores. The OID GEN RECEIVE SCALE PARAMETERS OID includes an NDIS RECEIVE SCALE PARAMETERS structure that specifies the RSS parameters.

In an embodiment the structure includes a header with a type that specifies that the object includes RSS Parameters a flag indicating whether the indirection table and associated members have changed and the size of the indirection table. The new data to be stored in the indirection table based on the core parking status are appended after the other structure members. Processing continues with block .

At block upon detecting receipt of an OID GEN RECEIVE SCALE PARAMETERS OID the miniport driver stores the received new data for the indirection table in the indirection table . For example if the retrieved core parking status indicates that only processor core 0 and processor core 4 are un parked in an embodiment in which there are eight receive RSS Rx queues a round robin core assignment can be performed resulting in the new data contents of the indirection table as shown in Table 2 below stored in indirection table . Processor core 0 is assigned to receive queues 0 2 4 and 6 and processor core 4 is assigned to receive queues 1 3 5 and 7.

For example the data to be stored in Table 2 can be represented as a data structure IndTable as shown below 

The IndTable structure is appended to the OID which is received by the miniport driver allowing the miniport driver to update the data stored in the indirection table .

An embodiment has been described for a system that includes a filter driver . However the monitoring of the core parking status and request for modification of the indirection table is not limited to the filter driver . In another embodiment these functions may be included in another part of the network driver stack.

As shown in instead of adding a filter driver to the network driver stack the monitoring of core parking status is performed by the OS kernel . The request to update the indirection table is sent directly from the OS kernel to the miniport driver . Similar to the embodiment discussed for the filter driver in conjunction with the OS kernel generates an OID GEN RECEIVE SCALE PARAMETERS OID with the modified contents for the indirection table as an input parameter as discussed in conjunction with the embodiment shown in . This OID is sent directly to the device driver which modifies the indirection table accordingly based the received modified contents.

In an embodiment an RSS alignment function is added to the OS core to adjust the RSS indirection table .

An embodiment has been described for the Windows Operating System. The monitoring of core parking status and modification of the contents of the indirection table based on the monitored core parking status is not limited to the Windows Operating System the method may also be applied to other operating systems for example the Linux Operating System.

Alternative embodiments of the invention also include machine accessible media containing instructions for performing the operations of the invention. Such embodiments may also be referred to as program products. Such machine accessible media may include without limitation computer readable storage media having instructions computer readable program code stored thereon such as floppy disks hard disks Compact Disk Read Only Memories CD ROM s Read Only Memory ROM and Random Access Memory RAM and other tangible arrangements of particles manufactured or formed by a machine or device. Instructions may also be used in a distributed environment and may be stored locally and or remotely for access by single or multi processor machines.

While embodiments of the invention have been particularly shown and described with references to embodiments thereof it will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the scope of embodiments of the invention encompassed by the appended claims.

