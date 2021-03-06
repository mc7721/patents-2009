---

title: Method and apparatus for displaying personalized user interface
abstract: A method of displaying a user interface (UI), wherein the displaying is performed by a client, is provided. The method includes receiving UI data from a server, generating the UI to be displayed based on the received UI data and characteristics of the client and displaying the generated UI.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09424053&OS=09424053&RS=09424053
owner: SAMSUNG ELECTRONICS CO., LTD.
number: 09424053
owner_city: Suwon-Si
owner_country: KR
publication_date: 20090403
---
This application claims the benefit of U.S. Provisional Patent Application No. 61 045 787 filed on Apr. 17 2008 in the United States Patent and Trademark Office and Korean Patent Application No. 10 2008 0079036 filed on Aug. 12 2008 in the Korean Intellectual Property Office the disclosure of which is incorporated herein in its entirety by reference.

Embodiments described herein relate to a method and apparatus for displaying a user interface UI wherein the displaying is performed by a client and more particularly to a method and apparatus for displaying a UI after a client receives UI data from a remote server.

A variety of types of multimedia devices have been developed and an accelerated convergence of the multimedia devices has occurred. Different types of multimedia devices are frequently used to configure a network and communicate multimedia data or control each other.

Multimedia devices that are physically far apart from each other are remotely controlled via a remote user interface RUI . A UI server provides a UI for controlling a UI client and the UI client controls the UI server through the provided UI. For example in providing receiving a UI according to the CEA 2014 standard the UI server provides the UI for remote control to the UI client in a web page format and the UI client displays the web page to a user using a web browser. Then the user of the client uses the displayed UI and controls the UI server.

Embodiments of the present invention provide a method and apparatus for displaying a user interface UI provided from a remote server wherein the displaying is performed by a client and a computer readable recording medium having recorded thereto a program causing a computer to execute the method.

According to an aspect of embodiments of the present invention there is provided a method of displaying a user interface UI wherein the displaying is performed by a client the method including receiving UI data from a server generating the UI to be displayed based on the received UI data and characteristics of the client and displaying the generated UI.

The UI data may be encoded in a multimedia data format using a scene description technology based on a Moving Picture Experts Group MPEG standard.

The generating of the UI to be displayed may include comparing the characteristics of the client against the information about the dynamic configuration of the UI.

Each one of the plurality of UI objects may be a minimum unit of the UI in which a predetermined event is generated from interaction with a user.

The information about the dynamic configuration of the UI may be used in the generating of the UI by changing at least one of a color a form a background image and a font of the UI.

The information about the dynamic configuration of the UI may include representation information indicating how the UI objects are to be arranged in the UI.

The generating of the UI to be displayed may include selecting at least one of the plurality of UI objects based on the characteristics of the client.

The characteristics of the client may comprise at least one of a performance of the client a user profile of the client a network type to which the client is connected and external information.

The external information may be information received from external servers including weather information servers.

According to another aspect of embodiments of the present invention there is provided a method of providing a user interface UI from a server to a client the method including generating UI data comprising information about a dynamic configuration of the UI and transmitting the generated UI data to the client wherein the client generates the UI based on the information about the dynamic configuration of the UI and characteristics of the client.

According to another aspect of embodiments of the present invention there is provided an apparatus for displaying a user interface UI of a client the apparatus including a connection unit receiving UI data from a server a UI generation unit generating the UI to be displayed based on the received UI data and a characteristics of the client and a display unit displaying the generated UI.

The UI data may be based on a use pattern of UI objects by a user indicating preferences of the user regarding the UI objects.

According to another aspect of embodiments of the present invention there is provided an apparatus for providing a user interface UI to a client of a server the apparatus including a UI data generation unit generating UI data comprising information about a dynamic configuration of the UI and a connection unit transmitting the generated UI data to the client wherein the client generates the UI based on the information about the dynamic configuration of the UI and characteristics of the client.

