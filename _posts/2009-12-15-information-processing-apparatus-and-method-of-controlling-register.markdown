---

title: Information processing apparatus and method of controlling register
abstract: An information processing apparatus and a method of controlling the same that employs a register window system and a Simultaneous Multithreading method for reducing circuit areas by sharing a data transfer bus between threads, said bus connecting a master register and a work register provided for each thread and for avoiding interference in instruction execution with other threads caused by a conflict between accesses to a register between threads. An information processing apparatus and a method of controlling the information processing apparatus employing a register window system for register reading, in which a master register and a work register are held for each thread and a bus for transferring data from the master to the work register is shared by threads in order to realize Simultaneous Multithreading.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08019973&OS=08019973&RS=08019973
owner: Fujitsu Limited
number: 08019973
owner_city: Kawasaki
owner_country: JP
publication_date: 20091215
---
This application is a continuation application of International PCT Application No. PCT JP2007 000659 which was filed on Jun. 20 2007.

The present invention relates to an information processing apparatus adopting a register window system for executing Simultaneous MultiThreading and to a method of controlling the same.

In recent years a register window system has been suggested as a configuration of general purpose registers used in information processing apparatuses. This aims at provision of plural register sets windows in order to eliminate the need to save and restore information between registers and memory devices which results when subroutines are called or returned.

However when an immense number of windows are used data cannot be read from a register onto an execution unit at high speed which is problematic. In order to cope with this problem a method is suggested in which a window that is currently referred to among general purpose registers is held as a work register and this work register is made to operate as if it is cache memory in order to reduce time loss in reading or writing information that might result depending upon size.

However a configuration in which only 1 window that is being referred to currently is held as a work register requires that data be transferred to the work register each time the window is switched. Because data that should be referred to during the transfer does not exist subsequent instructions cannot be executed until the data transfer is terminated.

This configuration results in severe degradation in performance of information processing apparatuses in which a large number of simultaneous instructions are issued using an out of order instruction execution method wherein the order of executing instructions is changed so that execution of instructions starts from those that have become ready to be executed regardless of the execution order in the program.

Accordingly in information processing apparatuses using an out of order instruction execution method a large number of instructions are stored in a buffer and are executable instructions such instructions are executed after changing the execution order that was specified by the program so that the throughput of the instructions is improved.

However in the above configuration the execution order of instructions cannot be changed before or after window switching and thus executions of all instructions stored subsequently to the switching are required to wait and this prevents an out of order execution method from functioning.

Patent Document 1 proposed a method in which plural windows are held as a work register in order to solve the above problem. Using this method windows adjacent to the window that is being referred to are held as a work register set and thereby subsequent instructions can be executed without waiting for data transfer when windows are switched successively.

Also it is generally known that recent information processing apparatuses adopt a superscalar method by which processes of computations are parallelized as much as possible so as to increase efficiency in using respective execution units so that all aspects of the performance are improved.

However not all execution units operate in an information processing apparatus adopting a superscalar method and there is a problem in that the parallelism is not fully utilized. Thus Simultaneous MultiThreading SMT is suggested as a method by which resources peripheral circuits such as computing units and data transfer buses that are not fully utilized by a single thread can be distributed to plural threads so that the inherent parallelism of an information processing apparatus can be utilized at a maximum.

As a solution to realization of SMT it is conceivable to simply increase the number of resources in accord with the number of threads. This means that 2 SMTs are configured using twice as many resources as a single thread. In such a case there is no conflict between threads that are accessing the same resources. However an increase in the number of threads immensely increases the number of necessary resources which reduces efficiency in using such resources. This works against the inherent purpose of SMT.

In this situation a configuration is required in which resources are partially commoditized so that an increase in the number of resources can be suppressed and the efficiency in using such resources can be increased. Also partial commoditization of resources causes a problem in which a conflict between different threads accessing common resources interferes with instruction executions in other threads.

In view of the above situation it is an object of the present invention to provide an information processing apparatus and a method of controlling the same that employs a register window system and a Simultaneous Multithreading method for reducing circuit areas by sharing a data transfer bus between threads said bus connecting a master register and a work register provided for each thread and for avoiding interference in instruction execution with other threads caused by a conflict between accesses to a register between threads.

One aspect of the present invention is an information processing apparatus of a register window system for executing Simultaneous MultiThreading including a register set in which a master register and a work register are provided for plural threads and which includes a data transfer bus shared between the threads for transferring data from the master register to the work register an instruction analysis unit for decoding an instruction read from a memory device an instruction issue control unit for performing control to issue the decoded instruction to a computation unit for executing the decoded instruction an instruction completion control unit for obtaining an instruction execution result of the computation unit and for performing control for updating the register set on the basis of the execution result and a data transfer control unit for controlling data transfer from the master register to the work register.

Preferably a data transfer control unit includes a flag generation unit for receiving a work register rewrite request signal output for each of the threads from the instruction completion unit generating a flag instructing starting of LOAD CWP process of the thread specified by the work register rewrite request signal and outputting the flag to a data transfer timing control unit in order to perform a process of rewriting data in a work register for each of the threads a data transfer control counter for counting cycles for data transfer on the basis of the flag a data transfer timing control unit for controlling data transfer at a prescribed timing on the basis of the flag and cycles of the data transfer and an instruction issue inhibition control unit for outputting on the basis of the cycles for the data transfer an instruction inhibition signal for inhibiting the instruction during data transfer.

Preferably the trap detection unit is provided with a data transfer request signal generation unit for detecting a trap for each of the threads so as to generate trap information and for outputting to the data transfer control unit the trap information for each of the threads.

Preferably when the work register rewrite request is issued from the instruction completion control unit and the trap detection unit in the same thread the flag generation unit in the data transfer control unit provides an order of priority to the work register rewrite request signal generates a flag instructing starting of a LOAD CWP process of the thread specified by the work register rewrite request according to the order of priority and outputs the flag to the data transfer timing control unit.

