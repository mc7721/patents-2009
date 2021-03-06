---

title: Application monitoring
abstract: A method and apparatus for monitoring an application executing on a self-service terminal. The method comprises: registering with a services manager (such as an XFS or J/XFS manager) to receive event reports indicative of a change of state being sent to the application; accessing an operating system function to deduce a current status of the application; and communicating a status of the application to the remote management system, without communicating with the application, to enable the remote management system to manage the self-service terminal more effectively.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08499071&OS=08499071&RS=08499071
owner: NCR Corporation
number: 08499071
owner_city: Duluth
owner_country: US
publication_date: 20090501
---
The present invention relates to a method and apparatus for application monitoring. In particular but not exclusively the invention may be implemented in a self service terminal SST .

A self service terminal is generally defined as a device that is suitable for allowing a customer to conduct a transaction or to access information in an unassisted manner that is without requiring help from a human and or in an unattended environment that is an area that is not constantly supervised by someone physically present to ensure that the SSTs are not being misused . An SST deployer may decide to provide human assistance and or supervision for customers of the SST such as in a retail airport or hotel location however SSTs are typically designed so that such assistance and or supervision is not essential. A common type of SST is an automated teller machine ATM .

To ensure that an ATM remains operational it typically includes management software for collating information from modules within the ATM and status information about applications executing on the ATM. The management software typically notifies a remote management system of any errors or malfunctions that are detected in the ATM together with status information.

It is now common for an ATM owner to use an ATM control application provided by a first vendor on an ATM provided by a second vendor different from the first vendor . An ATM control application provides transaction processing functions for customers and module management functions for service personnel such as engineers .

Transaction processing functions include a sequence of screens displayed to the customer and associated commands for controlling the modules in response to customer inputs. Module management functions include state of health information and module test routines.

If the second vendor is responsible for servicing and maintaining the ATM then the second vendor may not have access to information from the control application because this is provided by a different vendor and may not report status information to any entity outside itself that is outside of the control application . This makes it very difficult for the second vendor to manage the ATM efficiently.

It is among the objects of an embodiment of the present invention to obviate or mitigate the above problem or other problems associated with prior art SSTs and or the management thereof.

Accordingly the invention generally provides methods systems apparatus and software for application monitoring.

In addition to the Summary of Invention provided above and the subject matter disclosed below in the Detailed Description the following paragraphs of this section are intended to provide further basis for alternative claim language for possible use during prosecution of this application if required. If this application is granted some aspects of the invention may relate to claims added during prosecution of this application other aspects may relate to claims deleted during prosecution other aspects may relate to subject matter never claimed. Furthermore the various aspects detailed hereinafter are independent of each other except where stated otherwise. Any claim corresponding to one aspect should not be construed as incorporating any element or feature of the other aspects unless explicitly stated in that claim.

According to a first aspect there is provided a method of monitoring an application executing on a self service terminal the method comprising 

registering with a services manager to receive event reports indicative of a change of state relating to the application 

communicating a status of the application to the remote management system without communicating with the application to enable the remote management system to manage the self service terminal more effectively.

The services manager may be an XFS extensions for Financial Services manager a J XFS manager or any other convenient software manager.

By virtue of this aspect of the invention software can be provided that deduces the state of an SST application without requiring an interface to that application or any communication direct or indirect between that application and the software. This enables the status of a third party application to be conveyed to a remote management system.

The event reports indicative of a change of state relating to the application may comprise event reports relating to a change in state of a physical switch used to change the application from transaction mode to supervisor mode for example a supervisor switch on a operator personnel panel .

The physical switch may be depressed by a service engineer. Alternatively the physical switch may be triggered by opening a door.

The event reports indicative of a change of state relating to the application may comprise event reports relating to a change in state of an open closed indicator for indicating to a customer that the self service terminal is either in service or out of service.

The event reports indicative of a change of state relating to the application may comprise event reports relating to a notification of entry into vendor dependent mode VDM .

Accessing an operating system function to deduce a current status of the application may comprise ascertaining if the application is listed on an operating system active process list.

Accessing an operating system function to deduce a current status of the application may comprise ascertaining if the application is listed as being in an executing state.

Accessing an operating system function to deduce a current status of the application may comprise ascertaining if a central processing unit on which the application is intended to execute has a current utilization for that application that is non zero or variable. A zero percent utilization may indicate that the application has crashed or hung .

The method may further comprise testing a communications connection to a remote authorization host to deduce the communication status of the application.