According to another aspect of embodiments of the present invention there is provided a computer readable recording medium having embodied thereon a computer program causing a computer to execute the method of displaying a UI and the method of providing a UI from a server to a client.

Additional aspects and or advantages will be set forth in part in the description which follows and in part will be apparent from the description or may be learned by practice of the invention.

Reference will now be made in detail to the embodiments examples of which are illustrated in the accompanying drawings wherein like reference numerals refer to the like elements throughout. The embodiments are described below to explain the present invention by referring to the figures.

Referring to a client is a UI client which receives UI data from a server that is a remote UI server and displays the UI .

The UI data provided from the server to the client may be encoded in a multimedia data format according to the Moving Picture Experts Group MPEG standard. The MPEG standard is an international standard regarding a method of compression encoding video and audio and may include various versions such as MPEG 1 MPEG 2 MPEG 4 MPEG 7 and MPEG 21. The server encodes the UI data using the MPEG standard. Most devices that are currently developed include a MPEG decoder for reproducing compressed moving picture files. Thus when the UI is encoded based on the MPEG standard most devices may display the UI without separate applications for displaying the UI.

In particular an object based image encoding method such as MPEG 4 Binary Format for Scene BIFS or Lightweight Applications Scene Representation LASeR for mobile devices is used so as to encode the UI. UI objects may be image objects encoded by BIFS or LASeR and thus a BIFS or LASeR scene description technology is used to represent a spatio temporal arrangement of the UI objects and the UI objects are encoded. The UI object is denoted as a minimum unit of a UI in which a predetermined event is generated according to interaction with a user and a predetermined function is called based on the generated event.

BIFS or LASeR includes information about a scene description technology which can display the spatio temporal arrangement of the objects included in an image. Thus BIFS or LASeR is used to display the spatio temporal arrangement of the UI objects such as buttons and menus.

When an image codec such as BIFS or LASeR is used to encode the UI and an MPEG stream including the image for the UI is generated the client receives the MPEG stream including the image for the UI encoded according to BIFS or LASeR and decodes the received MPEG stream by using the MPEG decoder thereby displaying the UI only by reproducing the MPEG stream. Since the UI may be displayed by only reproducing the MPEG stream various devices including the MPEG decoder may display the UI provided from the server .

When the UI is configured by representing the object based arrangement using the object based scene description technology such as BIFS or LASeR the client which receives the UI data may generate a dynamically personalized UI by selecting and re arranging the objects.

In encoding the UI data using the MPEG scene description technology by the server the UI data including information about the dynamic configuration of the UI may be included. The information about the dynamic configuration of the UI is information for changing at least one of a color a form a background image and a font of the UI by personalizing the UI. This is described in more detail with reference to .

Referring to the UI data may be encoded by a UI package . The UI package includes a plurality of UI elements including a UI Element UI Element UI Element etc.

The plurality of UI elements may include information about the UIs based on characteristics of each different client. For example with respect to the same AV control UI UI element may include information about a UI used by users aged in their twenties and UI element may include information about a UI used by users aged in their thirties. Here information needed to select one of the plurality of UI elements is included in each of the UI elements as information to dynamically configure the UI. A UI element will now be described.

The UI element includes presentation information for representing objects included in the UI event information about events generated by the objects and function information about functions called for processing the events. Information about representation events and function are classified into layered information and are included in UI elements so that the UI may be dynamically expanded.

The information for representing the objects included in the UI indicates how the UI objects are arranged in the UI and what media is used to represent the UI objects.

A scene description is information for describing a scene configuration of the UI. The scene description is information about a location in which the objects are arranged in the UI and may include information for describing a layout form theme and template of the scene. Information about a way of representing the UI may be also included. When the UI objects are represented using a special effect such as fade out or fade in information about such a special effect may be also included. The scene description may be dynamically configured according to an adaptation utility which will be described later.

