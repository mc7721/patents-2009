---

title: Para-virtualization in a nested virtualization environment using reduced number of nested VM exits
abstract: A para-virtualization method is provided. The method comprises implementing a virtual machine (VM) for guest software running on first host software. In response to a privileged instruction, the guest software causes a first VM exit. If the first host software is not running directly on hardware, the privileged instruction is managed without causing a second VM exit. Otherwise, the privileged instruction is managed normally.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08495628&OS=08495628&RS=08495628
owner: International Business Machines Corporation
number: 08495628
owner_city: Armonk
owner_country: US
publication_date: 20090823
---
A portion of the disclosure of this patent document contains material which is subject to copyright protection. The owner has no objection to the facsimile reproduction by any one of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyrights whatsoever.

Certain marks referenced herein may be common law or registered trademarks of third parties affiliated or unaffiliated with the applicant or the assignee. Use of these marks is for providing an enabling disclosure by way of example and shall not be construed to limit the scope of the claimed subject matter to material associated with such marks.

The claimed subject matter relates generally to nested virtualization and more particularly to para virtualization in a nested virtualization environment.

In a virtualization environment a host software running on one or more hardware infrastructures may emulate the hardware for a guest software running on the host software. In other words a hypervisor running on a physical machine may implement a virtual machine VM for a guest running on the hypervisor. That is the VM may allow the guest to operate as if the guest were running directly on the physical machine.

Typically the physical machine operates in a guest mode or a root mode. In the guest mode the guest software manages execution of instructions by the physical machine. In the root mode the hypervisor manages execution of instructions by the physical machine. The physical machine generally operates in the guest mode but may switch to the root mode to execute a privileged instruction that requires support from the hypervisor to be compatible with the physical machine. Switching to the root mode is referred to as a VM exit and switching back to the guest mode is referred to as a VM entry.

The present disclosure is directed to systems and corresponding methods that facilitate para virtualization in a nested virtualization environment.

For purposes of summarizing certain aspects advantages and novel features have been described herein. It is to be understood that not all such advantages may be achieved in accordance with any one particular embodiment. Thus the claimed subject matter may be embodied or carried out in a manner that achieves or optimizes one advantage or group of advantages without achieving all advantages as may be taught or suggested herein.

In accordance with one embodiment a para virtualization method is provided. The method comprises implementing a virtual machine VM for guest software running on first host software. In response to a privileged instruction the guest software causes a first VM exit. If the first host software is not running directly on hardware the privileged instruction is managed without causing a second VM exit. Otherwise the privileged instruction is managed normally.

In accordance with another embodiment a system comprising one or more logic units is provided. The one or more logic units are configured to perform the functions and operations associated with the above disclosed methods. In accordance with yet another embodiment a computer program product comprising a computer useable medium having a computer readable program is provided. The computer readable program when executed on a computer causes the computer to perform the functions and operations associated with the above disclosed methods.

One or more of the above disclosed embodiments in addition to certain alternatives are provided in further detail below with reference to the attached figures. The claimed subject matter is not however limited to any particular embodiment disclosed.

Features elements and aspects that are referenced by the same numerals in different figures represent the same equivalent or similar features elements or aspects in accordance with one or more embodiments.

In the following numerous specific details are set forth to provide a thorough description of various embodiments of the claimed subject matter. Certain embodiments may be practiced without these specific details or with some variations in detail. In some instances certain features are described in less detail so as not to obscure other aspects of the disclosed embodiments. The level of detail associated with each of the elements or features should not be construed to qualify the novelty or importance of one feature over the others.

Para virtualization refers to the ability of a guest software to communicate with a root hypervisor using one or more hypercalls provided in an application programming interface API . As a result some of the functionality provided by the root hypervisor may be provided by the guest instead.

In one or more embodiments para virtualization may be implemented for a nested hypervisor i.e. a hypervisor running as a guest on another hypervisor and a root hypervisor. In one implementation if a guest running on the nested hypervisor causes a VM exit due to a privileged instruction the nested hypervisor may manage the privileged instruction without causing another VM exit. Depending on the level of nesting such an implementation may reduce the number of VM exits several orders of magnitude. Since each VM exit is associated with an overheard cost the reduction of VM exits may significantly improve performance.

Referring to in accordance with one or more embodiments para virtualization may be implemented in an exemplary nested virtualization environment comprising a physical machine and a level 0 L0 or root hypervisor and one or more higher level or nested hypervisors. The level 1 L0 hypervisor runs on the physical machine and one or more guests run on the L0 hypervisor and each of the higher level hypervisors. For example the guest runs as a guest on the level 2 L2 hypervisor the L2 hypervisor runs as a guest on the level 1 L1 hypervisor and the L1 hypervisor runs as a guest on the L0 hypervisor .