Preferably the instruction completion control unit inhibits instruction commit until an instruction of a LOAD CWP instruction by a different thread is completed when the instruction completion control unit is notified by the instruction inhibition signal that a process of rewriting data in a work register is being executed by a different thread when the thread that issued an instruction commit request exists.

Preferably the information analysis unit inhibits decoding of the instruction when the instruction analysis unit receives the instruction inhibition signal from the same thread as the thread that issued an instruction decode signal when the instruction decode request has been issued.

The present invention is a method of controlling a register window for executing Simultaneous Multithreading including an instruction analysis step for decoding an instruction read from a memory device as an instruction pipeline an instruction issue control step for performing control to issue the decoded instruction to a computation unit for executing the decoded instruction an instruction completion control step for obtaining an instruction execution result of the computation unit and for performing on the basis of the execution result of the computation unit control for updating the register set in which a master register and a work register are provided for plural threads and which includes a data transfer bus shared between the threads for transferring data from the master register to the work register and a data transfer control step for controlling data transfer from the master register to the work register.

Preferably the data transfer control step includes a flag generation step for receiving a work register rewrite request output for each of the threads and for generating a flag instructing starting of a LOAD CWP process in the work register rewrite request thread in order to perform a LOAD CWP process which is a process of rewriting data of the work register for each of the threads a data transfer control counter step for counting cycles for data transfer on the basis of the flag a data transfer timing control step for controlling data transfer at a prescribed timing on the basis of the flag and cycles of the data transfer and an instruction issue inhibition control step for inhibiting on the basis of the cycles for the data transfer the instruction during data transfer.

Preferably a trap is detected for each of the threads so as to generate trap information and the work register rewrite request is generated for each of the threads.

Preferably the flag generation step in the data transfer control step provides an order of priority for each of the threads and generates a flag instructing starting of a LOAD CWP process of the thread specified by the work register rewrite request based on the priority order.

Preferably the instruction completion control step inhibits instruction commit until a LOAD CWP instruction by a different thread is completed when it is reported that the LOAD CWP process is being executed by a different thread when the thread that issued an instruction commit request exists.

Preferably the instruction analysis step inhibits decoding of the instruction when the instruction inhibition was reported by the thread that issued an instruction decode request when the instruction decode request was issued.

According to the present invention a data transfer bus for connecting a master register and a work register adopting a register window system is shared by threads and thereby circuit areas can be reduced and interference of instruction executions with other threads caused by a conflict in accesses to registers between threads can be avoided.

In the examples below explanations will be given for an information processing apparatus that adopts a register window system and performs Simultaneous MultiThreading SMT .

An information processing apparatus according to the present example includes for plural threads a register set general purpose register or the like consisting of a master register and a work register that are based on a register window system and are for holding computation results and data needed for computations.

The register sets are required to allow each thread to refer to the number of registers specified by the architecture. Further the values in a master register assigned to each thread are not allowed to be updated by instructions given by other threads. Thus a master register is prepared for each thread.

When only one work register is used a work register has to be switched each time a different thread starts referring to the register so that a particular time is required to transfer data from a master register to a work register. This results in a great time loss in switching a work register and in referring to a register. Thus a work register is multiplexed together with a master register and the data transfer bus necessary for switching a work register is commoditization between threads. Also data transfer that is necessary for reflecting computation results on a work register from a computation unit as instruction execution resources is performed by using the commoditized data transfer bus described above.

Also commoditization of a transfer bus connecting a master register and a work register prevents plural data transfers from being conducted simultaneously. Thus control is performed so that plural requests to transfer data from a master register to a work register are not made simultaneously by threads.

Also control is performed so that transferring of data from a master register to a work register does not coincide with the writing of computation results which can otherwise result from the commoditization of a data transfer bus between the computation unit and a work register as well.

Specifically data needs to be transferred from a master register to a work register when a SAVE instruction a RESTORE instruction or a CWP switching instruction such as a WRCWP instruction is executed a trap has occurred or a DONE RETRY instruction is executed. Control is performed so that those cases coincide between different threads in order to inhibit those cases from occurring during a data transfer process. Also control is performed so that computation results or the like are not written to a work register during a data transfer process.

The memory device functions as cache memory in the information processing apparatus . The memory control unit controls the memory device and the computation unit . The memory control unit outputs to the instruction analysis unit codes instructions read from the memory device .

The instruction analysis unit decodes codes provided from the memory control unit . The instruction issue control unit controls issuing of instructions to resources that are used for performing processes corresponding to the decoded codes.

The computation unit performs computations or the like on the basis of operands provided from the memory control unit and the instruction issue control unit .

The general purpose register provides a master register and a work register for each thread and is controlled by the data transfer control unit the instruction completion control unit etc.

The instruction completion control unit is connected to the computation unit the instruction issue control unit the general purpose register and the data transfer control unit and obtains from the computation unit the results of executions of instructions corresponding to codes issued by the instruction issue control unit in order to update the general purpose register cancel the inhibition condition in the instruction analysis unit and the instruction issue control unit and output a LOAD CWP request for controlling the data transfer control unit in accordance with the execution results.

The trap detection unit detects a trap and outputs to the data transfer control unit a LOAD CWP request trap information of the trap detection unit .

The data transfer control unit is connected to the trap detection unit the instruction completion control unit the instruction issue control unit and the general purpose register and controls data transfer to the general purpose register and also controls types of transferred data timings of transfer and etc.

Next illustrates operations of each thread in the information processing apparatus . An instruction pipeline of a thread includes a Fetch stage a Decode stage a Dispatch stage an Execute stage an Update Buffer stage and a Commit stage.

The Fetch stage reads instructions from the memory device on the basis of control performed by the memory control unit .

The Dispatch stage issues on the basis of control performed by the instruction issue control unit instructions to instruction execution resources such as the computation unit .

