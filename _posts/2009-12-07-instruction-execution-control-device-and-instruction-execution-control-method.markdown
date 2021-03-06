---

title: Instruction execution control device and instruction execution control method
abstract: An instruction execution control device operates a plurality of threads in a simultaneous multi-thread system. The device has architecture registers (--) for each thread, and a selection circuit () which, when an operand data required for executing a function is read from a register file (), selects in advance a thread to be read from the register file (). This makes it possible to select an architecture register at an early stage, and although the number of circuits in a portion for selecting the architecture registers increases, the wiring amount of the circuits can be decreased, because the architecture register of the thread to be read is selected in advance.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07958338&OS=07958338&RS=07958338
owner: Fujitsu Limited
number: 07958338
owner_city: Kawasaki
owner_country: JP
publication_date: 20091207
---
This application is a continuation of International Application No. PCT JP2007 000652 filed on Jun. 20 2007 now pending herein incorporated by reference.

The present invention relates to an instruction execution control device and an instruction execution control method in which a plurality of threads operate in a simultaneous multi thread system and instruction control is executed in an out of order processing and more particularly to an instruction execution control device and an instruction execution control method for controlling reading of a register file which operates in a simultaneous multi thread system.

Higher speed processing is demanded for a CPU Central Processing Unit . And for this the processing of a CPU has been improved using various technologies. The methods used for this purpose are pipeline processing a superscalar system which performs parallel processing and an out of order execution system which executes instructions having completed input data with priority without executing according to the sequence assigned to the program instructions.

The out of order execution system is a technology to improve performance of a CPU by executing the subsequent instruction first when data required for the first instruction is not completed and data required for the subsequent instruction processing is completed e.g. see Patent Document 1 .

For example in the case of the processing instructions in the sequence written in a program if a first instruction processing is an instruction involving memory access and a subsequent instruction processing is an instruction which does not involve memory access then the instruction is executed in parallel with the memory access of the instruction processing and the instruction processing is executed after executing the instruction processing .

Another multi thread system for improving processing of a CPU by allowing not a single program but a plurality of programs to run has been proposed e.g. see Patent Document 2 .

In this multi thread system of allowing a plurality of programs to run by providing a plurality of sets of programmable resources a CPU it is equivalent to operate a plurality of CPUs when viewed from a software point of view. Therefore a plurality of programs can be executed.

The architecture register temporarily stores operand data and is required to have a read write speed equivalent to the computing speed as a part of the CPU. Therefore the architecture register is constructed not by memories but by huge registers. For example the architecture register is constructed by register files that can be installed at high density by a fewer number of transistors.

One example of this multi thread system is a VMT Vertical Multi Threading system. According to this system only one program can run at a time but programs can be switched when a long wait time for data is generated or when a predetermined interval time elapses. For the circuit amount used for a VMT system programmable resources are provided for the number of programs but the circuit amount to be added to run one program is little which is easily implemented.

In the case of the register file is constructed by an architecture register for each thread and one architecture register is set to active and the other architecture register is set to sleep according to the switching of the programs and operand data is read from an architecture register corresponding to the running program.

Another example of a multi thread system is a simultaneous multi thread system SMT system which allows a plurality of programs to run simultaneously. Since a plurality of programs run simultaneously circuit control becomes more difficult and resources increase compared with the case of allowing a single program to run but circuits can be efficiently used since a plurality of programs run at the same time.

In the case of this simultaneous multi thread system as well architecture registers for a plurality of threads are constructed by register files and operand data of a corresponding thread is read from these architecture registers for the plurality of threads.

As described above in the case of the simultaneous multi thread system architecture registers for a plurality of threads are constructed by register files and a plurality of programs are allowed to run simultaneously hence the circuit amount to select the architecture registers increases in order to read operand data required for executing functions compared with the a single thread system. Also wiring amount of the circuits may increase when operand data in different threads are read simultaneously.

Therefore compared with the case of a single thread it is difficult to improve read frequency of the register file. This means that improving performance of a CPU to increase computing speed is difficult even if the out of order system and simultaneous multi thread system are used.

With the foregoing in view it is an object of the present invention to provide an instruction execution control device and an instruction execution control method for reading operand data required for executing the function at high speed from a register file constituting the architecture registers in a plurality of threads in simultaneous multi thread processing.

It is another object of the present invention to provide an instruction execution control device and instruction execution control method to minimize an increase in circuit amount and wiring amount for reading from a register file even if architecture registers for a plurality of threads are constructed in the register file.