Testing a communications connection may be implemented by executing a ping on the internet protocol IP address of the remote authorization host. Alternatively or additionally testing a communications connection may be implemented by monitoring communication packet traffic. Alternatively or additionally testing a communications connection may be implemented by direct messaging to the monitored application.

According to a second aspect there is provided a monitoring component for monitoring an application executing on a self service terminal the monitoring component comprising 

a defined software interface for receiving event reports indicative of a change of state relating to the application 

an operating system interface for accessing an operating system function to deduce a current status of the application and

a communications interface for communicating a status of the application to the remote management system based on information received from at least one of the defined software interface and the operating system interface to enable the remote management system to manage the self service terminal more effectively.

According to a third aspect there is provided a self service terminal including the monitoring component of the second aspect.

The self service terminal may be an automated teller machine ATM an information kiosk a financial services center a bill payment kiosk a lottery kiosk a postal services machine a check in and or check out terminal such as those used in the retail hotel car rental gaming healthcare and airline industries or the like.

According to a fourth aspect there is provided a computer program comprising program instructions for implementing the steps of the method according to the first aspect.

The computer program may be embodied on a medium such as an optical disc a magnetic disc a solid state memory or the like conveyed on an electrical carrier signal or the like.

According to a fifth aspect there is provided a method of monitoring an application executing on a self service terminal the method comprising 

registering with a management component in the self service terminal to indicate types of event reports to be received 

communicating a status of the application to the remote management system without communicating with the application to enable the remote management system to manage the self service terminal more effectively.

The change of state events may be generated by a service provider associated with a module within the self service terminal.

According to a sixth aspect there is provided a method of monitoring an application executing on a self service terminal the method comprising 

registering with a services manager executing on the self service terminal to receive event reports indicative of a change of state of the self service terminal and

This aspect also has the advantage that a monitoring application can be used to convey updated status information about a control application to a remote management system without needing to communicate with the control application or to use the control application to effect the communication to the remote management system.

These and other aspects will be apparent from the following specific description given by way of example with reference to the accompanying drawings.

Reference will now be made to which is a schematic diagram showing an SST memory executing software components. In this embodiment the SST is an ATM. The software components comprise a control application a runtime platform a management application and a monitor application .

As is known in the art the control application presents a sequence of screens on an ATM display to a customer at the ATM collates information from the customer for example customer account information from a customer s ATM card transaction request and the like obtains authorization for a transaction request from a remote authorization host not shown in and instructs modules within the ATM as needed to fulfill an authorized transaction.

As is also known in the art the control application also comprises a conventional CEN XFS interface for communicating with a services manager in the form of an XFS manager described as box below in the runtime platform . In other words the control application is a conventional ATM control application having a conventional CEN XFS interface. CEN is the European Committee for Standardization and XFS is the extensions for Financial Services standard. The current version of this CEN XFS standard is v.3.10.

The runtime platform comprises proprietary run time components illustrated by the broken line box an operating system kernel illustrated by the broken line box an XFS manager service providers and a Vendor Dependent Application VDA for providing diagnostic and maintenance functions.

In this embodiment the operating system is a Windows XP trade mark operating system available from Microsoft Corporation trade mark . The operating system includes a plurality of device drivers . . . for interfacing with standard home computing devices such as a magnetic disk drive a display a serial port a parallel port and such like. As is well known in the art the operating system kernel is responsible for memory process task and disk management and includes routines for implementing these functions.

The proprietary run time components are a set of APTRA trade mark XFS components available from NCR Corporation 1700 S. Patterson Blvd. Dayton Ohio 45479 U.S.A. The run time components provide a range of programming facilities specific to self service terminal devices and services.

One function of the run time components is to enhance the operating system so that the operating system and run time components together provide high level access to all of the devices and modules including both standard home computing devices via the operating system and XFS computing devices via the run time components . Thus the combination of the run time components and the operating system can be viewed as providing a complete ATM operating system.

The run time components comprise a plurality of self service device drivers . . . that interface with self service specific devices together with support files not shown to allow each device or module to be operated tested maintained and configured. Although only a few device drivers are shown there are many device drivers in the run time components one for each self service specific module such as a card reader not shown a receipt printer not shown an encrypting keypad not shown and FDKs not shown and a cash dispenser not shown . Furthermore there are many more devices and modules in an ATM than those described herein for example there are more standard computing devices such as serial ports for example a USB port and a parallel port there may also be more self service devices and modules such as a statement printer a cash accept module and the like. These devices and modules are not discussed herein because they are not essential to an understanding of the invention.

The XFS manager includes an XFS application programming interface API and a service provider interface

