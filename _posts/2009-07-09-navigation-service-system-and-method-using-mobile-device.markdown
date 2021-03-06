---

title: Navigation service system and method using mobile device
abstract: A navigation service system and a navigation service method are provided. The navigation service system includes a mobile device, and a web server for communicating with the mobile device, the mobile device includes a display unit for displaying at least one navigation widget icon, a wireless communication unit for executing wireless communications with the web server, a Global Positioning System (GPS) module for receiving location information of the mobile device, a memory unit for storing a navigation widget, and a navigation widget controller for controlling the wireless communication unit to transmit the location information of the mobile device to the web server, for controlling the wireless communication unit to receive map data related to the location information from the web server, and for controlling the display unit to display the map data and the location information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08775067&OS=08775067&RS=08775067
owner: Samsung Electronics Co., Ltd.
number: 08775067
owner_city: Suwon-si
owner_country: KR
publication_date: 20090709
---
This application claims the benefit under 35 U.S.C. 119 a of a Korean patent application filed in the Korean Intellectual Property Office on Jul. 11 2008 and assigned Serial No. 10 2008 0067753 the entire disclosure of which is hereby incorporated by reference.

The present invention relates to mobile device technology. More particularly the present invention relates to a navigation service system and method using a mobile device equipped with a navigation widget.

A mobile device also known as a portable device a handheld device and the like is a pocket sized computing device typically having a display screen with touch input or a miniature keyboard often referred to as a keypad . Many different types of mobile devices such as a mobile communication device a Personal Digital Assistant PDA and a smart phone are widely used today. Such mobile devices not only provide a voice call a video call and a Short Message Service SMS but also offer a variety of useful applications e.g. a schedule manager games and the like . More particularly some recently launched portable devices have a navigation function that provides travel or traffic guide path based on location information.

A conventional navigation service system using a mobile device has an embedded map that has already been stored in the device. Therefore when a navigation service is activated the mobile device retrieves map data in connection with current location information from its own storage and displays retrieved map data on a screen.

The quantity of such map data is large so the mobile device needs a large storage capacity to store the map data. Also since map data should be updated frequently to reflect the newest data a user often suffers great inconvenience in use. In addition in order to use a navigation service system in foreign countries a user has to additionally download map data related to those countries.

Furthermore a conventional navigation service system uses limited map data provided by a navigation service provider or a mobile device manufacturer. Therefore a user is restricted in selection of map data and has difficulty in reflecting desired map data to a navigation service system.

Moreover a navigation program used in a conventional navigation service system has a slower loading time because of its large size and requires a large amount of resource for running.

Therefore a need exists for an improved navigation service technology that requires no embedded map allows a user to reflect desired map data and reduces a loading time.

An aspect of the present invention is to address at least the above mentioned problems and or disadvantages and to provide at least the advantages described below. Accordingly an aspect of the present invention is to provide a navigation service system and a navigation service method using a mobile device.

In accordance with an aspect of the present invention a navigation service system is provided. The system includes a mobile device and a web server for communicating with the mobile device the mobile device includes a display unit for displaying at least one navigation widget icon a wireless communication unit for executing wireless communications with the web server a Global Positioning System GPS module for receiving location information of the mobile device a memory unit for storing a navigation widget and a navigation widget controller for controlling the wireless communication unit to transmit the location information of the mobile device to the web server for controlling the wireless communication unit to receive map data related to the location information from the web server and for controlling the display unit to display the map data and the location information.

In accordance with another aspect of the present invention a navigation service method using a mobile device which includes a GPS module a navigation widget controller a wireless communication unit and a display unit is provided. The method includes receiving location information of the mobile device through the GPS module controlled by the navigation widget controller transmitting the location information to a web server through the wireless communication unit controlled by the navigation widget controller receiving map data related to the location information from the web server through the wireless communication unit controlled by the navigation widget controller and displaying the map data and the location information on the display unit controlled by the navigation widget controller.

Other aspects advantages and salient features of the invention will become apparent to those skilled in the art from the following detailed description which taken in conjunction with the annexed drawings discloses exemplary embodiments of the invention.

Throughout the drawings it should be noted that like reference numbers are used to depict the same or similar elements features and structures.