It is still another object of the present invention to provide an instruction execution control device and instruction execution control method to minimize an increase in circuit amount and writing amount for reading from a register file and improving frequency of simultaneous multi thread processing even if architecture registers for a plurality of threads are constructed in the register file.

In order to attain the above objects this invention provides an instruction execution control device including a reservation station for controlling a computing processing for processing out of order execution and controlling main storage operand address generation a register update buffer for storing data acquired by execution of a function a register file having an architecture register for each thread and a read thread selection circuit for limiting the number of threads that can be read simultaneously to the number of threads less than the number of threads of the architecture registers and a thread selection circuit which when operand data is read from the register file by executing an entry in the reservation station selects a read thread of the entry before the entry is executed and controls the read thread selection circuit. And the operand data is read from an architecture register of the thread selected by the thread selection circuit when the entry is computed or operand generation is executed.

Further this invention provides an instruction execution control method including a step of controlling using a reservation station a computing unit and a main storage operand generator to process an out of order execution a step of storing data acquired by the execution to a register update buffer which is not observed by a program a step of selecting a read thread of an entry of the reservation station before executing the entry when operand data is read from the register file by executing the entry by the reservation station a step of selecting using the read thread a register file having an architecture register for each thread of a simultaneous multi thread system and a read thread selection circuit for limiting the number of threads that can be read simultaneously to the number of threads less than the number of threads of the architecture registers and a step of reading operand data from the architecture register of the thread selected by the thread selection circuit when the entry is computed or operand generation is executed.

Also in the present invention it is preferable that the reservation station does not limit the number of threads that can be read simultaneously when reading the operand data required for computing and generating an operand address from the register update buffer or from an immediate value.

Also in the present invention it is preferable that the reservation station stores the operand data in the register update buffer into the architecture register when the instruction executed from the reservation station is completed by storing data acquired by executing an instruction by the entry of the reservation station into the register update buffer.

Also in the present invention it is preferable that the reservation station judges whether or not the entry in the reservation station requires to read the operand data from the register file and also judges whether or not the thread of this entry matches the thread of the entry selected by the thread selection circuit and selects for the execution the entry which requires to read data from the register file and of which thread matches with the thread of the entry selected by the thread selection circuit.

Also in the present invention it is preferable that the reservation station selects based on the judgment an entry which can read operand data required for execution of a function from the register update buffer or can use an immediate value as an entry to be executed regardless the thread of the entry.

Also in the present invention it is preferable that the thread selection circuit detects that a thread that can be read from the register file is limited to a specific thread and selects the specific thread.

Also in the present invention it is preferable that the thread selection circuit detects that a thread that can be read from the register file need not be limited to a specific thread and prohibits a selection of a thread which is not operating using a signal to indicate a thread which is operating.

Also in the present invention it is preferable that the thread selection circuit detects that a thread that can be read from the register file need not be limited to a specific thread and judges whether or not a thread in operation which cannot execute any of the entries in the reservation station exists and prohibits the thread selection of the thread which cannot issue any entry if it is decided that the thread exists and if another thread in operation which can issue an entry exists.

Also in the present invention it is preferable that the thread selection circuit detects that a thread that can be read from the register file need not be limited to a specific thread and judges whether or not an instruction which cannot be completed for a predetermined period exists in entries in the reservation station and selects the entry of the thread which is not completed at a predetermined interval if it is decided that the entry exists.

Also in the present invention it is preferable that the thread selection circuit detects that a thread that can be read from the register file need not be limited to a specific thread and selects a thread for which the time when this thread is not selected by the thread selection circuit is longest.

When a plurality of threads are operated by the simultaneous multi thread system an architecture register is provided for each thread and a thread to be read from the register file is selected in advance to read operand data required for execution of the function from the register file so the architecture register can be selected at an early stage. The number of circuit for selecting the architecture register increases but the wiring amount of circuits can be decreased because the architecture register of the thread to be read is selected in advance.

When operand data is read from a location other than the architecture registers by the entry of the reservation station all the threads are simultaneously read unlike the case of reading from the architecture register without restrictions by the threads which are read simultaneously.

Embodiments of the present invention will now be described with reference to the drawings in the sequence of an information processing device a general configuration of an instruction execution control device an instruction execution control device a thread selection circuit and other embodiments. The present invention however is not limited to the following embodiments but can be modified in various ways.

In order to fetch instructions an instruction fetch address generator selects an instruction address and sends an instruction fetch request for the selected instruction address to the primary instruction cache . The instruction fetched from the primary instruction cache is stored in an instruction buffer . The stored instructions are supplied to an instruction decoder in the execution sequence of the program from the instruction buffer .