An object description is information about a way of representing the objects included in the UI and includes information indicating what media from among an image a picture and audio is used to represent each of the UI objects. In addition information about the representing time and representing ways for the objects may be also included. For example when the objects are represented in the scene at different times information about the time for timing control may be included. In addition as in the scene description when the UI objects are represented in the scene by using a special effect such as fade out or fade in information about the way the representing is performed may be also included. When the UI objects are not fixed and instead are applied by using a moving animation effect such information may also be included.

The adaptation utility includes information for dynamically configuring the UI based on characteristics of the client . The client compares the characteristics of the client with the information included in the adaptation utility and dynamically configures the UI. Also information for selecting UI elements based on an age of the user for example users in their twenties thirties and forties may be included. In other words the adaptation utility may include information indicating that the UI element includes information about the UI used by users in their twenties and allows the client of the users in their twenties to display the UI according to the UI element .

In addition the scene description may be dynamically changed according to the adaptation utility . According to the characteristics of the client for example a size a font of the UI a color of the UI object etc. may be changed. The server pre determines how the UI is changed according to the characteristics of the client and information about the determination is included in the adaptation utility .

In addition information for selecting some of the objects from among the plurality of UI objects included in the UI element in consideration of the characteristics of the client may be included in the adaptation utility .

For example information about object selection for displaying all UI objects A B C and D in the client used by users aged in their twenties displaying the UI objects A B and C in the client used by users aged in their thirties and displaying UI objects A and B in the client used by users aged in their forties may be included in the adaptation utility .

For dynamic configuration of the UI the adaptation utility may include information about a scene tree which is described in more detail with reference to .

A UI for controlling the same AV may include UIs and for users aged in their twenties thirties and forties respectively. The server includes the information about the scene tree to the adaptation utility and generates UI data. The client refers to the scene tree so as to select one of the plurality of UI elements dynamically change the scene description or select some of the plurality of UI objects.

Referring back to FIG. a resource includes sources for representing UI objects for example multimedia data such as images moving picture files and audio.

The event information includes information about the events generated by the objects included in the UI scene. Information about the events generated as a result of interaction between the UI objects and the user such as objects selection by the user is included.

An event description includes information about the events generated by the objects. A kind of user interaction which can be performed through UI objects such as click touch and rotation will now be described.

An event handle includes information about a way of processing the generated events. For example when the event called click is defined in the event description the event handle includes information indicating how the event called click is processed. If the clicked UI object is an object for controlling volume information for processing the event called click by interpreting the event as volume up or volume down is included.

A binding interface includes information about mapping between the defined events and device application programming interfaces API called to process the events that is information about mapping between the events and called device API in order to make a connection between the events generated by UI objects and functions called by the events.

The function information about functions called for processing the events includes detailed information about the device APIs called to perform the functions.

A function description includes information about the detailed operation of the device APIs called by the events in other words the functions realized by the user through the device API. For example when the device API for a vibration function is called information about a detailed function such as controlling intensity and time of vibration is included.

A function call includes information about parameters of functions called by the UI objects. For example if it is described in the function description that the device APIs for the vibration function control vibration intensity and the vibration time at levels to the function call includes specific parameters indicating in what level the function should be called from among five levels of the vibration intensity and the vibration time when a predetermined event is generated. In other words when the vibration function is called by a UI object A at the vibration intensity of level and at the vibration time of level from among five levels of vibration intensity and vibration time specific parameters for calling such a function may be included in the function call .

Referring back to in operation the client generates a personalized UI. In other words the personalized UI to be displayed to the user is generated based on the UI received in operation and the characteristics of the client .

The client may compare the characteristics of the client and information about the dynamic configuration of the UI and generate the personalized UI .

The client may analyze information about the dynamic configuration of the UI and obtain information about the configuration of the UI which corresponds to the characteristics of the client . The characteristics of the client and the adaptation utility are compared to each other so as to select the UI element suitable for the characteristics of the client or to change the scene description to be suitable for the characteristics of the client .