The following description with reference to the accompanying drawings is provided to assist in a comprehensive understanding of exemplary embodiments of the invention as defined by the claims and their equivalents. It includes various specific details to assist in that understanding but these are to be regarded as merely exemplary. Accordingly those of ordinary skill in the art will recognize that various changes and modifications of the embodiments described herein can be made without departing from the scope and spirit of the invention. In addition descriptions of well known functions and constructions are omitted for clarity and conciseness.

The terms and words used in the following description and claims are not limited to the bibliographical meanings but are merely used by the inventor to enable a clear and consistent understanding of the invention. Accordingly it should be apparent to those skilled in the art that the following description of exemplary embodiments of the present invention are provided for illustration purpose only and not for the purpose of limiting the invention as defined by the appended claims and their equivalents.

It is to be understood that the singular forms a an and the include plural referents unless the context clearly dictates otherwise. Thus for example reference to a component surface includes reference to one or more of such surfaces.

In exemplary embodiments of the present invention a widget denotes a customized application that allows a user to edit a standby screen with mainly used contents and to directly activate desired services e.g. a clock weather a search a calendar a schedule stock and the like without accessing related web sites. Depending on types and features of target services a widget may be formed in a variety of manners such as a Java Script an Extensible Markup Language XML or an Open Application Programming Interface API . Since the widget may be activated in a standby screen the widget has an advantage of a faster loading time over typical applications.

In the exemplary embodiments of the present invention a navigation widget denotes a specific widget configured suitably for a navigation service. A navigation widget may be formed by using the Open API related to map data that a web server provides. Also a navigation widget may include instructions for a wireless communication unit in a mobile device to receive a list of candidate destinations and related map data from a web server. A navigation widget may further include instructions for a Global Positioning System GPS module in a mobile device to receive location information of the device from a GPS satellite. A navigation widget may still further include instructions for a display unit in a mobile device to display a location of the device on a map. A navigation widget may be redesigned to reflect a user s desired map to a navigation service system.

In the exemplary embodiments of the present invention a navigation widget controller may be included in a control unit of a mobile device and performs control functions for entire operations e.g. activation of a navigation widget of a navigation service system. A navigation widget controller controls a wireless communication unit to transmit location information of a mobile device to a web server and to receive map data in response to location information from a web server. A navigation widget controller then controls a display unit to display a device location on a map. Additionally a navigation widget controller controls a wireless communication unit to transmit a destination search keyword to a web server to receive a list of candidate destinations in response to a destination search keyword from a web server to transmit a selected destination in a list to a web server and to receive map data in response to a selected destination. Also a navigation widget controller controls a display unit to display a device location on a map.

In the exemplary embodiments of the present invention a navigation widget icon denotes a graphical object arranged in a standby screen to allow execution of a navigation service system. That is by touching a navigation widget icon if a mobile device has a touch screen or selecting a navigation widget icon through key input if a mobile device has a Liquid Crystal Display LCD a user may execute a navigation service system. If a navigation widget is embedded in a mobile device a navigation widget icon may appear in a standby screen through a user s menu selection. If a navigation widget is downloaded from a web server a navigation widget icon may appear in a standby screen automatically or through a user s menu selection.

The GPS also known as a global navigation satellite system is often used for navigation purposes. The GPS uses a constellation of satellites that transmit precise microwave signals which allow GPS receivers to determine their current location. In an exemplary implementation a GPS module in a mobile device has a GPS receiver communicating with GPS satellites to track the current location of the device.

The Open API denotes a user friendly open interface that web service providers open access ways to the public for specific functions or content services. While a traditional API denotes languages or messages used for communication between an Operating System OS and applications the Open API denotes languages or messages used for communication between web servers. As new programs are developed by using API it is also possible to develop new services by using the Open API. A number of web servers e.g. GOOGLE EBAY YAHOO NAVER and the like currently provide a variety of the Open APIs and also some web servers offer the Open API related to map data. In an exemplary implementation a mobile device may utilize destination data and map data stored in a web server by using the Open API that a web server provides. Additionally a user may redesign a navigation widget by using suitable Open APIs various web servers provide.