The instruction decoder decodes the instructions according to the execution sequence of the program. Depending on the type of the instruction to be decoded the instruction decoder creates a required entry for a reservation station unit for generating a main storage operand address RSA Reservation Station for Address generate which control execution of instructions a reservation station unit for computing a fixed point RSE Reservation Station for Execute a reservation station unit for computing a floating point RSF Reservation Station for Floating and a reservation station unit for branch instruction RSBR Reservation Station for BRanch .

In other words the instruction decoder decodes a fetched instruction in order and the decoded instruction is stored in the reservation station units and which control the execution of functions respectively depending on the type of instruction. A reservation station unit has reservation station units for computing and and reservation station unit for generating a main storage operand address.

An entry is created in a commit stack entry CSE Commit Stack Entry for controlling completion of an instruction for all the decoded instructions.

If a decoded instruction is a load instruction an entry is created in the RSA and the RSA instructs an operand address generator to generate an operand address and reads the corresponding data from the primary data cache to a fixed point update buffer GUB General Update Buffer and a floating point update buffer FUB Floating Update Buffer depending on the type of load instruction.

If the decoded instruction creates an entry in RSE and RSF each computing unit and is operated so as to execute corresponding computing processing. In the case when the decoded instruction creates an entry in the RSA RSE and RSF an out of order execution can be enabled by renaming a register corresponding to GUB and FUB and the execution result is stored in GUB and FUB.

Instructions executed based on out of order processing by the reservation stations and are completed according to the sequence of the program by the control of the CSE. Programmable resources such as a fixed point register floating point register and program counters PC NEXT PC and are updated only for the completed instructions.

A branching forecasting mechanism forecasts branching by an instruction from the reservation for branching instruction and controls the instruction fetch address generator .

Here a register file is used for the fixed point register and the floating point register of the architecture registers which are programmable resources provided for each thread since there are many registers. But for the next program counter and the program counter which are programmable resources provided for each thread a register file is not used since these are small registers.

As mentioned later a thread is selected for each computing cycle by the reservation station units and execution of entry of the selected thread is instructed to the operand address generators and computing units and and operand data of the thread selected from the register file is read and written whereby the simultaneous multi thread processing is executed.

In this embodiment the case of two threads threads and operating simultaneously is described but the present invention can also be implemented even if the number of threads is three or more.

In composing elements the same as are denoted with a same symbol and the reservation units and are connected to a thread selection circuit and an execution entry selection circuit .

The threads and are shared for the entries in the reservation station units and . In other words an entry stores a thread ID to indicate a thread of the entry a signal to instruct to read the operand data from the architecture register and the read address a signal to instruct to read from the register update buffer and the read address and an instruction identifier to indicate a number of an instruction to be allocated to each instruction when the instruction is decoded for example.

The architecture registers and of the two threads are constructed by a register file where threads which can be read simultaneously and threads which can be written simultaneously are integrated. The read thread and the write thread need not be the same.

As depicts the register file is comprised of the architecture registers and of the threads and a read thread selection circuit and a read operand selection circuit .

The thread selection circuit selects a read thread reads a read thread ID and sends it to the read thread selection circuit . The read thread selection circuit selects the architecture register and of a thread indicated by the read thread ID. Then the read address included in the execution entry is sent from the execution entry selection circuit to the read operand data selection circuit .

The read operand data selection circuit reads data of a portion required for function execution circuits and according to the read address so as to be used for execution of a function. The execution entry selection circuit selects an entry to be executed from the reservation station reads data on the portion required for executing a function from the register file register update buffers and and immediate value register and executes the function.

This operation will now be described. When a plurality of threads run in a simultaneous multi thread system the entry configuration of the reservations and are shared by the threads. The architecture register or is provided for each thread and is constructed by the register file .

When the operand data required for executing a function is read from the register file a thread to be read from the register file is selected in advance using the register read ID of the thread selection circuit . Also the number of threads to be read is limited to the number of threads smaller than the number of threads of the architecture register or .

Since the thread to be read is predetermined the register file can select the architecture register or at an early stage before the execution entry is selected by the execution entry selection circuit .

The circuits of the portion to select the architecture register or increase but the wiring amount of the circuits can be decreased because the architecture register of the thread to be read is already selected. When a function is executed data required for the execution is selected by operand selection units and but if the architecture register of the thread to be read is not selected the operand data for the amount of threads is sent from the architecture register to the operand selection units and . By selecting the architecture register of the thread to be read in advance the wiring amount to the operand selection units and can be decreased.

In this way by predetermining a thread to be read from the register file required operand data can be efficiently read from the register file and conventional frequencies could be exceeded if a semiconductor superior to conventional semiconductor technology is used.

