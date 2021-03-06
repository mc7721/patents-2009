---

title: Terminal device of non-android platform for executing android applications, and computer readable recording medium for storing program of executing android applications on non-android platform
abstract: Provided is a terminal device having a VM-based layer structure for executing heterogeneous applications. The terminal device includes: an application layer module including a first application and a second application; a platform layer module connected to a terminal processor and configured to operate the first application; and a middleware module configured to connect the platform layer module and the second application.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08555280&OS=08555280&RS=08555280
owner: Infraware Technology, Inc.
number: 08555280
owner_city: Seoul
owner_country: KR
publication_date: 20091211
---
The present application claims priority of Korean Patent Application No. 10 2009 0121002 filed on Dec. 8 2009 which is incorporated herein by reference in its entirety.

Exemplary embodiments of the present invention relate to a terminal device having a VM virtual machine based layer structure for executing heterogeneous applications and more particularly to a terminal technology which optimizes the android framework for low end devices such that Google android applications may be executed in terminals which do not operate on the android platform but operate on other platforms and includes a porting layer configured to connect a terminal platform to middleware and a VM provided by reconfiguring the Dalvik VM to be executed on a single task.

The Google android platform is a software stack released by OHA Open Handset Alliance led by Google and indicates a software package including the Linux kernel a VM a framework and applications.

The Google android platform may be applied only to high end smartphones which include a large sized display screen with 800 480 WVGA wide VGA resolution and provide a touch screen input.

In order to execute a Google android application the entire android software stack should be applied to a terminal device. Since the android software stack includes the Linux kernel and a plurality of basic services such as a system daemon the Google android platform is suitable for high end smartphones.

Accordingly the android applications have a limitation in that they should be executed only in high end smartphones. Therefore the android applications cannot be executed in general feature phones which operate on other platforms.

An embodiment of the present invention is directed to a terminal technology having a VM based layer structure for executing heterogeneous applications which is not only capable of executing Google applications even in low end terminal devices but also capable of native applications supported by the platforms of general terminal devices.

Another embodiment of the present invention is directed to a terminal device having a VM based layer structure for executing heterogeneous applications. The terminal device includes an application layer module including a first application and a second application a platform layer module connected to a terminal processor and configured to operate the first application and a middleware module configured to connect the platform layer module and the second application. The middleware module includes a class library layer module including an application framework module having a class library required for executing the second application and a core class library module providing a Java API Application Programming Interface a native library layer module including a VM configured to operate the second application through the class library and the Java API and a native library used for implementing the library of the application framework module and a porting layer module configured to connect the native library layer module and the platform layer module and provide a function of managing hardware of a terminal through the platform layer module.

The first application may include a native application the second application may include an android application and the VM may include a Dalvik VM.

The VM may operate on a single task in interconnection with the platform layer module through the porting layer module.

The VM may include one or more of a thread management module a dynamic library management module a foreign function interface FFI a synchronization module and a memory management module and may operate in interconnection with the platform layer module through the porting layer module.

The porting layer module may include one or more of a file system a memory allocation module a network module a basic library a timer and a device control module and may be configured to access corresponding hardware of the terminal device and manage and control the hardware.

The native library layer module may include one or more native libraries which operate in interconnection with the hardware management modules of the porting layer module.

The application framework module may include one or more service modules for performing telephone service location based service Bluetooth networking service WiFi networking service USB service and sensor service and executes a corresponding service in background according to the execution of the second application.

Exemplary embodiments of the present invention will be described below in more detail with reference to the accompanying drawings. The present invention may however be embodied in different forms and should not be constructed as limited to the embodiments set forth herein. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the present invention to those skilled in the art.

The terminal device includes an application layer module a middleware module a platform layer module a terminal processor and terminal hardware .

In general the terminal device refers to a mobile device such as a mobile phone or MP3 player. However the terminal device may include general terminal devices which are operated by the terminal processor based on platforms.

First the application layer module includes a first application and a second application. Here the first application indicates a native application which may be directly executed on the platform of the terminal device and the second application indicates an added application which may be executed through middleware including a porting layer and a VM.

In the case of a mobile terminal on the WISE Web based Inquiry Science Environment platform of LG native applications operating on the WISE platform corresponds to the first application and the Google android applications correspond to the second application.

The platform layer module is connected to the terminal processor and configured to operate the first application.

The middleware module is positioned between the platform layer module and the application layer module and configured to connect the second application provided in the application layer module .

At this time the middleware module not only includes a VM and a library to execute the second application but also includes a porting layer to connect the middleware module to the platform layer module . The details of the middleware module will be described with reference to .