The Execute stage executes on the basis of instructions issued by the Dispatch stage instructions issued in instruction execution resources such as the computation unit .

The Commit stage updates on the basis of control performed by the instruction completion control unit content in the memory device and the general purpose register in the order of instructions and in accordance with the results of executing instructions in the Execute stage.

Among those stages a Fetch stage a Decode stage and a Commit stage operate in an in order manner in other words they operate in accordance with an execution order. By contrast a Dispatch stage an Execute stage and an Update Buffer stage operate in an out of order manner which means that the order of data being processed starts with whichever piece of data is ready to be processed regardless of the execution order.

Next the master register and the work register constituting the general purpose register will be explained by referring to . illustrates the relationship between the master register and the work register .

The master register hereinafter referred to as an MRF Master Register File is composed of windows connected to form a ring. The MRF is managed by a CWP Current Window Pointer .

The work register hereinafter referred to as a WRF Working Register File is composed of a window specified by a CWP and adjacent windows on both sides of that window.

Also the WRF includes a global register that can be used regardless of a CWP global for normal global for trap a local register unique to each of the windows an in register that allows overlaps between the windows and an out register.

The MRF and the WRF are provided for each thread and they are connected to each other by a data transfer bus as illustrated in the general purpose register in and a control bus not illustrated . The data transfer bus is controlled by bus path switching performed by selectors and . The switching may be controlled for example by the data transfer control unit or the like or may be controlled by providing circuits that are not illustrated.

The MRF is composed of local registers local through local in registers in through in out registers out through out for 8 windows a global register global for normal of 8 words used for normal operations and a global register global for trap of 8 words used for trap processing.

One of the windows in the MRF is composed of a local register of 8 words an in register of 8 words and an out register of 8 words. Also it is configured so that in x overlaps out x of an adjacent window when CWP x. For example in overlaps out after the wrap around.

The WRF for a thread is composed of 3 windows on the basis of the specification by a CWP and is composed of 64 words in total which consists of 8 words each for local x 1 local x and local x 1 8 words each for in x 1 in x and in x 1 and 8 words for out x 1 and 8 words for a global register.

A bus with a 16 word width specifically 8 words for in and out registers and 8 words for local and global registers is prepared for data transfer from the MRF to the WRF and this is shared by different threads so that data is transferred while switching as necessary between threads that occupy the data transfer bus .

Switching of windows is performed when the values of a CWP change due to incrementing or decrementing of CWP and due to execution of an instruction to rewrite the values into arbitrary values that are not successive. Hereinafter an instruction to increment a CWP is referred to as a SAVE instruction an instruction to decrement a CWP is referred to as a RESTORE instruction and an instruction to change a CWP into arbitrary values that are not successive is referred to as a WRCWP instruction.

The computation unit is connected to the WRF so that it can read data held in the WRF and the computation unit executes instructions specified by the data being held SAVE instructions to increment a CWP and RESTORE instructions to decrement a CWP.

Also the computation unit is connected to the MRF and the WRF so that it can write information to the MRF and the WRF and executes a writing process both to the MRF and the WRF simultaneously.

When a SAVE instruction or a RESTORE instruction is being executed the WRF is composed of three windows specified by a CWP after movement. Specifically when the register specified by a CWP before movement is x the three windows x x 1 and x 2 are used for a SAVE instruction and the three windows x 2 x 1 and x are used for a RESTORE instruction. Because two of the three windows are already held by the WRF only the data for the local register and in out registers of one window which is lacking is required to be transferred from the MRF to the WRF . Because the windows x 1 and x 1 are each already held by the WRF for cases of SAVE and RESTORE instructions as data for the moved CWP data reading can be executed without waiting for the data to be transferred from the MRF i.e. without loss in time.

During the execution of a WRCWP instruction when the register specified by the moved CWP is y the WRF is composed of the three windows y 1 y and y 1. Because it is not guaranteed that data will still be held after a CWP has moved to the WRF in the case of WRCWP a local register and in out registers that are necessary to compose the three windows based on window y are transferred from the MRF to the WRF . During this data reading from window y is not executable because the data cannot be referred to and when the transfer has been completed subsequent instructions are executed to the updated WRF .

Also when a trap occurs during the execution of a process the values in the register at the time when the trap occurred have to be held because values and operations that do not depend on normal operations are needed or because such values are needed for restarting the process. Thus the global register is switched to one dedicated to a trap process so that a trap process is executed. For portions depending upon normal operations in out registers and local register are referred to.

When a trap process is performed a particular instruction is executed and the global register is again switched from the state for the trap process to the state for normal operations in order to restart the process. The portions necessary for normal operations are reflected through the in out registers and the local register an instruction executed upon the termination of a trap process is referred to as a DONE RETRY instruction .

For example a case is assumed where there are two threads the number of threads in the same cycle is limited to one in issuing instructions referring to registers writing to registers and completing instructions and a CWP is changed by SAVE RESTORE instructions in each cycle as necessary. Data transfer from the MRF to the WRF is executed after the completion of a change of a CWP by the SAVE RESTORE instructions Commit stage . At that time the amount of data that needs to be transferred to the WRF is 16 words consisting of eight local words and eight in out words and that data is transferred in one cycle through the data transfer bus which is 16 words in width. Instructions subsequent to the SAVE RESTORE instructions in the same thread have to refer to rewritten data however they can refer to correct data without waiting for the completion of the data transfer because the WRF also holds the window specified by the CWP and the adjacent windows. Also even in a case when there is an instruction to update the WRF such as SAVE RESTORE instructions and a WRCWP instruction subsequent to the same thread a conflict of transfer bus can be avoided because the data transfer can be completed in one cycle so that updating of WRF is completed before issuing a request to update the WRF . Further even when a request to update the WRF is issued in next or subsequent cycles a conflict of data bus is not caused because the data transfer has been completed in one cycle.