The thread selection circuit selects a thread to be read from the register file in advance. When the reservation stations to execute different functions such as RSA and RSE read the operand data from a same register file read control is performed by the thread selection circuit in the register file so a same thread is used when the operand data is read from the register file in the entries executed by the reservation stations and .

When the operand data is read from locations other than the architecture registers and by the entries of the reservation station units and all the threads can be read simultaneously unlike the case of reading data from the architecture registers.

In other words the data other than the architecture registers and from which data is acquired in executing a function are used the register update buffers and and the immediate value register constructed by a work register which are not observed by a program. When the data in these registers is used as operand data the threads can be simultaneously read without restriction.

The instruction execution control device in will be described in detail. is a block diagram depicting the reservation station in is a block diagram depicting the register file and function execution circuit in is a diagram depicting the register file in is a diagram depicting entry execution selection operation of the reservation station in and is a diagram depicting the entry registration operation of the entry generation circuit in .

As depicts the reservation station unit for computing has an entry generation circuit a reservation station for computing and an execution entry selection circuit .

In the same way the reservation station unit for main storage operand generation has an entry generation circuit a reservation station for storage memory operand generation and an execution entry selection circuit .

The thread selection circuit receives a thread ID of an instruction decoded by the instruction decoder and selects a thread and notifies the selected thread to the entry generation circuits and the reservation stations and and a register read ID buffer as one thread selection method as described later.

As described in the reservation stations and receive the selected thread ID from the thread selection circuit in each cycle in order to execute an out of order processing and assigns priority to entries so that an entry for which required operand data is ready is executed with priority.

The execution entry selection circuit or selects an entry to be executed out of the entries registered in the reservation station or and outputs it to the computing unit or the like. When a plurality of entries are ready to be executed then the execution entry selection circuit or selects and executes from an older entry of the entries.

In the same way the entry generation circuit receives the selected thread ID from the thread selection circuit at a stage where an entry is registered in the reservation station or and assigns priority to entries so that an entry of which required operand data is complete is executed with priority as described in .

In order to control this priority the thread selection circuit selects a thread one cycle before the execution entry selection circuit or selects an entry of the reservation station or . This selection thread ID is sent to the register file via the register read ID buffer so a thread to be read in the register file is determined in advance.

Therefore the architecture register or can be selected at an early stage before the execution entry is selected by the execution entry selection circuit or .

The entry execution selection operation of the reservation station or will now be described with reference to . The reservation station or checks whether or not the registered valid entry is an entry for reading the operand data required for execution from the architecture register S .

If it is decided that this entry is an entry for reading operand data from the architecture register it is judged whether or not the ID of this entry matches the ID of the thread selected by the thread selection circuit which selects a thread to be read from the register file in one previous cycle of the execution entry circuit or S .

If it is decided that this entry ID matches the ID of the selected thread in step S the entry is judged as an entry which has a possibility to be selected by the execution entry selection circuit or in the next cycle and a 1 flag is assigned to this entry S .

If it is decided that this entry ID does not match the ID of the selected thread then the entry is decided as an entry which has not possibility to be selected by the execution entry selection circuit or in the next cycle and a 0 flag is assigned to this entry S .

If the entry is decided as an entry which the operand data required for execution is read from a register update buffer other than the architecture register or if the entry is decided as an entry which uses an immediate value in step S the entry can be executed regardless the thread of the entry in the reservation station or . Therefore the reservation station or judges whether or not the entry is ready for execution S .

If it is decided that the entry is ready for execution this entry is decided as an entry which has a possibility to be selected by the execution entry selection circuit or in the next cycle and a 1 flag is assigned to the entry S .

If it is decided that this entry is not ready for execution then the entry is decided as an entry which has no possibility to be selected by the execution entry selection circuit or in the next cycle and a 0 flag is assigned to this entry S .

In this way it is judged whether or not the entry registered in the reservation station or is an entry for reading the operand data from the register file. And if it is decided that this entry is an entry for reading the operand data it is checked whether or not this entry is an entry of the selected thread. And if it is decided as the entry of the selected thread this entry is recognized as an entry which has a possibility to be selected to be executed in the next cycle.

Therefore this entry can be selected by the execution entry selection circuit or and executed in the next cycle. Thereby even if the architecture register is selected first using the thread ID this entry matches the entry to be executed in the next cycle and as a result the simultaneous multi thread system can be smoothly executed.

The register file can be selected more quickly when this prioritization is performed in multiple stages. For example this prioritization is suitable for the current window system which is described in and .