A web server is a server that provides web pages i.e. HyperText Markup Language HTML files . A web server has a specific domain name and may be equipped with a web server program capable of serving web pages using HyperText Transfer Protocol HTTP . In an exemplary implementation a web server provides map data and a list of candidate destinations to a mobile device. Also a web server provides the Open API for easier access to the web server from a mobile device.

Referring to the navigation service system includes a mobile device a GPS satellite a web server and a database .

The mobile device includes a GPS module and thereby receives location information of the mobile device from the GPS satellite . Also the mobile device accesses the web server and then receives navigation data such as maps and a list of candidate destinations from the web server .

The GPS satellite transmits location information of the mobile device to the GPS module embedded in the mobile device.

The web server provides navigation data such as maps and a list of candidate destinations to the mobile device being connected to the mobile device through a wireless internet network for example. Also the web server provides the Open API related to navigation data so that the mobile device may use navigation data such as maps and a list of candidate destinations.

The database stores navigation data including maps and a list of candidate destinations. The navigation data in the database is provided to the mobile device by the web server .

Referring to the mobile device includes a wireless communication unit an audio processing unit a display unit an input unit a memory unit a GPS module and a control unit .

The wireless communication unit includes a Radio Frequency RF unit and a data processing unit both of which are elements to execute wireless communications for the mobile device . The RF unit transmits and receives RF signals. Specifically the RF unit includes an RF transmitter not illustrated that up converts the frequency of transmission signals and amplifies transmission signals and an RF receiver not illustrated that down converts the frequency of reception signals and low noise amplifies reception signals. Although not illustrated the data processing unit is composed of an encoder a modulator both of which are used for transmission signals a decoder and a demodulator both of which are used for reception signals.

The audio processing unit which includes a microphone and a speaker performs functions of processing audio signals. The audio processing unit may provide a navigation voice service to a user.

The display unit displays various kinds of graphical information input by a user or offered to a user. The display unit may be formed of an LCD and the like. Also the display unit may be formed with a touch screen which performs portions or all of functions of the input unit . The display unit displays map data in connection with the location of the mobile device or the destination. Also the display unit displays the device location overlapped on the map data.

The input unit may be formed of a keypad a touchpad and the like. The input unit creates input signals based on user s manipulations and transmits the input signals to the control unit . For example a user may execute a navigation program through the input unit .

The memory unit stores user s information and a variety of programs required for operation of the mobile device . The memory unit may store a navigation widget that corresponds to a specific application created using the Open API that the web server provides.

The GPS module receives GPS satellite signals including location information of the mobile device from the GPS satellite and transmits the satellite signals to the control unit .

The control unit provides control signals required for entire operations of the mobile device . More particularly the control unit includes a navigation widget controller for the control of the navigation service system.

The navigation widget controller controls the wireless communication unit through activation of a navigation widget so that the wireless communication unit may receive map data and a list of candidate destinations from the web server . Also the navigation widget controller controls the GPS module through activation of a navigation widget so that the GPS module may receive location information of the mobile device from the GPS satellite . The navigation widget controller further controls the display unit through activation of a navigation widget so that the display unit may display map data and a device location.

Referring to the DataBase DB includes a destination list DB and a map data DB . Additionally the map data DB has a display DB a network DB and a guide DB .

The destination list DB stores a list of addresses in connection with destinations including domestic and foreign countries . When a user requests a destination list to the web server by inputting a destination search keyword the web server retrieves a list of candidate destinations in connection with the keyword input from the destination list DB and transmits the list to the mobile device .

The map data DB stores map image data that will be displayed on the display unit of the mobile device . The display DB the network DB and the guide DB in the map data DB stores display format data road line data and route guidance data respectively.

In an exemplary implementation the mobile device has a navigation widget stored therein and the navigation widget controller embedded therein. The navigation widget and the navigation widget controller may be equipped in the mobile device before launching or may be installed in the mobile device through a download.

Referring to the navigation widget controller of the mobile device activates the navigation widget in step S in response to a user s manipulation of a navigation widget icon which is displayed on the display unit in a standby state. If the navigation widget is embedded in the mobile device the navigation widget icon may appear in a standby screen through a user s menu selection. If the navigation widget is downloaded from the web server the navigation widget icon may appear in a standby screen automatically or through a user s menu selection.