Referring to in accordance with one or more embodiments a guest running on a hypervisor causes a VM exit to the root hypervisor e.g. the L0 hypervisor due to a privileged instruction P .

If the guest is running on a para virtualized nested hypervisor e.g. the L1 hypervisor or the L2 hypervisor P the root hypervisor traps to the next level hypervisor e.g. the L1 hypervisor P . In other words the root hypervisor throws an exception and transfers control to the next level hypervisor to handle the exception. The next level hypervisor manages the privileged instruction without causing another VM exit P . If the guest is running on the root hypervisor the root hypervisor manages the privileged instruction normally P . It is noteworthy that the root hypervisor may mark para virtualized nested hypervisors on startup as provided in more detail below.

Referring to in accordance with one embodiment on startup or at some other point in time a hypervisor performs a hypercall to determine whether the hypervisor is a nested hypervisor running on another hypervisor or the root hypervisor running directly on the hardware P . The hypercall may be described in an API. If the hypercall fails P the hypervisor is determined to be the root hypervisor P . Otherwise the hypervisor is determined to be a nested hypervisor P and the hypervisor is marked as a para virtualized nested hypervisor by the root hypervisor P .

Referring to in accordance with one embodiment on startup or at some other point in time the hypervisor requests an identification ID of the underlying hardware e.g. performs a CPU ID command to determine whether the hypervisor is a nested hypervisor running on another hypervisor or the root hypervisor running directly on hardware P . If the value of returned by the ID request is a value associated with a VM P the hypervisor is determined to be a nested hypervisor P . Otherwise the hypervisor is determined to be the root hypervisor P .

A para virtualization implementation is provided below for enabling a nested hypervisor to manage privileged instructions in an Intel VT x virtualization environment. It should be understood however that such an implementation is provided for purposes of example to illustrate the processes described above. In other implementations para virtualization may be implemented for different types of privileged instructions in different types of virtualization environments without limitation.

Referring to in accordance with one or more embodiments an exemplary virtualization environment e.g. Intel VT x comprises a CPU a root hypervisor a nested hypervisor a guest and a memory . The guest is a guest that runs on the nested hypervisor and the nested hypervisor is a guest that runs on the root hypervisor .

Referring to in accordance with one embodiment the root hypervisor implements a VM for the nested hypervisor by creating a VM control structure VMCS and loading the VMCS into the memory . The root hypervisor also runs the nested hypervisor P . On startup the nested hypervisor performs a hypercall and determines that the nested hypervisor is running on another hypervisor. In response to the hypercall the root hypervisor marks the nested hypervisor as a para virtualized nested hypervisor P .

The nested hypervisor implements a VM for the guest by creating a VMCS and calling a VMTPRLD instruction to load the VMCS into the memory . The VMTPRLD instruction causes a trap to the root hypervisor and the root hypervisor saves the address of the VMCS P . In other words the nested hypervisor throws an exception and transfers control to the root hypervisor to handle the exception.

Once the VMCS is loaded into the memory the nested hypervisor calls a VMLAUNCH instruction to run the guest . The VMLAUNCH instruction causes a trap to the root hypervisor and the root hypervisor creates a VMCS and calls a VMTPRLD instruction to load the VMCS into the memory P . The root hypervisor also calls a VMLAUNCH instruction to run the guest P .

Referring to in accordance with one embodiment the guest causes a VM exit due to a privileged instruction e.g. VMREAD or VMWRITE P . In response to the VM exit the root hypervisor updates the VMCS in the memory with values from the VMCS and runs the nested hypervisor P .

The nested hypervisor reads from or writes to the VMCS in the memory e.g. depending on whether the privileged instruction is a VMREAD or a VMWRITE instruction respectively . In other words the nested hypervisor directly accesses the VMCS e.g. instead of calling the VMREAD or VMWRITE instruction again to access the VMCS and causing another VM exit . Once the memory access is completed the nested hypervisor calls a VMRESUME instruction to perform a VM entry i.e. run the guest again P .

The VMRESUME instruction causes a trap to the root hypervisor and the root hypervisor updates the VMCS with values from the VMCS and the VMCS . The root hypervisor also calls a VMPTRLD instruction to load the VMCS into the memory P and calls a VMLAUNCH instruction to run the guest P .

Alternatively instead of directly accessing the VMCS in the memory the nested hypervisor may perform a hypercall that batches several privileged instructions e.g. VMREADs and VMWRITEs to reduce the number of VM exits.