The prioritization operation by the entry generation circuit or will now be described with reference to . is an entry selection operation in a cycle where an instruction is decoded and the entry generation circuit or registers a new entry in the reservation station or . When the entry generation circuit or receives the instruction to create an entry the reservation station or from the instruction decoder the entry generation circuit or checks whether or not the entry to be registered is an entry for reading operand data required for execution from the architecture register S .

If this entry is judged as an entry for reading operand data from the architecture register it is judged whether or not the ID of this entry matches the ID of the thread selected by the thread selection circuit which selects a thread to be read from the register file in this cycle S .

If it is decided that this entry ID matches the ID of the selected thread in step S the entry is decided as an entry which has a possibility to be selected by the execution entry selection circuit or in the next cycle and a 1 flag is assigned to this entry S .

If it is decided that this entry ID does not match the ID of the selected thread then the entry is decided as an entry which has no possibility to be selected by the execution entry selection circuit or in the next cycle and a 0 flag is assigned to this entry S .

If the entry is decided as an entry which reads the operand data required for execution from the register update buffer other than the architecture register or if the entry is decided as an entry which uses an immediate value in step S the entry can be executed regardless the thread of the entry to be registered. Therefore the entry generation circuit or judges whether or not the entry is ready for execution S .

If it is decided that the entry is ready for execution this entry is decided as an entry which has a possibility to be selected by the execution entry selection circuit or in the next cycle and a 1 flag is assigned to the entry S .

If it is decided that this entry is not ready for execution then the entry is decided as an entry which has no possibility to be selected by the execution entry selection circuit or in the next cycle and a 0 flag is assigned to this entry S .

In this way the entry generation circuit or checks whether or not the entry to be registered is an entry for reading the operand data from the register file in the entry registration cycle in the reservation station or . And if this entry is decided as an entry for reading the operand data the entry generation circuit or checks whether or not the entry is an entry of the selected thread. And if it is decided as the entry of the selected thread this entry is recognized as an entry which has a possibility to be selected to be executed in the next cycle.

Therefore this entry can be selected by the execution entry selection circuit or and executed in the next cycle. Thereby even if the architecture register is selected first using the thread ID this entry matches the entry to be executed in the next cycle and as a result the simultaneous multi thread system can be smoothly executed.

Now the register configuration of the architecture register in the register file in the out of order system will be described with reference to . The architecture register or installed for each thread is constructed by huge registers.

In these architecture registers a portion of the register required for executing an instruction is limited to the portion indicated by the current window pointer CWP which is provided for each thread. So the portion of the register indicated by the current window pointer CWP is copied from the architecture register A the copied portion is stored in the current window register CWR C.

In order to copy this portion from the architecture register A to CWR C the portion is stored once from the architecture register A to the CWR replacement buffer CRB B and is then stored in CWR C.

When the portion of the register of the current window pointer CWP is stored in CWR C one portion of one register before and after the current window pointer CWP is also stored in CRB B. For example in the case of the current window pointer CWP 1 three blocks of CWP 1 of the architecture register A are stored in CWR C and CRB B stores the above two blocks of CWP 0 or below two blocks below of CWP 2 in the architecture register A.

CWR C and CRB B are provided for each thread and are constructed by a register file which has only one thread that can be read at the same time just like the architecture register A.

Reading operand data required from the architecture register via the reservation station or involves reading operand data from CWR C. While executing an instruction to change the current window pointer e.g. SAVE and RESTORE instructions the operand data may be read from CRBB.

Using this register configuration for a huge architecture register can improve the throughput of data read and decrease register amount in the out of order instruction execution system e.g. see Japanese Patent Application Laid Open No. 2007 87108 .

As depicts the register file has architecture registers A and A provided for each thread CRB B and B provided for each thread and CWR C and C provided for each thread as depicted in . Each of CRB B and B has a read thread selection circuit and read operand data selection circuit . Each of CWR C and C has a read thread selection circuit and read operand data selection circuit .

A register read thread ID of the register read thread ID buffer is sent to the respective read the thread selection circuit of CRB B and B and CWR C and C. A selection entry including operand address from the execution entry selection circuit is sent to CRB B B CWR C and C the register update buffer the immediate value register and a latch circuit respectively.

A selection entry including operand address from the execution entry selection circuit is sent to CRB B B CWR C C the register update buffer the immediate value register and a latch circuit respectively.

For this according to the register read ID and the entry selected by the execution entry selection circuit or the operand data is read from the CWR C C CRB B B the register update buffer and the immediate value register . Out of these operand data the operand selection circuit or selects the operand data required for executing a function and sends the selected operand data to the computing unit or operand address generator via the latch circuit or so as to execute the function specified by the entry.