The objects to be included in the UI that is to be displayed may be selected according to the characteristics of the client . Here the objects may be selected with reference to the adaptation utility or the client may voluntarily select the UI objects only in consideration of the characteristics of the client .

The characteristics of the client may include at least one of performance qualities of the client a user profile of the client a network type to which the client is connected and external information.

Performance qualities of the client may include hardware performance of the client such as a CPU of the client a memory a display resolution and battery power remaining. A hardware resource which can be allocated by the client for displaying a UI for example allocable CPU processing capacity and allocable spare memory may also be included in the performance qualities of the client .

The user profile of the client includes user preferences. The user preferences which may be different in each client may be reflected in the displaying of the UI. A standard for determining such preferences includes age gender and language of the user. The user preference may be represented by a standard such as MPEG 21 UED Usage Environment Description or W3C CC PP Composite Capabilities Preference Profile .

The network type to which the client is connected includes ADSL VDSL WLAN and Wi Fi. According to the network type to which the client is connected bandwidth used in displaying the UI by the client may vary and thus the network type may be the base for generating a personalized UI.

The external information is used to generate a personalized UI and may include information relating to weather stock time and season. According to the information relating to weather stock time and season the UI needed for the user may vary and thus the UI may be dynamically displayed. When the client has a function of operating the UI by using motion sensing such a function is also included in the external information. The external information may be received from an external server instead of the client for example servers for providing weather information or stock information.

In operation the client controls the server using the displayed UI. According to the user input based on the displayed UI a predetermined event is called to the server or a predetermined control message is transmitted to the server .

The client may generate the personalized UI according to the characteristics of the client in operations through so that use of the client by the user may be improved. Also the server may be controlled more efficiently by using the personalized UI.

Similarly to a client in is a UI client which displays the UI the UI receiving UI data from a server which is a remote UI server. A difference between and is that the external information is received from a separate context server and the received external information is reflected in the generation of the UI.

Operation may correspond to operation in . In operation the server transmits the UI data to the client .

The UI data provided from the server to the client may be data encoded in a multimedia data format according to a Moving Picture Experts Group MPEG standard in particular a scene description technology according to the MPEG standard. Also the UI data may be data encoded in a UI package format using a scene description technology according to the MPEG standard as illustrated in for example.

In operation the context server transmits the external information to the client . For example information about weather and stock is provided to the client . Based on not only a use environment of the client such as weather season and temperature but also the external information such as stock fluctuations the UI may be personalized.

Thus in order to generate the UI by reflecting the external information the context server provides predetermined external information to the client in operation .

In operation the client generates the personalized UI. In other words the UI personalized based on the external information received in operation is generated. As described with reference to the external information and the adaptation utility may be compared to each other so as to select a predetermined UI element or the scene description may be changed according to the external information. The objects to be included in the UI that is to be displayed may be selected according to the external information.

For example in cloudy weather the UI element formed of a color and font suitable for the cloudy weather is selected or the scene description is changed to a color and font suitable for the cloudy weather thereby generating the UI.

In generating of the personalized UI based on the UI data received from the server is illustrated. However generating of the personalized UI based on the external information is not limited thereto and the UI previously displayed by the client may be changed based on the external information and displayed to the user in addition to the UI received from the server . For example a color and font of the UI displayed by the client may be changed based on the information about weather or stock and displayed to the user.

Similarly to a client in is a UI client which displays the UI the UI receiving UI data from a server which is a remote UI server. A difference between and is that the client generates the UI in whereas the server generates the UI based on the user profile of the client in .

In operation the client transmits the user profile to the server . As described above the user profile may include a user preference. A standard for determining such a preference includes age gender and language of the user. The user preference may be represented by a standard such as the MPEG 21 UED Usage Environment Description or the W3C CC PP Composite Capabilities Preference Profile .