The service providers communicate with the XFS manager and also with the device drivers associated with the modules. Suitable service providers are available from NCR Corporation 1700 S. Patterson Blvd. Dayton Ohio 45479 U.S.A.

The service providers provide a high level of abstraction to allow the control application to issue standard XFS commands to request functions and services. The service providers translate these XFS commands for the particular device drivers used in the runtime platform . Each service provider is typically associated with one module such as a cash dispenser module however one of the service providers is associated with vendor dependent mode which is a logical device . A service provider the Sensors and Indicators Units SIU service provider is associated with switches microswitches sensors and LEDs that are distributed across the ATM.

The Vendor Dependent Application VDA is accessed via the control application typically by a service person selecting supervisor mode on the ATM and then selecting a maintenance diagnostics mode. When this occurs the control application goes offline after concluding any transaction currently in progress and passes control of the modules to VDA . Control is passed to VDA once the modules have all entered vendor dependent mode VDM . This will be described in more detail below.

The management application is used for collating management information from the modules within the ATM and for sending and receiving management messages.

The management application comprises an SNMP simple network management protocol portion that handles communications creates traps sends these traps to a remote management system and the like. The SNMP portion also includes one or more non proprietary objects one or more proprietary objects and a CEN object .

The non proprietary objects are typically in the form of DLLs and are used for communicating with industry standard devices and modules within the ATM such as USB ports magnetic disk drives and the like. The proprietary object is typically also in the form of a DLL and is customized for proprietary modules in the ATM or modules with proprietary features such as the card reader the encrypting keypad the cash dispenser and the like. The CEN object communicates with the XFS manager specifically the XFS API . The management application includes conventional components for managing state of health information relating to the modules in the ATM.

The control application platform and management application are conventional and available from ATM vendors such as NCR Corporation or its competitors. These components can be used in embodiments of the present invention without any modification. The new application provided herein is the monitor application .

The monitor application is used for deducing the state of the control application without having any interface to the control application .

The monitor application comprises an XFS application programming interface API an operating system interface a remote management system interface and a timer .

The monitor XFS API is used to communicate with the XFS manager specifically the XFS API . This enables the monitor application to receive messages from the service providers such as the VDM service provider and the SIU the Sensors and Indicators Units service provider . This is described in more detail below.

The operating system interface is a conventional interface that allows the monitor application to query operating system components to ascertain information such as the current active processes executing on the central processing unit CPU with which the memory is associated the CPU utilization percentage for a particular process and the like.

The remote management system interface receives status messages through the monitor XFS API and the operating system interface and communicates these to a remote management system not shown in .

Reference will now be made to which is a simplified schematic diagram of an ATM network including an ATM incorporating the ATM memory executing the software components described with reference to .

The ATM comprises a central processing unit CPU coupled to the memory a plurality of user interface modules not shown in detail but including a cash dispenser a card reader a display a receipt printer an encrypting keypad and the like a network connection module and a service operator panel .

The service operator panel enables diagnostic tests to be performed on and information to be retrieved from the modules within the ATM .

The service panel includes a physical mode switch for switching the ATM between transaction mode and supervisor mode. In supervisor mode a service engineer can execute the VDA to enter vendor dependent mode VDM and execute replenishment maintenance or diagnostic tasks. When the engineer has completed this then he she can exit the VDA component and press the mode switch to return control of the modules to the control application . This is referred to as returning to transaction mode.

The network connection module enables the ATM to communicate with a remote authorization host for authorizing transactions requested by an ATM customer and also enables the ATM to communicate with a remote management system to send status information as requested by the remote management system and also to send fault signals in response to a fault condition being detected as will be described in more detail below.

Communication between the ATM the authorization host and the remote management system is achieved using a network .

Reference will now be made to which is a flowchart illustrating steps involved when the monitor application deduces a current state of the control application . For clarity has been split into four flowcharts .

Initially the monitor application registers with the appropriate service providers via the XFS manager step . In this embodiment the monitor application registers with the VDM service provider and the SIU servicer provider . This enables the monitor application to receive notifications from the VDM service provider that the ATM is entering or exiting vendor dependent mode VDM . This also enables the monitor application to receive notifications of status changes of indicators and switches from the SIU service provider as will be explained in more detail below.

The next step is for the monitor application to set the internal timer to a preset value step . The purpose of the timer is to recreate the effect of a heartbeat for the control application . When the timer has decremented to zero then the monitor application interrogates the operating system via the operating system interface to obtain evidence that the control application is still executing.