In this case as well the thread ID is selected before the entry selection cycle. Since either CRB B or CRB B and either CWR C or C are selected by the thread ID in advance the specified operand data can be read immediately if the entry is selected.

An address of the entry of the register update buffer can be used when reading the operand data required for execution from this register update buffer . Hence the operand data of different threads can be read simultaneously.

Therefore when the entries of the reservation station or execute the entries including reading the operand data required for executing a function from the register update buffer entries which are ready to be executed can be selected by the execution entry selection circuit or in each cycle without being restricted by the thread ID which is read from the register file just like the case of reading from the architecture register A A .

Now update processing of the architecture register by executing a function will be described with reference to . To execute functions by the computing unit and the operand address generator the operand data can be read from the register update buffer or the immediate value register is used other than the architecture registers A and .

As depicts the register update buffer is a register which is not observed by a program which stores data on the result of the execution of the function and the entry can be shared and used by threads and .

The execution result data written in the register update buffer is held in the register update buffer until the executed instruction is completed. When the instruction is completed an instruction completion is transmitted from CSE in the data is read from the register update buffer and written to the architecture register A A and CWR C C .

For subsequent instructions the functions can be executed by reading the operand data from the register update buffer until the function execution result is written to the architecture register A A from execution to completion of the instruction .

The thread selection circuit to select the thread will now be described. is a diagram depicting a thread selection method of the thread selection circuit is a diagram depicting the third selection method in and are diagrams depicting the fourth selection method in and to are circuit diagrams of the thread selection circuit .

As depicts there are four types of selection methods of the thread selection circuit for a register read ID and register read ID in the next cycle is determined according to these selection conditions. If the four types of selection conditions are not applicable the opposite thread of the register read ID is selected for the register read ID in the next cycle S .

In the first selection method it is judged whether or not a thread is specified S . The first selection method has highest priority in the thread selection circuit and if a thread is specified the thread selection circuit always selects a thread to be specified. The case when the read thread of the register is specified is a case when the current window pointer is changed.

In other words as described in when a current window pointer is changed the register portion indicating the changed current window pointer CWP of the thread and the pointers before and after the current window pointer are read from the architecture register A.

This data is written to CRBB and by reading it from the CRBB and then writing it to CWRC CWRC with the new window pointer can be provided.

During transition processing of the register from the change of the current window pointer CWP to setting of the new window pointer the thread of which changed the current window pointer has a priority in reading the architecture register A the read and write of CRBB and the write to CWRC. This means that a thread which can read and write the register file is restricted to the thread of which changed the current window pointer.

Therefore during register transition processing the thread which is executing the register transition processing and a thread selected by the thread selection circuit which selects a thread to be read from the register file will match. The register transition processing is controlled so that it can be processed only by one thread at the same time and cannot be processed by two threads at the same time.

In this way while the thread to read and write the register file is restricted during the transition processing of the register it is controlled such that the thread selection circuit always selects a thread the same as the thread of the transition processing of the register. As a result the entry which is executed by the reservation station and which reads an operand data from the architecture register matches the thread in the transition processing of the register. In this way the thread selection circuit during the transition processing of the registers operates so as to restrictively select the thread in the transition processing of the register.

In the processing in the middle of execution of the instruction to change the current window pointer CWP the reservation station may read the operand data from CRBB when the operand data is to read from the architecture register until the current window pointer CWP is changed.

At this time the thread selection circuit selects the thread which is changing the current window pointer so that the operand data is not read from CRBB during execution of an instruction to change the current window pointer from the reservation station when the opposite thread changes the current window pointer and the thread to read and write CRBB and CWRC restricts the current window pointer CWP.

There are three thread selection methods when a thread is not limited to a specific thread. A first selection method when a thread is not limited to a specific thread second selection method is that the thread selection circuit selects an operating thread when the operating thread is a single thread S .

A second selection method when a thread is not limited to a specific thread third selection method is to select an opposite thread of a thread which cannot be issued when such an entry which cannot be issued exists S . In other words if at least one entry which is ready to be executed exists in the entries of the reservation stations and for computing and for generating a main storage operation address and no entries in the opposite thread are ready to be executed the thread where at least one entry can be executed is selected.

The state in which the entry of the reservation station or can be executed is a state in which an entry in each thread is valid and is not interlocked or in which an entry is null but an entry has a possibility to become valid in the next cycle.

In an entry of the reservation station or information for controlling not to execute the entry interlock function even if the entry can be ready to be executed is provided as a signal of the entry.

