---

title: Method and device for playing back media data with limited control
abstract: A method and apparatus for restricting a control operation with respect to reproduction of media data so as to commercially implement consumption of the media data, the method and apparatus including: restricting the control operation with respect to reproduction of the media data by using a predetermined Application Programming Interface (API); and reproducing the media data received from a media server, according to the restricted control operation.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08474024&OS=08474024&RS=08474024
owner: Samsung Electronics Co., Ltd.
number: 08474024
owner_city: Suwon-si
owner_country: KR
publication_date: 20090122
---
This application is a National Stage application under 35 U.S.C. 371 of PCT KR2009 000323 filed on Jan. 22 2009 which claims the benefit of U.S. provisional Patent Application No. 61 023 601 filed on Jan. 25 2008 the disclosures of which are incorporated herein in their entirety by reference.

Apparatuses and methods consistent with exemplary embodiments relate to a method and apparatus for reproducing media data and more particularly to a method and apparatus for reproducing media data while restricting a control operation with respect to reproduction of the media data.

Due to an increase in media data exchanged via wireless or wired communication networks various methods have been developed to commercially implement use of media data. For example a user may be provided free media data and in return the user has to view an advertisement related to the free media data. In this manner media data consumption by the user is commercially implemented.

In this case if the user does not view the advertisement by using a skip function or a fast forward function the media data consumption cannot be commercially implemented. Also if a user records the free media data and indiscriminately shares the recorded media data with other users the media data consumption may not be commercially implemented.

Thus a media data provider requires control operations including recording skipping and fast forwarding of media data to be restricted so as to prevent execution of the control operations while a user reproduces the media data.

Aspects of exemplary embodiments provide a method and apparatus for reproducing media data while restricting a control operation by a user. Aspects of exemplary embodiments also provide a computer readable recording medium having recorded thereon a program for executing the method.

According to an aspect of an exemplary embodiment there is provided a method of reproducing media data received from a media server performed by a client device the method including driving a browser including an application programming interface API for restricting a control operation with respect to reproduction of the media data restricting the control operation with respect to the reproduction of the media data by using the API and reproducing the media data based on the restricted control operation.

The restricting the control operation may include receiving information about the restricting of the control operation and retrieving the API for restricting the control operation with respect to the reproduction of the media data according to the received information.

The receiving the information may include receiving information as metadata before a session for the reproduction of the media data is started or receiving a notification according to the Consumer Electronics Association CEA 2014 standard during a session for the reproduction of the media data wherein the notification is related to the restricting of the control operation.

The receiving the information may include receiving the information about the restricting of the control operation according to Asynchronous JavaScript and Extensible Markup Language AJAX during a session for the reproduction of the media data.

The receiving the information may include receiving the information about the restricting of the control operation from a server that is different from the media server.

The reproducing the media data may include when an input indicating a control operation is received from a user determining whether the control operation is a restricted control operation when the control operation is determined as the restricted control operation ignoring the control operation and continuing the reproducing the media data.

According to an aspect of another exemplary embodiment there is provided a media data reproducing apparatus that is a client device for reproducing media data received from a media server the media data reproducing apparatus including a browser driving unit which drives a browser including an application programming interface API for restricting a control operation with respect to reproduction of the media data and an application driving unit which restricts the control operation with respect to reproduction of the media data by using the API and which drives an application that reproduces the media data based on the control operation.

According to an aspect of another exemplary embodiment there is provided a computer readable recording medium having recorded thereon a program for executing the method of reproducing the media data.

According to an aspect of another exemplary embodiment there is provided a method of providing media data the method including transmitting from a first server to a client device media data and transmitting from a second server to the client device information about restricting a control operation with respect to a reproduction of the media data by the client device wherein the information is used by the client device to retrieve an application programming interface API for restricting the control operation with respect to the reproduction of the media data.