The initial value to which the timer is set is not critical. A low initial value for example ten seconds will result in frequent calls to the operating system which is inefficient. A very high initial value for example ten hours will result in very infrequent calls to the operating system so the control application may have hung for hours before it is detected by the monitor application . In this embodiment an initial value of ten minutes is selected for convenience.

The next step is for the monitor application to detect if an event has been received step from one of the service providers that the monitor application has registered with. The monitor application is registered to receive events from the VDM service provider and the SIU service provider

If an event is received step then the event is processed as described in detail below with reference to .

If an event is not received then the next step is for the monitor application to detect if the value of the timer has decremented to zero step .

If the value of the timer has decremented to zero then the monitor application ascertains if the communications status of the ATM has changed from operational to non operational step . Details of the sub steps implemented in step are shown in and are described below.

If the communications status of the ATM has changed then the monitor application specifically the remote management system interface sends a message to the remote management system to indicate the new communication status of the ATM step .

If the communications status of the ATM has not changed then the monitor application ascertains if the operating system status has changed step . Details of the sub steps implemented in step are shown in and are described below.

If the operating system indicates that the control application status has changed then the monitor application specifically the remote management system interface sends a message to the remote management system to indicate the new status of the control application step then the monitor application returns to step to reset the timer to the initial value.

If the operating system indicates that the control application status has not changed then the monitor application returns to step so that the timer can be reset to the initial value.

The sub steps involved in processing a received event step will now be described with reference to which shows step in more detail.

When the SIU service provider detects that someone typically a service engineer has depressed the physical mode switch then the service provider sends an event notification to all applications registered with it. Since the monitor application registered with the service provider during step the monitor application will receive these notifications. The event notification conforms to the CEN XFS 3.10 standard and indicates that the physical mode switch state has changed. This takes the form of a WFS SRVE SIU PORT STATUS event that reports WFS SIU OPERATORSWITCH.

Similarly if the control application has to stop offering customer transactions for a period of time then the control application changes the state of a logical out of service indicator from being in service to being out of service. The event notification conforms to the CEN XFS 3.10 standard and takes the form of a WFS SRVE SIU PORT STATUS event that reports WFS SIU OPENCLOSE.

However in addition to the two events received from the SIU service provider that are described above an event can be received from the SIU service provider that relates to an indicator that the monitor application is not interested in because it does not reflect or relate to a change in state of the control application .

If the received event relates to the state of the physical mode switch then this indicates that the control application has changed between transaction mode in which a customer can execute a transaction and supervisor mode in which a service engineer can operate on the ATM .

Similarly if the received event relates to the state of the logical out of service indicator then this indicates that the control application has changed between in service mode in which a customer can execute a transaction and out of service mode in which customer transactions are typically not available on the ATM .

In addition an event may be received from the VDM service provider that requires acknowledgement for example a request from the service provider to enter or exit vendor dependent mode must be acknowledged by the monitor application or that indicates status for example vendor dependent mode having been entered or exited .

Every time a status of a switch or indicator on the ATM changes then the SIU service provider will send an event notification listing the status of all of the indicators and switches which will be received by the monitor application step and many of these will not be relevant to the physical mode switch or the logical out of service indicator. For this reason when the monitor application receives an event it ascertains if the event relates to a switch or indicator that is not relevant step .

If the event is relevant that is it relates to the physical mode switch the logical out of service indicator or vendor dependent mode then the monitor application ascertains if the physical mode switch status has changed step .

If the event notification indicates that the physical mode switch status has changed then the remote management system interface sends a new mode status message to the remote management system indicating the new mode status of the ATM step .

If the event notification does not indicate that the physical mode switch status has changed then the monitor application ascertains if the logical out of service indicator status has changed step .

If the event notification indicates that the logical out of service indicator status has changed then the remote management system interface sends a new service status message to the remote management system indicating the new service status in service or out of service of the ATM step .

If the event notification does not indicate that the logical out of service indicator status has changed then the monitor application ascertains if the VDM status has changed step .

A VDM status change may be indicated by an event that reports WFS SYSE VDM MODEENTERED indicating that the ATM is now in VDM mode or WFS SYSE VDM MODEEXITED indicating that the ATM is now out of VDM mode .

If the VDM status has changed then the remote management system interface sends a message to the remote management system indicating the new status of the control application step since the control application is in a different status when the ATM is in vendor dependent mode VDM .