Once this signal is set this entry is not selected by the execution entry selection circuit or and cannot be executed but after reset this entry can be executed and can be selected by the execution entry selection circuit or .

When detecting a state where the entry of the thread is valid and is not interlocked or a state where the entry is null but the entry has a possibility to become valid in the next cycle it is judged whether or not the entry in the thread is valid and is not interlocked or the entry has a possibility to become valid in the next cycle even if the entry is null S . If the entry of the thread is valid and is not interlocked or if the entry has a possibility to become valid YES the thread selection based on the third selection method is not executed.

Next if the entry of the thread is not valid and is interlocked or if the entry has no possibility to become valid NO then it is judged whether or not a signal to clear all the entries of the thread was issued to the thread . And if the signal to clear all the entries was issued to the thread thread selection is not executed in this selection circuit S . If the clear signal was not issued to the thread the thread is selected.

Whereas if it is detected that the entry of the thread is valid and is not interlocked or the entry is null but the entry has a possibility to become valid in the next cycle it is judged whether or not the entry of the thread is valid and is not interlocked or the entry has a possibility to become valid even if the entry is null S . If the entry of the thread is valid and is not interlocked or if the entry has a possibility to become valid YES the thread selection based on the third selection method is not executed.

If the entry of the thread is not valid and is interlocked or if the entry has no possibility to become valid NO then it is judged whether or not a signal to clear all the entries of the thread was issued to the thread . And if the signal to clear all the entries was issued to the thread this selection circuit does not select a thread S . If the clear signal was not issued to the thread the thread is selected.

Referring again to according to the third selection method used when the thread is not limited to a specific thread called as fourth selection method if an instruction which is in a state of standby for execution and cannot be completed for a predetermined period is detected and if the instruction which cannot be completed exists in an entry of the reservation station as depicted in the thread of the instruction which cannot be completed in the current state is selected by the thread selection circuit at a predetermined interval S . This selection circuit is effective when two threads are operating.

This will be described in detail with reference to . It is detected whether or not the opposite thread of the thread of the instruction completed the last time is in a state where no instruction can be completed for a predetermined period S S . If not detecting in this state NO the thread selection by this method is not executed.

If in this state YES it is judged whether or not this is during the later mentioned thread ID operation period and if not during the operation period the thread selection in this method is not executed S .

If during the operation period it is judged whether or not an entry in the reservation station of which the instruction identifier of the valid entry in the reservation station for computing matches the instruction identifier of the instruction which cannot be completed in the current state exists S .

If exists this entry the thread of the instruction which cannot be completed unless a clear signal is issued is selected by the thread selection circuit S S .

In this state the thread is selected by the thread selection circuit at a predetermined interval as depicted in . The thread selection circuit selects a thread during the thread selection period and does not select a thread if it is not the thread selection period S .

If a signal to clear all the entries of a thread for separated all thread is issued the thread selection by this selection circuit is not executed for this thread to which the clear signal was issued S S .

This thread selection circuit is constructed by logical circuits. The circuit in is a circuit to implement the fourth selection method and the output thereof becomes input to the circuit in . The circuit in is a circuit to implement the third selection method and the output thereof becomes input to the circuit in . The circuit in is a circuit to implement the first and second selection methods and to output the final thread selection ID THREAD ID .

The circuit in the final stage in has an output AND gate one input inversion type AND gate one input inversion and output inversion type AND gate and a pair of OR gates and .

In FORCE THREAD  or FORCE THREAD  is a signal which indicates that the register is in transition processing and indicates the case of requiring to specify a thread. When this signal is ON the selection circuit by using the outputs of the OR gates and and this signal selects a thread which is turned ON by the AND gate or . In other words the first selection method described in step S in is executed. These two signals are not turned ON at the same time.

In THREAD  ONLY ACTIVE or THREAD  ONLY ACTIVE is a signal to indicate a thread which is operating in a single thread operation. These two signals are not turned ON at the same time. When this signal is turned ON the thread selection circuit selects a thread which is turned ON by the OR gates and and AND gate or . The second selection method in step S in is therefore executed.

In the circuit in RS VALID NOT INTLCK THREAD  ONLY signal and RS VALID NOT INTLCK THREAD  ONLY signal are output by the third selection method in and RSE COMP WAIT THREAD  and RSE COMP WAIT THREAD  are output by the fourth selection method in .

The circuit to implement the third selection method in has a pair of one input inversion type AND gates and a pair of one input inversion type AND gates and and a pair of OR gates and .