According to an aspect of another exemplary embodiment there is provided a method of reproducing media data received from a media server performed by a client device the method including restricting a control operation with respect to a reproduction by the client device of media data by using an application programming interface API and reproducing the media data based on the restricted control operation.

Hereinafter exemplary embodiments will be described in detail with reference to the attached drawings. The exemplary embodiments may be embodied in various forms without being limited to the exemplary embodiments set forth herein. Descriptions of well known parts are omitted for clarity and like reference numerals refer to like elements throughout. Expressions such as at least one of when preceding a list of elements modify the entire list of elements and do not modify the individual elements of the list.

The client drives the browser and drives an application for reproduction of the received media data based on the driven browser. The browser provides an environment for driving the application for reproduction of the received media data and includes at least one application programming interface API related to reproduction of the received media data. The at least one API related to reproduction of the received media data may include an API for restricting a control operation with respect to reproduction of the received media data. The application may be a webpage related to reproduction of the received media data. In this case the webpage may include a link or a script that is related to reproduction of the received media data.

In operation the client requests the media server for the application e.g. the webpage for reproduction of the media data and receives the application in response to the request. For example the client may receive the webpage including the link or the script related to reproduction of the media data.

In operation the client requests the media server for the media data by driving the application received in operation and receives the media data in response to the request. The client receives the media data in a streaming manner or a downloading manner.

In operation the client receives from the media server information about restriction on a control operation that may be performed by a user.

In the present exemplary embodiment a session for reproduction of the media data is started according to the request for the media data by the client in operation . After the session for reproduction of the media data is started the information about restriction on the control operation may be separately received from the media server in operation . However it is understood that other exemplary embodiments are not limited thereto. For example according to another exemplary embodiment the client may receive the information when the session is started in operation e.g. as metadata .

As non limiting examples the information about restriction on the control operation may be received in the form of a notification according to the CEA 2014 standard after the session for reproduction of the media data is started or may be received according to Asynchronous JavaScript and Extensible Markup Language AJAX . In the latter case the client may drive an application supporting the AJAX and may receive only necessary information that is the information about restriction on the control operation from the media server without reloading entire pages. Thus after the session for reproduction of the media data is started the client may request the media server for the information about restriction on the control operation and may receive the requested information about restriction on the control operation according to the AJAX.

The information about restriction on the control operation may be information related to restriction on pausing or stopping the media data or may be information related to restriction on recording the media data. For example in cases where a user is to view an advertisement before the media data is to be reproduced the information about restriction on the control operation may be related to restriction on pausing or stopping the advertisement. Also in order to protect a copyright of the media data when the media data is being reproduced the information about restriction on the control operation may be related to restriction on recording the media data.

In operation the client restricts the control operation with respect to reproduction of the media data according to the information received in operation . The client retrieves the API for restricting the control operation with respect to reproduction of the media data according to the information received in operation . The retrieved API specifies at least one of control operations allowed during reproduction of the media data and specifies control operations prevented during reproduction of the media data. This operation will be described in detail with reference to .

 SetMode is a control operation restricting method that involves setting possible control operations by receiving variables corresponding to modes illustrated in from a webpage that is an application driven in the client . For example when 0x01 is input to the API as a variable it is only possible to start and stop the media data and when 0x02 is input to the API as a variable it is only possible to pause and resume the media data. In order to make a start stop pause and resumption possible 0x03 is input as a variable wherein 0x03 is a combination of 0x01 and 0x02 and is 00000011 in binary. 0x08 is a variable for restricting recording of the media data and when 0x11 i.e. 00001011 in binary is input as a variable it is possible to start stop pause resume and record the media data.

In order to restrict another control operation the aforementioned four bits may be used and in order to restrict the control operation by using a default mode i.e. a basic setting in a browser 0xff i.e. a binary number of 11111111 is input.

The object properties are provided to indicate a current state restricted by the SetMode method. For example Playmode is an object property that indicates a current restriction state of the control operation and recordMode is an object property that indicates whether recording of the media data is currently restricted.