In operation the sever generates the UI data based on the user profile received in operation . In other words the UI is generated based on user preferences of the client received in operation . According to the MPEG standard the UI may be encoded in a multimedia data format and the UI data may be generated.

In operation the UI data is transmitted to the client . A MPEG stream generated according to the MPEG standard is streamed to the client .

In operation the client displays the UI received in operation to the user. The MPEG stream is decoded and displayed to the user in real time.

In operation the client transmits a use pattern to the server . In other words the client analyzes a pattern of controlling the UI performed by the user in operation and transmits the analyzed information to the server . There may be a particular type of UI object preferred by the user. In addition there may be a particular type of content preferred by the user. Thus if the user pattern of the UI is analyzed the user preference may be known. The client transmits the information about the use pattern to the server and allows the server to update the UI by considering the preference of the client .

In operation the server generates new UI data based on the use pattern of the UI received in operation .

In operation the server transmits the UI data generated in operation to the client . In other words the UI data generated from the use pattern of the user of the client which was received in operation is transmitted to the client .

Referring to the client may include a connection unit a UI generation unit a display unit an input reception unit and a control processing unit .

The connection unit receives UI data from a server wherein the UI data is encoded in a multimedia data format using a scene description technology based on the MPEG standard. As similarly illustrated in the connection unit first transmits the user profile to the server and in response to this personalized UI data may be received.

The UI generation unit decodes the UI data received from the connection unit and generates the UI. A decoding unit decodes the UI data by using a MPEG decoder. The decoded UI is personalized by a representation unit based on the characteristics of the client . The decoded UI is personalized with reference to the characteristics of the client and information about the dynamic configuration of the UI included in the UI data. The characteristics of the client used in personalizing the UI includes performance of the client a user profile of the client a network type to which the client is connected and external information.

The control processing unit calls a predetermined event through the connection unit or generates and transmits a control message in order to perform a control operation according to the user input.

Referring to the server includes a connection unit a control processing unit and a UI data generation unit .

The connection unit transmits the UI data to the client wherein the UI data is encoded in a multimedia data format using a scene description technology based on the MPEG standard. As similarly illustrated in the connection unit first receives the user profile from the client and in response to this personalized UI data may be transmitted.

The control processing unit performs a control operation based on a message for calling the event received from the connection unit or a control message. As a result of performing the control operation when the UI needs to be updated the UI data generation unit is controlled and new UI data is generated.

The UI data generation unit encodes the UI data wherein the UI data is encoded in a multimedia data format using a scene description technology based on the MPEG standard. Information needed to dynamically configure the UI may be included in the UI data. When the connection unit receives the user profile of the client before transmitting the UI data the UI data is generated based on this.

According to embodiments of the present invention since the client only considers the characteristics of the client such as user preferences the client generates a personalized UI by itself and displays the personalized UI. Thus user satisfaction when using the client can be improved.

The invention can also be embodied as computer readable codes on a computer readable recording medium. The computer readable recording medium may be any data storage device that can store data which can be thereafter read by a computer system. Examples of the computer readable recording medium include read only memory ROM random access memory RAM CD ROMs magnetic tapes floppy disks and optical data storage devices. The computer readable recording medium can also be distributed over network coupled computer systems so that the computer readable code is stored and executed in a distributed fashion. For example an method of displaying and providing a user interface can be performed by using a computer mobile phone set top box portable media player digital television digital camera camcorder and DVD player which can represent UI based on MPEG decoder. And an apparatus for displaying a user interface and an apparatus for providing a user interface according to an exemplary embodiment of the present invention can comprise a bus coupling each unit of the apparatus as shown in at least one processor coupled to the bus a memory coupled to the bus to store instructions received message or generated message and to the at least one processor to execute instructions as described earlier.

Although a few embodiments have been shown and described it would be appreciated by those skilled in the art that changes may be made in these embodiments without departing from the principles and spirit of the invention the scope of which is defined in the claims and their equivalents.