Next a case in which a CWP is changed by a WRCWP instruction is described. Transfer of data from the MRF to the WRF is executed after the completion of a change of CWP by using a WRCWP instruction. In this all data in the WRF has to be rewritten to data of the windows based on the changed CWP and accordingly the amount of data that needs to be transferred is 64 words and the data is transferred in 4 cycles using a bus that is 16 words in width. This process of rewriting all data in the WRF is herein referred to as a LOAD CWP process.

Similarly to the case of SAVE RESTORE instructions subsequent instructions in the same thread have to refer to rewritten data and accordingly correct data cannot be referred to until the completion of the data transfer. In this case as well POST SYNC control can inhibit subsequent instructions from referring to data before the completion of the execution of the instruction. Also even when there is an instruction to update the WRF which includes an instruction requiring a change of a CWP after the SAVE RESTORE instructions in the same thread conflicts can be avoided because five stages are taken between the issue and completion of the subsequent instructions.

However a LOAD CWP process takes four cycles to be completed and accordingly when issuing of subsequent instructions is restarted after the completion of an instruction the LOAD CWP process can still be in execution which means that it cannot be guaranteed that data can be referred to. Accordingly control has to be performed to inhibit subsequent instructions from being issued until the completion of a data transfer process even after the completion of the execution of an instruction.

When a trap has occurred all operations being executed are cancelled and thereafter data is transferred from the MRF to the WRF . The amount of data that has to be transferred to the WRF is 18 words for a global register. However when a trap has occurred it is necessary to cancel all instruction sequences for normal operations and thereafter fetch instruction sequences for a trap process from the memory device . This takes a substantial number of cycles because 3 stages i.e. a Fetch stage a Decode stage and a Dispatch stage have to be performed for canceling instruction sequences for normal operations fetching new instruction sequences and referring to updated registers. This means that prompt updating of the WRF is not necessary and accordingly a LOAD CWP process can be used instead of preparing a new logic in order to transfer 8 words for a global register from the MRF to the WRF so that the logic is simplified and fewer resources are used.

Also all operations of instructions that are being executed are cancelled when a trap has occurred and accordingly there is no conflict with a request based on an instruction in the same thread to transfer data from the MRF to the WRF when a LOAD CWP process is being performed or a LOAD CWP process starts. However traps occur irregularly and thus there is a risk that a trap can occur during the execution of another LOAD CWP process. This makes it necessary to perform control so that a conflict between LOAD CWP processes caused by a trap in the same thread is avoided.

Also a case of a DONE RETRY instruction upon the termination of a trap process requires that instruction sequences for a normal process be fetched from the memory device after the completion of the instruction meaning that prompt updating of the WRF is not necessary. Accordingly in this case too the updating of the WRF is performed by a LOAD CWP process.

Also the data transfer bus connecting the MRF and the WRF is shared by plural threads while the data transfer bus is occupied by one of them during a LOAD CWP process. Accordingly while a thread is executing a LOAD CWP process other threads cannot transfer data from the MRF to the WRF . This means that control has to be performed so that while a thread is executing a LOAD CWP process other threads suspend a process of updating the MRF .

The data transfer control unit includes a flag generation unit a data transfer control counter an instruction issue inhibition control unit a data transfer timing control unit and a data write control unit .

An instruction completion control unit and a trap detection unit are connected to the data transfer control unit .

In m MRFs and m WRFs Th through Th m are prepared for each thread and each of Th through Th m consists of 64 words total for local 8 words 3 in out 8 words 4 and global 8 words .

For data transfer from the MRFs to the WRF the data transfer bus that is 8 words total in width consisting of 4 words each for the in out and the local global. Accordingly data of 8 words can be transferred in 1 cycle.

The flag generation unit receives a LOAD CWP request on the basis of SAVE instructions RESTORE instructions and WRCWP instructions from the instruction completion control unit and the trap from the trap detection unit and the like and generates flags.

When a flag LOAD CWP GO TH m is generated by the flag generation unit instruction issue inhibition control is performed by the instruction issue inhibition control unit during data transfer from the MRF to the WRF and execution of subsequent instructions is inhibited. Also when a flag has been generated by the flag generation unit the counter value in the data transfer control counter that has received the flag is set to zero and the counting starts for the cycles required to transfer the data in accordance with the flag.

The data transfer timing control unit performs control in accordance with the flag and the counter value in the data transfer control counter in order to determine at what timing data is to be transferred from the MRF to the WRF provided for each thread transfer data selection . Specifically it controls while CWP x output of a signal for transferring data to the inx outx 1 register a signal for transferring data to the inx 1 outx register a signal for transferring data to the inx 1 outx 2 register a signal for transferring data to the inx 2 outx 1 register a signal for transferring data to the localx register a signal for transferring data to the localx 1 register a signal for transferring data to the localx 1 register and a signal for transferring data to the global register.

The data write control unit controls writing of data to the WRF . The data write control unit outputs on the basis of a counter value LOAD CWP COUNTER set by the data transfer control counter WE Write Enable for controlling wiring to the WRF of data transferred from the MRF . This is a signal MOVE I O WRITE ENABLE for controlling the WRF writing data to the in out register or a signal MOVE G L WRITE ENABLE for controlling the WRF writing data to the local global register.

The flag generation unit includes OR circuits and 2 input logical sum circuits latch circuits through an AND circuit 2 input logical product circuit and another AND circuit 3 input logical product circuit another OR circuit 2 input logical sum circuit a comparator and another AND circuit 2 input logical product circuit .

LOAD CWP REQ BY INST TH  and LOAD CWP REQ BY TRAP TH  are input into the OR circuit respectively from the instruction completion control unit illustrated in and the trap detection unit and the OR circuit generates LOAD CWP REQ TH  for thread Th in accordance with those inputs. Also LOAD CWP REQ BY INST TH  and LOAD CWP REQ BY TRAP TH  are input into the OR circuit and the OR circuit generates LOAD CWP REQ TH  for thread Th .