The terminal processor is a central processing unit CPU . In the case of a mobile terminal a mobile dedicated processor capable of processing a variety of multimedia and a communication function may be used as the terminal processor .

The terminal hardware includes a screen output unit an audio output unit and a user input unit which compose the terminal device.

The middleware module may be divided into a class library layer a native library layer and a porting layer . At this time the respective layers become close to the physical layer in the downward direction. The lowermost porting layer is positioned adjacent to the platform layer module and the uppermost class library layer is positioned adjacent to the application layer module .

The class library layer module includes an application framework module including a class library required for executing the second application and a core class library module providing the Java API Application Programming Interface .

In an actual example the application framework module is used by modifying or reusing an application framework module of the Google android platform. The application framework module of the Google android platform includes a class library and services required for executing android applications. At this time some services are not needed for compatibility with the applications and thus may be removed to reduce the weight.

Furthermore the core class library module is applied by reusing a core library which belongs to the android runtime in the Google android platform. The core library of the Google android platform includes a basic Java API for programming in Java.

The native library layer module includes a VM configured to operate the second application positioned in the application layer through the class library provided in the application framework module and the Java API provided in the core class library module . Furthermore the native library layer module includes native libraries which are to be the foundation for implementing libraries of the application framework module .

In an actual example the VM is applied by modifying the Dalvik VM of the Google android platform. That is Linux dependent modules are removed from the existing Dalvik VM functions which are not provided by other platforms are added and the Dalvik VM is reconfigured in a structure to be executed even on a single task.

Furthermore the native libraries are applied by reusing libraries positioned under the application framework layer of the Google android platform. At this time the native libraries use open source software. The native libraries may be modified and ported if necessary and then set in the native library layer module .

The porting layer module connects the native library layer module to the platform layer module and provides a function of managing the hardware of the terminal through the platform layer module .

That is the porting layer module is a layer in which operating system dependent codes are organized so as to be easily transplanted and includes a variety of hardware management modules such as a file system a memory allocation module a network module basic libraries stdio stdlib math etc a timer device control modules display media input device 3D etc and other utilities.

The porting layer module is configured to access the corresponding hardware of the terminal device through the above described hardware management modules and manage and control the hardware.

For example the porting layer module includes Kernel DLL pthread etc System file memory socket stdio stdlib string math time Device framebuffer media input 3D etc and Utils log debug etc .

A first application manager and a second application manager provide a variety of management functions of downloading automatically upgrading and erasing a corresponding application.

The VM is applied by modifying the Dalvik VM. The Dalvik VM is a VM provided by the Google android platform and is configured to have a slightly different concept from the Java VM. That is the Dalvik VM may be operated in a smaller memory environment than the Java VM.

The VM includes a thread management module a dynamic management module a foreign function interface FFI a synchronization module a memory management module and so on. The thread management module is configured to manage threads such as pthread and the dynamic management module is configured to manage dynamic libraries such as a shared object and DLL.

The above described modules included in the VM are platform independent modules and the VM may operate while interworking with the platform layer module through the porting layer module without being affected by the platform. That is the VM may escape from the Linux dependent functions of the existing android platform.

Furthermore the VM is configured by modifying the existing Dalvik VM to perform the memory management according to the terminal device .

In addition the VM may be operated on a single task by modifying the existing Dalvik VM to operate the VM even in the terminal device which does not support multi tasking but operates on a single task. That is the VM operates on a single task in interconnection with the platform layer module through the porting layer module .

The native libraries serve as the foundation for implementing upper layer libraries and may be ported and provided according to other platforms other than Linux.

Referring to the native library layer module includes a variety of native libraries which operate in interconnection with the hardware management modules of the porting layer module .

The application framework module may includes a variety of service modules for performing telephone service location based service Bluetooth networking service WiFi networking service USB service sensor service and so on. At this time the services provided by the service modules may serve as servers or daemons in the entire system. When the second application is executed the corresponding service is executed in background.

The respective service modules may be modified if necessary and unnecessary service modules may be removed to reduce the weight.

According to the embodiments of the present invention the Google android applications may be executed not only in terminals of the Google android platform but also in terminals operated by other operating systems. Therefore as the android applications are served through a larger number of terminals it is possible to create a variety of added values.

Furthermore since the volume of the android platform may be reduced the android applications may be served through general low end feature phones not high end smartphones.

While the present invention has been described with respect to the specific embodiments it will be apparent to those skilled in the art that various changes and modifications may be made without departing from the spirit and scope of the invention as defined in the following claims.