In different embodiments the claimed subject matter may be implemented either entirely in the form of hardware or entirely in the form of software or a combination of both hardware and software elements. For example a nested virtualization environment may comprise a controlled computing system environment that may be presented largely in terms of hardware components and software code executed to perform processes that achieve the results contemplated by the system of the claimed subject matter.

Referring to a computing system environment in accordance with an exemplary embodiment is composed of a hardware environment and a software environment . The hardware environment comprises the machinery and equipment that provide an execution environment for the software and the software environment provides the execution instructions for the hardware as provided below.

As provided here software elements that are executed on the illustrated hardware elements are described in terms of specific logical functional relationships. It should be noted however that the respective methods implemented in software may be also implemented in hardware by way of configured and programmed processors ASICs application specific integrated circuits FPGAs Field Programmable Gate Arrays and DSPs digital signal processors for example.

Software environment is divided into two major classes comprising system software and application software . In one embodiment a hypervisor may be implemented as system software or application software executed on one or more software or hardware environments to facilitate para virtualization in a nested virtualization environment.

System software may comprise control programs such as the operating system OS and information management systems that instruct the hardware how to function and process information. Application software may comprise but is not limited to program code data structures firmware resident software microcode or any other form of information or routine that may be read analyzed or executed by a microcontroller.

In an alternative embodiment the claimed subject matter may be implemented as computer program product accessible from a computer usable or computer readable medium providing program code for use by or in connection with a computer or any instruction execution system. For the purposes of this description a computer usable or computer readable medium may be any apparatus that can contain store communicate propagate or transport the program for use by or in connection with the instruction execution system apparatus or device.

The computer readable medium may be an electronic magnetic optical electromagnetic infrared or semiconductor system or apparatus or device or a propagation medium. Examples of a computer readable medium include a semiconductor or solid state memory magnetic tape a removable computer diskette a random access memory RAM a read only memory ROM a rigid magnetic disk and an optical disk. Current examples of optical disks include compact disk read only memory CD ROM compact disk read write CD R W and digital video disk DVD .

Referring to an embodiment of the application software may be implemented as computer software in the form of computer readable code executed on a data processing system such as hardware environment that comprises a processor coupled to one or more memory elements by way of a system bus . The memory elements for example may comprise local memory storage media and cache memory . Processor loads executable code from storage media to local memory . Cache memory provides temporary storage to reduce the number of times code is loaded from storage media for execution.

A user interface device e.g. keyboard pointing device etc. and a display screen can be coupled to the computing system either directly or through an intervening I O controller for example. A communication interface unit such as a network adapter may be also coupled to the computing system to enable the data processing system to communicate with other data processing systems or remote printers or storage devices through intervening private or public networks. Wired or wireless modems and Ethernet cards are a few of the exemplary types of network adapters.

In one or more embodiments hardware environment may not include all the above components or may comprise other components for additional functionality or utility. For example hardware environment can be a laptop computer or other portable computing device embodied in an embedded system such as a set top box a personal data assistant PDA a mobile communication unit e.g. a wireless phone or other similar hardware platforms that have information processing and or data storage and communication capabilities.

In some embodiments of the system communication interface communicates with other systems by sending and receiving electrical electromagnetic or optical signals that carry digital data streams representing various types of information including program code. The communication may be established by way of a remote network e.g. the Internet or alternatively by way of transmission over a carrier wave.

Referring to application software may comprise one or more computer programs that are executed on top of system software after being loaded from storage media into local memory . In a client server architecture application software may comprise client software and server software. For example in one embodiment client software is executed on a personal computing system not shown and server software is executed on a server system not shown .

Software environment may also comprise browser software for accessing data available over local or remote computing networks. Further software environment may comprise a user interface e.g. a Graphical User Interface GUI for receiving user commands and data. Please note that the hardware and software architectures and environments described above are for purposes of example and one or more embodiments of the invention may be implemented over any type of system architecture or processing environment.

It should also be understood that the logic code programs modules processes methods and the order in which the respective processes of each method are performed are purely exemplary. Depending on implementation the processes can be performed in any order or in parallel unless indicated otherwise in the present disclosure. Further the logic code is not related or limited to any particular programming language and may comprise of one or more modules that execute on one or more processors in a distributed non distributed or multiprocessing environment.

The claimed subject matter has been described above with reference to one or more features or embodiments. Those skilled in the art will recognize however that changes and modifications may be made to these embodiments without departing from the scope of the claimed subject matter. These and various other adaptations and combinations of the embodiments disclosed are within the scope of the claimed subject matter as defined by the claims and their full scope of equivalents.