The output terminal of the OR circuit is connected to the SET terminal of the latch circuit and LOAD CWP REQ TH  for thread Th is input into the SET terminal of the latch circuit . Also the output terminal of the AND circuit is connected to the RST terminal reset terminal of the latch circuit . Also the output terminal of the latch circuit is connected to the a input terminal of the AND circuit and the a input terminal inversion input of the input terminal of the AND circuit .

The output terminal of the OR circuit is connected to the SET terminal of a latch circuit and LOAD CWP REQ TH  is input into the SET terminal of the latch circuit . Also the RST terminal reset terminal of the latch circuit is connected to the output terminal of the AND circuit . The output terminal of the latch circuit is connected to the b output terminal of the AND circuit .

The b input terminal inversion input of the AND circuit is connected to the output terminal of the latch circuit and is also connected to the c input terminal of the AND circuit and the b input terminal of the AND circuit 2 input logical product circuit . The output terminal of the latch circuit is connected to the input terminal 1 of a counter circuit data transfer control counter . The output terminal of the AND circuit is connected to the SET terminal set terminal of a latch circuit .

The output terminal of the AND circuit is connected to the SET terminal SET terminal of a latch circuit .

The output terminal of the AND circuit and the a input terminal of the OR circuit are connected to each other and the output terminal of the AND circuit and the b input terminal of the OR circuit are connected to each other. The output terminal of the OR circuit is connected to the SET terminal set terminal of the latch circuit .

The output terminal of the counter circuit is connected to the input terminal of the comparator through a bus that is 2 bits in width.

The output terminal of the comparator is connected to the a input terminal of the AND circuit . The output terminal of the AND circuit is connected to the RST terminal reset terminal of the latch circuit and is also connected to the RST terminals respectively of the latch circuit and the latch circuit .

LOAD CWP GO TH  is output from the output terminal of the latch circuit to the instruction issue inhibition control unit and the data transfer timing control unit . LOAD CWP GO TH  is output from the output terminal of the latch circuit to the instruction issue inhibition control unit and the data transfer timing control unit .

The instruction issue inhibition control unit includes an AND circuit 2 input logical product circuit another AND circuit 2 input logical product circuit a latch circuit and another latch circuit .

The a input terminal of the AND circuit is connected to the output terminal of the comparator and the a input terminal of the AND circuit .

LOAD CWP REQ TH  for thread Th is input into the SET input terminal of the latch circuit . The output terminal of the latch circuit is connected to the b input terminal of the AND circuit and the output terminal of the AND circuit is connected to the RST terminal reset terminal of the latch circuit .

LOAD CWP REQ TH  for thread Th is input into the SET input terminal set terminal of the latch circuit . The output terminal of the latch circuit is connected to the b input terminal of the AND circuit and the output terminal of the AND circuit is connected to the RST terminal reset terminal of the latch circuit .

In the configuration illustrated in LOAD CWP INTLK ALL LOAD CWP INTLK OWN TH  and LOAD CWP INTLK OWN TH  are fixed to high while a LOAD CWP process is executed. Also by suppressing other LOAD CWP requests while they are fixed in the high state a conflict between LOAD CWP processes is avoided.

LOAD CWP INTLK ALL is a signal for avoiding a conflict between threads is set to high at the same timing as a LOAD CWP process starting instruction is given to the general purpose register and is reset to low after four cycles.

LOAD CWP INTLK OWN TH  and LOAD CWP INTLK OWN TH  are signals for avoiding a conflict in a thread and when a LOAD CWP request is received these signals are set to high and after four cycles they are reset to a low . The timing of the resetting is determined by the fact that the effective cycle number of a LOAD CWP process is always a fixed cycle number 4 and the resetting timing of LOAD CWP INTLK can be changed even in a model with a different LOAD CWP process effective cycle number because of differences in the transfer bus width or the amount of data transferred.

Conflicts between threads in LOAD CWP processes are avoided by transmitting by using LOAD CWP INTLK ALL and to the general purpose register an instruction to start a LOAD CWP process in a logic as illustrated in .

First an explanation will be given for a case when a LOAD CWP process request has been issued from thread Th .

The latch circuit receives LOAD CWP REQ TH  LOAD CWP process request for thread Th sets LOAD CWP REQ HOLD TH  to high and checks LOAD CWP INTLK ALL in the next cycle.

Specifically when the output of the latch circuit LOAD CWP INTLK ALL is low the output of the latch circuit LOAD CWP GO TH  controlled by the AND circuit is set to high . Then LOAD CWP GO TH  is transmitted from the output terminal of the latch circuit to the general purpose register in the next cycle in order to start a LOAD CWP process.

When LOAD CWP INTLK ALL is high the AND circuit performs control so that setting of LOAD CWP GO TH  is inhibited and thereby a conflict is avoided between threads in a LOAD CWP process. Because high is input into the b input terminal of the AND circuit low is output from the output terminal of the AND circuit and is set in the latch circuit .

Because low is output from the AND circuit while LOAD CWP GO TH  as an output of the latch circuit is being inhibited low the value of LOAD CWP REQ HOLD TH  is held by the latch circuit .

When a LOAD CWP process that has been executed is completed LOAD CWP INTLK ALL becomes low and LOAD CWP GO TH  is set to high in the next cycle so that LOAD CWP processes are executed successively in thread without a conflict.

In the present example LOAD CWP GO TH  as an output of the latch circuit is set to high and an output of the AND circuit becomes high and thereby LOAD CWP REQ HOLD TH  as an output of the latch circuit is reset to low so that it can be ensured that threads selected by a LOAD CWP process request are in order. Thereby higher priority is given to the side of thread Th .

Next explanations will be given for an example in which the side of thread Th has issued a LOAD CWP request.