If the status has not changed then the relevant event is a request either to enter or exit vendor dependent mode. In response to this request the monitor application via the XFS API responds to the request with an acknowledgment step in accordance with the CEN XFS standard. For example the monitor application responds to a request to enter VDM with a WFS CMD VDM ENTER MODE ACK response.

The sub steps involved in testing the communications status of the ATM step will now be described with reference to .

The monitor application pings the IP address of the remote authorization host step and then receives a response step .

If the ping is successful then the communications at the remote authorization host are operational. If the ping is not successful then the communications at the remote authorization host are not operational.

The communications status is then compared with the previous communications status as of the last time that an IP address ping was performed on the remote authorization host step .

If the communications status has changed for example from operational to non operational or vice versa then the monitor application proceeds to step to indicate the new communications status of the remote authorization host .

The sub steps involved in testing the status of the control application as indicated by the operating system step will now be described with reference to .

The monitor application via the operating system interface interrogates the operating system kernel to ascertain if the control application appears in the list of active processes step .

The active process status of the control application is then compared with the previous active process status as of the last time that the operating system kernel was interrogated step .

If the active process status of the control application has changed then the monitor application proceeds to step where the new control application status is transmitted to the remote management system .

If the active process status of the control application has not changed then the monitor application via the operating system interface interrogates the operating system kernel to ascertain the CPU utilization for the control application process step .

The CPU utilization may be in one of two states a non working state indicated by a zero percent utilization of the CPU by the control application or a working state indicated by a non zero percent utilization of the CPU by the control application .

The CPU utilization state for the control application is then compared with the previous CPU utilization state as of the last time that the operating system kernel was interrogated step .

If the CPU utilization state for the control application has changed then the monitor application proceeds to step where the new control application status is transmitted to the remote management system .

If the CPU utilization state for the control application has not changed then the monitor application proceeds to step where the internal timer is reset.

It will now be appreciated that this embodiment has the advantage that a monitor application can be used in conjunction with a third party control application to provide a remote management system with status information about the control application without having to interface to the control application . The monitor application can be used with conventional ATM software without having to modify the conventional ATM software.

Various modifications may be made to the above described embodiment within the scope of the invention for example the timer described above decrements from an initial value to zero in other embodiments the timer may increment from zero to a predetermined value or any other convenient timing mechanism may be used for example when a predetermined number of events has occurred.

In other embodiments the remote management system and the authorization host may be implemented on the same server.

In other embodiments the communications status test step may include pinging the local network address to ascertain if there is a problem with the communications software stack on the ATM . In the event of such a problem being detected however the monitor application would not be able to send a message to the remote management system until the problem was repaired unless the monitor application has a separate communications facility such as a wireless transceiver .

In other embodiments the communications status test step may include monitoring communication packet traffic.

In other embodiments the monitor application may monitor either events relating to the status of the physical mode switch or the status of the VDM service provider rather than monitoring both.

In the above embodiment the ATM is designed and supplied by NCR Corporation and the proprietary run time components are also scripted and provided by NCR Corporation. In other embodiments the ATM may be from a different ATM vendor. In such embodiments the proprietary run time components would also typically be provided by that vendor. Nevertheless provided the proprietary run time components supported XFS then the monitor application could still be used to deduce the state of the control application .

In other embodiments the management application may implement a different protocol to SNMP such as a different network management protocol.

In other embodiments instead of providing a physical mode switch the SST may detect a request to change modes by for example sensing a door being opened a pre defined key on the supervisor keyboard being pressed or an icon on a supervisor display being selected.

In other embodiments the SST may be able to execute customer transactions even when a customer engineer is operating on the SST.

In some embodiments the user interface modules may also include a physical out of service light responsive to the state of the logical out of service indicator. This out of service light may comprise an LED array that emits green light when the ATM is in service and red light when the ATM is out of service. This means that a WFS SRVE SIU PORT STATUS event will change the status of that is the color displayed by the out of service light.

Although the monitor application flow has been described as a series of steps these steps may be carried out in any suitable order or simultaneously where appropriate. The steps described in the above embodiment are intended to illustrate how the monitor application responds to notifications from service providers or from information retrieved from the operating system it is not intended to imply that any particular programming structure is used. For example the events are received asynchronously and interrupt any processing that is taking place for example a received event may be processed during a call to the operating system to ascertain if the control application is executing on the operating system s task list.

The methods described herein may be performed by software in machine readable form on a tangible storage medium or as a propagating signal.

The terms comprising including incorporating and having are used herein to recite an open ended list of one or more elements or steps not a closed list. When such terms are used those elements or steps recited in the list are not exclusive of other elements or steps that may be added to the list.