Referring to if the mobile device is formed with a touch screen the navigation widget is activated when a user touches the navigation widget icon in a standby screen. If the mobile device is formed with an LCD the navigation widget is activated when a user selects the navigation widget icon through key input using the input unit . Additionally a shortcut key may be established for activation of the widget.

Referring to the navigation widget icon may be arranged at different positions in different shapes. A user may change the position of the navigation widget icon through a drag action in case of a touch screen or by using key buttons in case of an LCD . Also the shape of the navigation widget icon may vary with a user s selection.

Returning to when the navigation widget is activated the mobile device requests information related to the current location of the mobile device to the GPS satellite in step S. The mobile device then receives GPS satellite signals including information related to the device location from the GPS satellite through the GPS module in step S. On receipt of GPS signals the mobile device accesses the web server and transmits current location information of the mobile device to the web server through the wireless communication unit in step S. In response to location information of the mobile device the web server retrieves map data from the map DB in step S. The mobile device then receives map data from the web server through the wireless communication unit in step S and displays the received map data and the current location of the mobile device on the display unit in step S.

Referring to a map related to the current location of the mobile device is received from the web server and displayed on the display unit . Additionally the current location of the mobile device is received from the GPS satellite and overlapped with the map displayed on the display unit .

Referring to a map has a scaled down form and is arranged in a portion of a standby screen. When a user touches or selects the navigation widget icon illustrated in the icon disappears and the map appears at the position of the icon. The scaled down form of the map may be increased or decreased in size and moved through a drag action in case of a touch screen or by using key buttons in case of an LCD without touchscreen capabilities .

However the GPS satellite begins to transmit information related to the current information of the mobile device to the GPS module in step S and continues such transmission in real time until the navigation widget is ended.

The navigation widget includes the Open API the web server provides. Also the navigation widget includes several instructions for the wireless communication unit to receive a list of candidate destinations and related map data from the web server for the GPS module to receive device location information from the GPS satellite and for the display unit to display the device location on map data.

Referring to while the mobile device receives current location information from the GPS satellite and map data related to the current location from the web server in step S a keyword for destination search is input through the input unit of the mobile device in step S. The input of the destination search keyword may be performed while or before the GPS module receives the current location of the mobile device from the GPS satellite .

Referring to when the map is displayed with the current device location as illustrated in a search icon may also be displayed on the map . If the search icon is touched or selected a screen on the display unit is changed from the map to the input screen for destination search illustrated in . In an exemplary implementation the input screen may appear immediately after the navigation widget is activated through a touch or selection of the navigation widget icon as illustrated in . When the input screen is displayed a user inputs a keyword e.g. Store for destination search through the input unit .

Returning to when a keyword for destination search is input the mobile device transmits the keyword to the web server to request candidate destinations related to the keyword in step S. The web server then retrieves a list of candidate destinations from the destination list DB in step S and transmits the list to the mobile device in step S.

Referring to the mobile device displays a list that includes several candidate destinations e.g. a main branch of Store a branch A of Store and the like related to the keyword e.g. Store .

Returning again to a user selects one of the candidate destinations in the list in step S and the mobile device transmits the selected destination to the web server to request related map data in step S.

The web server retrieves map data related to the selected destination from the map data DB in step S and transmits the map data to the mobile device in step S. The mobile device starts a navigation service to the destination while displaying the map data and the current device location on the display unit in step S.

Referring to the mobile device displays a current location of the mobile device that is represented as a dot in the map and a guide path to the destination that is represented as a dotted line in the map. During a navigation service the mobile device may further provide voice guidance through the speaker.

As described above the navigation service system of exemplary embodiments of the present invention may provide a navigation service to a user of the mobile device without requiring a map embedded mobile device. Therefore updating map data is not required. Also it is possible to easily use a navigation system in foreign countries.

Furthermore the navigation service system may allow a user to reflect desired map data by redesigning a navigation program thus implementing a wide selection of map data.

Additionally the widget based navigation program may reduce a loading time of the navigation service system.

While this invention has been shown and described with reference to certain exemplary embodiments thereof it will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the spirit and scope of the invention as defined by the appended claims and their equivalents.