The latch circuit receives LOAD CWP REQ TH  LOAD CWP process request from thread Th sets LOAD CWP REQ HOLD TH  to high and checks LOAD CWP INTLK ALL in the next cycle. When LOAD CWP INTLK ALL is low the latch circuit sets LOAD CWP GO TH  to high in the latch circuit . In the Next cycle the latch circuit transmits LOAD CWP GO TH  to the general purpose register in order to perform control so as to start a LOAD CWP process.

When LOAD CWP INTLK ALL is high the latch circuit performs control so as to inhibit setting of LOAD CWP GO TH  in order to avoid a conflict between threads in a LOAD CWP process.

When setting of LOAD CWP GO TH  is being inhibited the value of LOAD CWP REQ HOLD TH  is held in the latch circuit . When a LOAD CWP process that has been executed is completed LOAD CWP INTLK ALL becomes low and accordingly LOAD CWP GO TH  is set to high so that LOAD CWP processes in thread Th can be executed successively without a conflict.

By resetting LOAD CWP REQ HOLD TH  to low and simultaneously setting LOAD CWP GO TH  to high the order of LOAD CWP process requests are secured between threads.

There is also a case when LOAD CWP REQ TH  and LOAD CWP REQ TH  are received at the same time. This occurs when LOAD CWP REQ HOLD TH  and LOAD CWP REQ HOLD TH  both become high . In this case there is no order and LOAD CWP GO TH  is set to high giving priority to the side of thread Th and thereby a conflict between threads can be avoided. As described above simplification of logic can reduce the number of mounting areas.

In the present example a case where there are two threads has been explained. However even when there is a larger number of threads Th through Th m a conflict can be avoided between threads in LOAD CWP processes by securing the order of LOAD CWP REQ HOLD TH  through LOAD CWP REQ HOLD TH m.

As described above a conflict can occur between requests for LOAD CWP processes in the same thread when a LOAD CWP process occurs due to a trap while another LOAD CWP process is being executed. A conflict between LOAD CWP processes in a thread caused by a trap can be avoided by a data transfer request signal generation unit included in the trap detection unit in using LOAD CWP INTLK OWN TH  and LOAD CWP INTLK OWN TH  for transmitting to the instruction completion control unit a request for a LOAD CWP process.

The data transfer request signal generation unit on the side of thread Th illustrated in includes a latch circuit an AND circuit 2 input logical product circuit and a flip flop circuit .

When the trap detection unit has detected a trap it generates TRAP DETECT TH  and inputs it into the data transfer request signal generation unit .

The SET terminal of the latch circuit is configured to receive TRAP DETECT TH . The output terminal of the latch circuit is connected to the a input terminal of the AND circuit . LOA CWP INTLK OWN TH  which is output from the instruction issue inhibition control unit is input into the b input terminal of the AND circuit inversion input . The output terminal of the AND circuit is connected to the input terminal D of the flip flop circuit . The output terminal of the flip flop circuit is connected to the RST terminal rest terminal of the latch circuit .

The latch circuit receives TRAP DETECT TH  trap detection from thread and sets CANCEL OPERATION TH . The AND circuit cancels all instructions that are being executed by the side of thread Th in the cycle in which CANCEL OPERATION TH  became high and thereafter it checks LOAD CWP INTLK OWNTH .

The flip flop circuit sets LOAD CWP REQ BY TRAP TH  to high when LOAD CWP INTLK OWN TH  is low and transmits it to the data transfer control unit . At the same time the flip flop circuit outputs RE I FETCH REQ TH  and again starts fetching instruction sequences from the memory device . When LOAD CWP INTLK OWN TH  is high the flip flop circuit performs control so as to inhibit the setting of LOAD CWP REQ BY TRAP TH  so that a conflict with a LOAD CWP process that has already been executed in the same thread can be avoided.

By using LOAD CWP INTLK OWN TH  which has a set timing earlier than that of LOAD CWP INTLK ALL for inhibition of LOAD CWP REQ BY TRAP TH  control is performed so that setting intervals of LOAD CWP REQ HOLD TH  are made to be longer and a single thread cannot occupy the execution of a LOAD CWP process. In the present example a case where there are two threads has been explained. However even when there is a larger number of threads employing a configuration that enables securement of the order of LOAD CWP REQ HOLD TM m makes it possible to prevent a LOAD CWP process of a thread from being in an unexecutable state for an unnecessarily long time.

A conflict between LOAD CWP processes in a thread due to a trap on the side of thread Th can be avoided by using a circuit configuration similar to the above thread Th and performing control on the basis of LOAD CWP INTLK OWN TH  and TRAP DETECT TH  on the side of thread Th as input signals in order to transmit to the data transfer control unit LOAD CWP REQ BY TRAP TH  which is a request for a LOAD CWP process.

 Avoidance of Reference to WRF Made by Subsequent Instructions in the Same Thread During Execution of LOAD CWP .

Reference to WRF made by subsequent instructions in the same thread during the execution of a LOAD CWP is avoided by using LOAD CWP INTLK OWN TH  and LOAD CWP INTLK OWN TH  to control instruction decodes by using the instruction analysis unit illustrated in .

The instruction analysis unit on the side of thread Th illustrated in includes a latch circuit an AND circuit 3 input logical product circuit and a flip flop circuit .

The SET input terminal of the latch circuit recives an input of POST SYNC REQ TH  which is an internal signal of the instruction analysis unit and which becomes high when an instruction is specified by analysis to be instructions that require inhibition of decoding of subsequent instructions such as a WRCWP instruction as a result of decoding by means of the instruction analysis unit . COMMIT OPERATION TH  which is an output of the instruction completion control unit is input into the RST terminal of the latch circuit . The output terminal of the latch circuit is connected to the c input terminal of the AND circuit inversion input . DECODE OPERATION REQ TH  which is an internal signal of the instruction analysis unit is input into the a terminal and LOAD CWP INTLK OWN TH  which is an output of the data transfer control unit is input into the b input terminal inversion input . The output terminal of the AND circuit is connected to the input terminal D of the flip flop circuit . The output terminal of the flip flop circuit is connected to the instruction issue control unit .