Also in relation to operations and to be described later in order to inform a user about an occurrence of an error when the user inputs a control operation that is not allowed error may be provided as an object property.

Referring to similar to the API of the API of includes an object method and object properties for restricting the control operation with respect to reproduction of the media data. Comparing the API of with the API of the API of is different in that variables input to the SetMode method do not correspond to modes for specific control operations but correspond to reproduction modes that are combinations of a plurality of control operations.

In other words when 0x00 is input to the SetMode method as a variable the client may be set as AdvancedPlayer Mode in which all control operations are possible. when 0x01 is input to the SetMode method as a variable the client may be set as PrimitivePlayer Mode in which it is only possible to start and stop reproduction of the media data. In PrimitivePlayer Mode adjusting a media data reproduction speed searching for the media data and seeking to previous next media data is restricted. When 0x02 is input to the SetMode method as a variable the client may be set as BasicPlayer Mode in which only adjusting a media data reproduction speed is restricted.

Referring back to in operation the client reproduces the media data according to the control operation restricted in operation . That is the media data is reproduced according to the restricted control operation.

A user may input a control operation during reproduction of the media data. In this case in operation the client determines whether the control operation input by the user is restricted in operation .

In operation if the control operation input by the user in operation is not allowed by the restricted control operation the client ignores the user input and continues reproducing the media data. However if the control operation input by the user in operation is allowed by the restricted control operation the client performs the control operation according to the user input.

The media data reproducing unit requests a media server or for media data receives the media data and reproduces the received media data.

The browser driving unit drives a browser that provides an environment for driving an application for reproduction of the media data. The browser provides at least one API related to reproduction of the media data. The browser may be a browser compatible with the CEA 2014. As described above the API related to reproduction of the media data includes an API for restricting a control operation with respect to reproduction of the media data. The application may be a webpage related to reproduction of the media data.

The application driving unit drives the application related to reproduction of the media data based on the browser driven by the browser driving unit . The application driving unit requests the media server or for the application related to reproduction of the media data e.g. the webpage receives the application and drives the application.

Also the application driven by the application driving unit retrieves the API included in the browser wherein the API is for restricting the control operation with respect to reproduction of the media data. The application driving unit retrieves the API based on information about restriction on the control operation received by the information receiving unit and restricts the control operation with respect to reproduction of the media data. For example based on the information it is possible to restrict pausing or stopping of reproduction of the media data or to restrict recording of the media data. A detailed description related to restriction on the control operation is provided above with reference to .

When restriction is set with respect to the control operation the media data is reproduced based on the restricted control operation. According to the CEA 2014 standard all control operations related to reproduction of the media data are defined by APIs of the browser. Thus according to the present exemplary embodiment an API for restriction of a control operation may be added to the browser in the form of an embedded object or a plug in object and the control operation may be restricted based on the added API.

In this manner since the control operation with respect to reproduction of the media data may be restricted external to the client by using the added API a user may not discretionally skip or fast forward commercial content such as an advertisement so that consumption of the media data may be commercially implemented.

The information receiving unit receives the information about restriction on the control operation with respect to reproduction of the media data from the media server or the third server . As described above the information about restriction on the control operation may be received in the form of a notification from the media server or the third server after a session for reproduction of the media data is started or may be received from the media server or the third server according to AJAX. Also as described above the information about restriction on the control operation may be transmitted in the form of metadata to the client before a session for reproduction of the media data is started.

The information receiving unit may be pushed to receive the information about restriction on the control operation from the media server or the third server . Moreover the information receiving unit may request the information about restriction on the control operation from the media server or the third server and may receive the information in response to the request.

The application providing unit provides an application e.g. a webpage related to reproduction of the media data to the media data reproducing unit of the client . When the application providing unit receives a request related to provision of the application from the client the application providing unit provides the application e.g. a webpage including a link or a script related to reproduction of the media data in response to the request.