In RSE VALID NOT INTLCK OR THREAD  is a signal to indicate that there is at least one valid entry of thread which is not interlocked in the entries of the reservation station for computing.

 RSA VALID NOT INTLCK OR THREAD  is a signal to indicate that there is at least one valid entry of the thread which is not interlocked in the entries of the reservation station for generating the main storage operand address.

 IWR VALID OR THREAD  is a signal to indicate that the instruction of the thread is decoded by the instruction decoder. If one of these signals is ON it means that an entry which is ready for execution from the OR gate exists in the entries of thread of the reservation station.

When this signal of the thread from the OR gate is OFF and the signal CLEAR PIPELINE THREAD  to clear the entries of the thread is OFF RS VALID NOT INTLCK THREAD  ONLY is output from the AND gate via the AND gate and is input to the OR gate in . Therefore the circuit in selects the thread .

The same circuit configuration is used to select the thread . In other words RSE VALID NOT INTLCK OR THREAD  is a signal to indicate that there is at least one valid entry of the thread which is not interlocked in the entries of the reservation for computing.

 RSA VALID NOT INTLCK OR THREAD  is a signal to indicate that there is at least one entry of the thread which is not interlocked in the entries of the reservation station for generating a main storage operand address.

 IWR VALID OR THREAD  is a signal to indicate that the instruction of the thread is decoded by the instruction decoder. If one of these signals is ON it means that an entry which is ready for execution from the OR gate exists in the entries of the thread of the reservation station.

When this signal of the thread from the OR gate is OFF and the signal CLEAR PIPELINE THREAD  to clear the entries of the thread is OFF RS VALID NOT INTLCK THREAD  ONLY is output from the AND gate via the AND gate and is input to the OR gate in . Therefore the circuit in selects the thread .

The entry existence detection circuit has a coincidence circuit which detects the matching of the signal CSE OUT PTR THREAD  to indicate an instruction identifier of an instruction which will complete next and the signal RSE  IID to indicate an instruction identifier of a No. 0 entry of the reservation station for computing and AND gates to execute AND operation of a signal RSE  VALID THREAD  to indicate that the No. 0 entry of the reservation station for computing is valid in the thread and the output of the coincidence circuit .

Therefore if the output of the entry existence detection circuit is ON it means that the first instruction of the thread exists in the reservation station for computing. This existence detection circuit is provided in a number corresponding to n number of entries of the reservation station for computing respectively and if one of the entries establishes by the OR gate a signal to indicate the existence in the reservation station for computing is output by the first instruction of the thread .

In the AND gate a signal LAST COMMIT THREAD ID  to indicate that the thread of the instruction which completed the last time is the thread a signal TOQ EU COMP WAIT THREAD  to indicate that the first instruction is in computing wait state a signal WARNING TO COMIT THREAD  to indicate that the instruction of the thread is not completed for a predetermined period and a signal RSE COMP WAIT MODE to indicate that this is a period selected by the thread selection circuit have been input.

When all of these input signals are ON and the CLEAR PIPELINE THREAD  which is a signal to clear is OFF if the signal that the first instruction of the thread from the OR gate exists in the reservation station for computing is output the RSE COMP WAIT THREAD  signal is asserted from the AND gate .

Further if there is no thread which is selected by any of the above mentioned four types of patterns the thread opposite the thread indicated by the register read ID has the register read ID in the next cycle since two threads operate simultaneously as described in step S in .

In the circuit in the signal with opposite polarity of the signal GPR READ THREAD ID to indicate the register read ID is input to the OR gate which determines the OR with the logic to select the thread side whereby if all the above mentioned conditions are not established the next cycle register read ID can select the opposite thread of the register read ID.

In the above mentioned embodiments the simultaneous multi thread system in which two threads threads and simultaneously operate was described but the present invention can be applied to the system in which three or more threads operate simultaneously. The architecture register was described using a divided register configuration based on the current window pointer in but can also be applied to other configurations.

The present invention was described above using the embodiments but the present invention can be modified in various ways within the scope of the spirit of the present invention and these variant forms shall not be excluded from the scope of the present invention.

When a plurality of threads are operated by the simultaneous multi thread system an architecture register is provided for each thread and a thread to be read from the register file is selected in advance when reading the operand data required for execution of the function from the register file so the architecture register can be selected at an early stage. The number of circuits in a portion for selecting the architecture registers increases but the wiring amount of circuits can be decreased because the architecture register of the thread to be read is selected in advance.

When reading the operand data from a location other than the architecture registers by the entry of the reservation station all the threads can be simultaneously read unlike the case of reading from an architecture register without restrictions by the threads which are read simultaneously.