On the AND circuit on the thread Th side if LOAD CWP INTLK OWN TH  is low when an instruction decode request DECODE OPERATION REQ TH  is issued instructions are decoded as they are. If LOAD CWP INTLK OWN TH  is high shifting to the Dispatch stage is avoided by inhibiting instruction decoding and instructions that need LOAD CWP processes are completed and thereafter reference to WRF made by subsequent instructions in the same thread during the execution of a LOAD CWP is avoided.

Similarly to the thread Th side control is performed by using POST SYNC REQ TH  COMMIT OPERATION TH  DECODE OPERATION REQ TH  and LOAD CWP INTLK OWN TH  so that reference to WRF made by subsequent instructions in the same thread during the execution of a LOAD CWP process can be avoided.

Avoidance of a conflict between a LOAD CWP process and an instruction to update the WRF in a different thread is realized by controlling an instruction commit by using the instruction completion control unit that uses LOAD CWP INTLK OWN TH  and LOAD CWP INTLK OWN TH .

The instruction completion control unit includes an AND circuit 2 input logical product circuit a flip flop circuit an AND circuit 2 input logical product circuit an AND circuit 2 input logical product circuit and an OR circuit 2 input logical sum circuit .

COMMIT OPERATION REQ TH  which is a commit request output from the computation unit is input into the a input terminal of the AND circuit on the side of thread Th . LOAD CWP INTLK OWN TH  output from the data transfer control unit is input into the b input terminal of the AND circuit inversion input . The output terminal of the AND circuit is connected to the input terminal D of the flip flop circuit .

The output terminal of the flip flop circuit is connected to the a input terminal of the AND circuit and the a input terminal of the AND circuit .

The oldest instruction from among a SAVE instruction a RESTORE instruction and a WRCWP instruction in other words LOAD CWP INST EQ OLDEST TH  which specifies the instruction that is to be committed next is input from the instruction issue control unit to the b input terminal of the AND circuit . LOAD CWP REQ BY INST TH  output from the AND circuit is output to the data transfer control unit .

To the b input terminal of the AND circuit a signal specifying that an instruction that executes an update of GPR such as an ADD instruction addition a SUB instruction subtraction or a LOAD instruction data read from memory is the instruction to be committed next WRITE GPR INST EQ OLDEST TH  is input. Output of the AND circuit WRITE GPR ENABLE BY INST TH  is a write enable signal connected to the WRF for thread Th in the general purpose register .

The AND circuit commits instructions as they are and rewrites the general purpose register with WRITE GPR ENABLE BY INST TH  being issued if LOAD CWP INTLK OWN TH  is low when an instruction that needs rewiring of the general purpose register on the side of the thread Th WRITE GPR INST EQ OLDEST TH  and a commit request COMMIT OPERATION REQ TH  occurred.

In the AND circuit instructions are committed as they are when an instruction commitment request is issued by LOAD CWP INST EQ OLDEST TH  and LOAD CWP INTLK OWN TH  is low and LOAD CWP REQ BY INST TH  is issued. Thereafter LOAD CWP REQ TH  which is the result of an OR operation between LOAD CWP REQ BY INST TH  and LOAD CWP REQ BY TRAP TH  is output from the instruction completion control unit and a LOAD CWP process starts.

When LOAD CWP INTLK OWN TH  is high in the AND circuit other threads are prevented from rewriting WRF until a LOAD CWP process is completed by inhibiting an instruction commit.

Similarly to the side of thread Th a conflict between a LOAD CWP process and in an instruction to update the WRF given by other threads can be avoided by using COMMIT OPERATION REQ TH  and LOAD CWP INTLK OWN TH .

When LOAD CWP INTLK OWN TH  is high it is not possible that an instruction requiring rewriting of the general purpose register is committed in thread Th in order to prevent decoding of subsequent instructions. Thus by utilizing the fact that the operations will not be influenced when an OR logical sum of LOAD CWP INTLK OWN TH  and LOAD CWP INTLK OWN TH  inhibits the committing of both threads a configuration can be used in which the inhibition logic of a commit is simplified into an OR logical sum of LOAD CWP INTLK OWN TH m of all threads even when the number of threads has increased.

In the vertical axis represents the waveforms of 1 LOAD CWP REQ TH  2 LOAD CWP REQ HOLD TH  3 LOAD CWP GO TH  4 LOAD CWP REQ TH  5 LOAD CWP REQ HOLD TH  6 LOAD CWP GO TH  7 LOAD CWP INTLK ALL 8 LOAD CWP COUNTER 9 data transfer bus MRF WRF 10 WRF Th 11 WRF Th 12 LOAD CWP INTLK OWN TH  13 LOAD CWP INTLK OWN TH  14 LOAD CWP REQ BY TRAP TH  15 DECODE OPERATION TH  16 COMMIT OPERATION TH  17 LOAD CWP REQ BY TRAP TH  and 18 DECODE OPERATION TH . The horizontal axis represents the time axis cycle numbers .

In the first cycle 9 data transfer bus is not occupied by any threads. It is possible to refer to currently held data of 10 WRF Th and 11 WRF Th .

In the second cycle 1 LOAD CWP REQ TH  and 4 LOAD CWP REQ TH  occur simultaneously in the instruction completion control unit and the signal is output to the data transfer control unit .