The media data providing unit provides the media data reproducing unit of the client with media data requested by the client .

The information providing unit transmits the information about restriction on the control operation with respect to reproduction of media data to the client . For example after a session for reproduction of the media data is started the information providing unit transmits the information about restriction on the control operation to the client as a notification or transmits the information about restriction on the control operation to the client according to AJAX. Moreover as described above the information about restriction on the control operation may be transmitted to the client as metadata before a session for reproduction of the media data is started.

Referring to the residential network of the IPTV service system includes an Open IPTV Terminal Functional OITF device an IP Multimedia Subsystem IMS gateway IG an application gateway AG device a Content and Service Protection CSP Gateway CG device and a Wide Area Network WAN gateway device . corresponds to cases in which the above devices to of the residential network are separate from each other. However it is understood that two or more of the above devices to may be modules included in one device.

An IPTV service is provided from an IPTV service provider server to the residential network and the IG device the AG device the CG device and the WAN gateway receives the provided IPTV service and relays the IPTV service to the OITF device .

The IPTV service provider server corresponds to a media server and provides the OITF device with media data an application related to reproduction of the media data and information about restriction on reproduction of the media data.

The OITF device consumes the IPTV service of one of a plurality of IPTV service providers. The OITF device selects one of the plurality of IPTV service providers according to a user input and consumes the IPTV service provided by the selected IPTV service provider. The OITF device may be a device such as a TV that receives and consumes a service.

The OITF device corresponds to a client or . In other words the OITF device receives the media data related to the IPTV service from the IPTV service provider server reproduces the media data and drives the application related to reproduction of the media data based on a browser including an API related to reproduction of the media data and an API related to restriction on the control operation.

The IG device allows an IPTV service access in conjunction with an IMS of the OITF device . The IG device receives the IPTV service from the IPTV service provider server and relays the IPTV service to the OITF device . The IG device interacts with the OITF device by using a predetermined protocol that is defined for interaction between devices in the residential network . According to an IPTV service provision request from the OITF device the IPTV service is requested from the IPTV service provider server the IPTV service is received and the received IPTV service is relayed to the OITF device .

The AG device receives the application and relays the received application to the OITF device . In cases where a predetermined application is used for the IPTV service the AG device receives the application from the IPTV service provider server and provides the application to the OITF device . It is understood that the AG device may be omitted for example when it is not necessary for the OITF device to be provided the application.

Furthermore it is understood that the CG device is an optional device that may be used when IPTV content and service protection of an external network are converted into protection e.g. Digital Transmission Content Protection over IP DTCP IP that is acceptable to the OITF device .

The WAN gateway is used to support a physical connection between the residential network and the IPTV service provider server .

The apparatus for reproducing media data and the apparatus for providing media data according to exemplary embodiments may include a bus coupled to each unit of the devices illustrated in and at least one processor coupled to the bus. Also the apparatuses may include a memory coupled to the at least one processor that is combined with the bus so as to store commands received messages and generated messages and to execute the commands.

According to exemplary embodiments since a user may not discretionally control reproduction of the media data the user may not skip commercial content such as an advertisement. Thus consumption of the media data may be further commercially implemented. Also a content market may be expanded by activating an online content market.

Exemplary embodiments can also be embodied as computer readable codes on a computer readable recording medium. The computer readable recording medium is any data storage device that can store data which can be thereafter read by a computer system. Examples of the computer readable recording medium include read only memory ROM random access memory RAM CD ROMs magnetic tapes floppy disks optical data storage devices etc.

The computer readable recording medium can also be distributed over network coupled computer systems so that the computer readable code is stored and executed in a distributed fashion.

While exemplary embodiments have been particularly shown and described above it will be understood by those of ordinary skill in the art that various changes in form and details may be made therein without departing from the spirit and scope of the present invention as defined by the following claims.