In the third cycle 1 LOAD CWP REQ TH  high and 4 LOAD CWP REQ TH  high are obtained and latched respectively by the latch circuit and the latch circuit in the flag generation unit of the data transfer control unit and 2 LOAD CWP REQ HOLD TH  and 5 LOAD CWP REQ HOLD TH  become high . At this moment 7 LOAD CWP INTLK ALL is low .

 2 LOAD CWP REQ HOLD TH  high and 7 LOAD CWP INTLK ALL low are input into the AND circuit and high is output from the output terminal of the AND circuit so that high is set in the latch circuit .

 2 LOAD CWP REQ HOLD TH  high 5 LOAD CWP REQ HOLD TH  high and 7 LOAD CWP INTLK ALL low are input into the input terminal of the AND circuit and low is output from the output terminal of the AND circuit so as to be input into the RST terminal of the latch circuit and 5 LOAD CWP REQ HOLD TH  high is held.

Because output from the AND circuit is high high is output to the SET terminal of the latch circuit .

 1 LOAD CWP REQ TH  high is input into the latch circuit . 4 LOAD CWP REQ TH  high is input into the latch circuit .

In the fourth cycle because 7 LOAD CWP INTLK ALL is high and 2 LOAD CWP REQ HOLD TH  is low the output of the AND circuit is low . At this moment 8 LOAD CWP COUNTER is reset to 0 .

In the fifth through seventh cycles counting is performed in the counter circuit until 8 LOAD CWP COUNTER becomes 3 low is output from the comparator while the counter value is between 0 and 2 inclusive and when the counter value has become 3 the output of the comparator becomes high . The outputs of the latch circuit and the latch circuit are held as they are high . The data transfer bus is occupied by the WRF from the MRF of thread Th .

When the counter value has become 3 the output of the AND circuit becomes high and the output of the 7 LOAD CWP INTLK ALL becomes low .

In the ninth cycle the output of 7 LOAD CWP INTLK ALL becomes low and thereby 5 LOAD CWP REQ HOLD TH  also becomes low . At this moment 8 LOAD CWP COUNTER is reset to 0 .

As explained by referring to the data transfer request signal 14 LOAD CWP REQ BY TRAP TH  is generated in the trap detection unit by a trap in thread Th in the ninth cycle at the earliest.

As explained by referring to 15 DECODE OPERATION TH  of subsequent instructions in the same thread is generated by the instruction analysis unit and WRF is referred to in the ninth cycle at the earliest.

In the tenth through twelfth cycles 8 LOAD CWP COUNTER is counted until it becomes 3 in the counter circuit the output of the comparator is low while the counter value is between 0 and 2 inclusive and when the counter value becomes 3 the output of the comparator becomes high . The outputs of the latch circuit and the latch circuit are held as they are high . The data transfer bus is occupied by the MRF and the WRF in the thread Th .

When the counter value has become 3 the output of the AND circuit becomes high and the output of 7 LOAD CWP INTLK ALL becomes low .

In the thirteenth cycle 8 LOAD CWP COUNTER is reset to 0 . The data transfer bus is released from thread Th .

As explained in 16 COMMIT OPERATION TH  is generated in the instruction completion control unit and a LOAD CWP process and a request to update the WRF of other threads are output in the fourteenth cycle at the earliest.

As explained in a data transfer request signal 14 LOAD CWP REQ BY TRAP TH  is generated in the trap detection unit by a trap in thread Th in the fourteenth cycle at the earliest.

As explained in 15 DECODE OPERATION TH  of subsequent instructions in the same thread is generated in the instruction analysis unit and refers to the WRF in the fourteenth cycle at the earliest.

In step S an instruction is fetched Fetch stage . Specifically an instruction is read from the memory device .

In step S it is determined whether or not POST SYNC REQ TH m which is a request signal of POST SYNC control and LOAD CWP INTLK OWN m is in effect. When the determination is Yes the process loops after step S. Otherwise the process proceeds to step S. For example in thread Th the instruction analysis unit performs determination on the basis of POST SYNC REQ TH  and LOAD CWP INTLK OWN .

In step S instruction analysis step instructions are decoded by the instruction analysis unit Decode stage . When the instruction is a WRCWP instruction the process proceeds to step S. When the instruction is not a WRCWP instruction the process proceeds to step S.

In step S instructions are given and executed. In other words a Dispatch stage issues an instruction to the computation unit instruction execution resources instruction issuing step . Also an Execute stage executes instructions in the computation unit . Also in the instruction completion control unit the execution results are combined Update Buffer stage .

In step S whether or not LOAD CWP INTLK OWN m has occurred in other threads is determined and if LOAD CWP INTLK OWN m has not occurred the process proceeds to step S. When it has occurred a loop starts.

In step S the memory device and the general purpose register are updated in accordance with execution results Commit stage . If it is not a SAVE instruction a RESTORE instruction or a WRCWP instruction i.e. when it is a normal instruction the process proceeds to step S. When it is a SAVE instruction or a RESTORE instruction the process proceeds to step S. When it is a WRCWP instruction the process proceeds to S.

In step S a CWP is updated and in step S data is transferred from the MRF of the corresponding thread to the WRF .

In step S whether or not LOAD CWP INTLK ALL is in effect is determined. When it is in effect a loop starts. When it is not in effect the process proceeds to step S.

In step s it is determined whether or not LOAD CWP COUNTER which is the counter value of the above data transfer control counter is 3 . When it is 3 the process proceeds to step S.

In step S the LOAD CWP process is terminated. In other words LOAD CWP INTLK ALL LOAD CWP INTLK OWN TH  and LOAD CWP INTLK OWN TH  are cancelled.

When a trap has occurred in step S subsequent instructions that are being executed in the same thread are cancelled in step S and whether or not LOAD CWP INTLK OWN TH m is present is determined in step S. In the above example it is 2SMT and accordingly whether or not LOAD CWP INTLK OWN TH  which is in thread Th has occurred is determined. When it has occurred the process proceeds to step S. When it has not occurred the process proceeds to step S.

By using the technique based on the present invention that has been described in detail the mounting area can be reduced and a conflict between processes in commoditized resources can be avoided by hardware in order to realize SMT in general purpose registers that employ a register window system.

The scope of the present invention is not limited to the above embodiments and various modifications and alterations are allowed without departing from the spirit of the present invention.

