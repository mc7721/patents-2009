---

title: Notification apparatus, notification system, method of operating notification apparatus, and program for notification apparatus
abstract: A management apparatus of a notification system includes an interface unit that communicates with a store terminal used for a predetermined site work process by a site worker and an IP telephone terminal used for IP phone call, which are located at one work site; an accepting unit that accepts an emergency notification to the site worker; a display control unit that displays and outputs the accepted emergency notification on the store terminal via the interface unit; and a calling unit that calls the IP telephone terminal via the interface unit to make the site worker recognize the emergency notification.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08451982&OS=08451982&RS=08451982
owner: NEC Corporation
number: 08451982
owner_city: Tokyo
owner_country: JP
publication_date: 20090706
---
This application is based upon and claims the benefit of priority from Japanese patent application No. 2008 181028 filed on Jul. 11 2008 the disclosure of which is incorporated herein in its entirety by reference.

The present invention relates to a notification apparatus a notification system a method of operating a notification apparatus and a program for notification apparatus and more particularly to a notification apparatus a notification system a method of operating a notification apparatus and a program for notification apparatus that report an emergency to a terminal located at a work site.

It is described that confirmation of opening is made when a notification of a message having a high emergency is transmitted to an addressee in Japanese Laid open patent publication No. 2000 341431 for example.

For example when a need for emergency notification to a plurality of stores occurs in a system that performs pop up display of an emergency notification message on a screen of a POS terminal of the stores the confirmation by opening of the message can be managed out by the system. However there may be a danger in that the store side does not notice the message causing a delay of the opening of the message of emergency.

An exemplary object of the invention is to provide a notification apparatus a notification system a method of operating a notification apparatus and a program for a notification apparatus that can make the site workers notice the emergency notification promptly and with certainty.

a terminal communication unit that communicates with an information processing terminal used for a predetermined site work process by a site worker and an Internet Protocol IP telephone terminal used for IP phone call which are located at one work site 

an emergency displaying unit that displays and outputs the accepted emergency notification on the information processing terminal via the terminal communication unit and

an emergency calling unit that calls the IP telephone terminal via the terminal communication unit to make the site worker recognize the emergency notification.

an information processing terminal that is located at a work site and used for a predetermined site work process by a site worker 

a management apparatus that is connected to the information processing terminal and the IP telephone terminal via a network wherein

a displaying unit that performs display processing controlled by the management apparatus via the communication unit 

a ringing unit that receives a call from the management apparatus via the communication unit and sounds the ring tone and

a communication unit that communicates with the information processing terminal and the IP telephone terminal via the network 

an emergency displaying unit that communicates with the information processing terminal via the communication unit and allows the emergency notification accepted by the accepting unit to be displayed and output on the displaying unit of the information processing terminal and

an emergency calling unit that communicates with the information processing terminal via the communication unit and calls the IP telephone terminal thereby making the site worker recognize the emergency notification.

A method of operating a notification apparatus according to an exemplary aspect of the invention that communicates with an information processing terminal used for a predetermined site work process by a site worker and an IP telephone terminal used for IP phone call which are located at one work site includes 

making the notification apparatus display and output the accepted emergency notification on the information processing terminal and

making the notification apparatus call the IP telephone terminal to make the site worker recognize the emergency notification.

A program according to an exemplary aspect of the invention allows a computer to realize a notification apparatus that communicates with an information processing terminal used for a predetermined site work process by a site worker and an IP telephone terminal used for IP phone call which are located at one work site wherein the program allows the computer to execute 

a reception procedure by which the notification apparatus accepts an emergency notification to the site worker 

an emergency displaying procedure by which the notification apparatus displays and outputs the accepted emergency notification on the information processing terminal and

an emergency calling procedure by which the notification apparatus calls the IP telephone terminal to make the site worker recognize the emergency notification.

Here any combination of the above described constituent elements as well as conversion of the expression of the present invention among methods apparatuses systems recordation media computer programs and others is also effective as a mode of the present invention.

Also various constituent elements of the present invention need not necessarily be individually independent and there may be a case in which a plurality of constituent elements are formed into one member a case in which one constituent element is formed with a plurality of members a case in which one constituent element is a part of another constituent element a case in which the a part of one constituent element and a part of another constituent element overlap with each other and the like cases.

Though the method and the computer program of the present invention recite a plurality of procedures in order the order of description does not limit the order of execution of the plurality of procedures. For this reason in executing the method and the computer program of the present invention the order of the plurality of procedures can be changed within a range that does not deteriorate the scope of the present invention.

Also the plurality of procedures of the method and the computer program of the present invention are not limited to being executed at timings that are individually different from each other. For this reason there may be a case in which another procedure is performed while a certain procedure is being executed a case in which an execution timing of a certain procedure and an execution timing of another procedure are partly or wholly overlapped with each other and the like cases.

According to the present invention there are provided a notification apparatus a notification system a method of operating a notification apparatus and a program for notification apparatus that can make the site worker notice the emergency notification promptly and with certainty.

The invention will now be described herein with reference to illustrative exemplary embodiments. Those skilled in the art will recognize that many alternative exemplary embodiments can be accomplished using the teachings of the present invention and that the invention is not limited to the exemplary embodiments illustrated for explanatory purposes.

Here in all of the drawings like constituent elements will be denoted with like reference numerals and the description thereof will not be repeated.

The notification system of the present exemplary embodiment includes an information processing terminal store terminal that is located at a work site store S and used for a predetermined site work process by a site worker store clerk an IP telephone terminal that is located at the work site store S and used for IP phone call and a management apparatus that is connected to the store terminal and the IP telephone terminal via a network . The store terminal includes a communication unit IP communication unit of that communicates with the management apparatus via the network and a displaying unit touch panel of that performs display processing controlled by the management apparatus via the IP communication unit . The IP telephone terminal includes a communication unit IP communication unit of that communicates with the management apparatus via the network and a ringing unit alarm speaker of that receives a call from the management apparatus via the IP communication unit and sounds the ring tone. The management apparatus includes an interface unit that communicates with the store terminal and the IP telephone terminal via the network an accepting unit that accepts an emergency notification to the site worker store clerk a display controlling unit that communicates with the store terminal via the interface unit and allows the emergency notification accepted by the accepting unit to be displayed and output on the touch panel of the store terminal and a calling unit that communicates with the store terminal via the interface unit and calls the IP telephone terminal to make the site worker store clerk recognize the emergency notification.

Specifically the notification system includes a management apparatus and a plurality of store servers that are connected to the management apparatus via a network such as the Internet a WAN Wide Area Network or a LAN Local Area Network and respectively located at a plurality of stores Sa Sb In only two stores are depicted. Hereafter they will be abbreviated as store S that are managed by the management apparatus . Further in each store S the store server includes an interface unit I F that communicates with the management apparatus via the network and is connected to at least one store terminal and at least one IP telephone terminal via a network such as a LAN.

The management apparatus and the store server are server computers. The management apparatus and the store server are what are known as Session Initiation Protocol SIP servers and realize various functions for the management apparatus and the store server by executing corresponding computer program CP that is mounted on a memory not illustrated in the drawings .

As shown in this computer program CP includes a general use operating system OS that is not specialized to each store S and an application software AS corresponding to each store S.

This application software AS includes for example of module softwares MS such as various kinds of widgets that are prepared in advance by being specialized to respective specific functions a customizing software CS such as an Application Programming Interface API that integrates these module softwares MS in correspondence with the desires of each store S and the like.

Returning to in the present exemplary embodiment the store terminal is for example what is known as a POS Point Of Sales terminal and is located for each of the plurality of cashier units not illustrated in the drawings in the store. The IP telephone terminal is an IP telephone set that is located at the same work site as the store terminal . Here in the construction of the parts that will not be essentially related to the gist of the present invention and not be illustrated in the drawings.

Also each of the constituent elements of the notification system is realized by an arbitrary combination of hardware and software including at the center thereof a CPU of an arbitrary computer a memory a program that realizes the constituent elements of the present drawings and that is loaded on the memory a storage unit such as a hard disk that stores the program and an interface for connection to the network. Then those skilled in the art will understand that there may be various modifications to the method of realization thereof and the apparatus. Each of the drawings described in the following shows a block of a functional unit rather than the construction of a hardware unit.

The management apparatus includes an accepting unit a display controlling unit a calling unit a sound output controlling unit a detecting unit a recording unit a history storing unit which is denoted as history in the drawings and an interface unit I F .

The interface unit communicates with the store server of each store S via the network . The accepting unit accepts an emergency notification to the store S by operation input into an operation unit or the like that is not illustrated in the drawings. For example the accepting unit accepts input of various information such as designation of a store or a group to which the emergency notification should be issued setting of an emergency level input of the specific contents object commercial products contents whether the products must be recalled or not of the notification and input of certification information. The emergency notification information that has been accepted by the accepting unit is recorded to the history storing unit by the recording unit .

Here although not illustrated in the drawings the management apparatus includes a database that stores information of the store servers of the plurality of stores S to be managed.

The display controlling unit transmits the emergency notification that has been accepted by the accepting unit to the store server of each store S via the interface unit and allows the emergency notification to be displayed and output on a touch panel of the store terminal described later. Here the display controlling unit may manage only the store server instruct the store server to perform the display and output of the emergency notification so that the store server instructs the plurality of store terminals under the management of the store server to perform the display and output or alternatively the display controlling unit may manage the plurality of store terminals of each store S and control the display and output.

As shown in in the present exemplary embodiment an emergency notification screen includes for example an emergency notification mark a content displaying column and a confirmation button . The emergency notification mark is displayed conspicuously so that the store clerk of the store S immediately recognizes that the present screen is an emergency notification. It may be a blinking display or a moving picture. In the content displaying column the contents of the emergency notification are described. The confirmation button is operated after the store clerk of the store S confirms the emergency notification screen . By pressing the confirmation button down the emergency notification screen may be closed after a confirmation screen. Also the management apparatus may be informed of the confirmation of the emergency notification via the store server .

Returning to the calling unit transmits the emergency notification accepted by the accepting unit to the store server of each store S via the interface unit and calls a later described IP telephone terminal via the store server . Here the calling unit may manage only the store server and instruct the store server so that the store server calls a plurality of IP telephone terminals that are under the management of the store server . Alternatively the calling unit may manage and directly call the plurality of IP telephone terminals of each store S. As will be described later when called the IP telephone terminal can receive a call and then sound the ring tone so as to inform the store clerk.

The sound output controlling unit allows a sound message to be output to the IP telephone terminal by sound when the store clerk of the store S or the like makes a response at each IP telephone terminal that the calling unit has called. For example the sound output controlling unit may allow a notification message of This is an emergency notification. that notifies that an emergency notification has been issued an instruction message of This is an emergency notification. Look at the screen. that prompts the clerk to look at the screen because the emergency notification has been issued an emergency message of This is an emergency notification. Quickly recall the commercial products A. that transmits the contents themselves of the emergency notification or the like to be output by sound.

The detecting unit detects whether the site worker store clerk has responded to the calling of the emergency notification to the IP telephone terminal . The detecting unit may make an inquiry to the store server of each store S via the interface unit or may receive notification from the store server of each store S.

As described above the recording unit records the emergency notification information accepted by the accepting unit to the history storing unit and records to the history storing unit a detection result of each store S detected by the detecting unit as to whether the calling of the emergency notification has been responded to or not.

The history storing unit stores for example date and time of the receipt a code of the store or group serving as an object of notification an emergency level contents whether the certification has been successfully made or not the situation of notification confirmation for each store date and time of repeated notification and the like as the emergency notification information accepted by the accepting unit .

The management apparatus of the present exemplary embodiment executes various processing operations in accordance with the computer program mounted as described above and whereby various units to such as described above are realized as various functions.

The computer program according to the present exemplary embodiment is a program for allowing a computer to realize a notification apparatus management apparatus that communicates with an information processing terminal store terminal used for a predetermined site work process by a site worker store clerk and an IP telephone terminal IP telephone terminal used for IP phone call which are located at one work site wherein the program is described so as to allow the computer to execute a reception procedure by which the management apparatus accepts an emergency notification to the site worker store clerk an emergency displaying procedure by which the management apparatus displays and outputs the accepted emergency notification on the store terminal and an emergency calling procedure by which the management apparatus calls the IP telephone terminal to make the site worker store clerk recognize the emergency notification.

As illustrated in in the present exemplary embodiment the store terminal includes an IP communication unit a register unit an input unit an alarm speaker and a touch panel .

A microcomputer is incorporated into the IP communication unit and integrates and controls each of the units such as the register unit the input unit the alarm speaker and the touch panel in accordance with the computer program on a mounted memory not illustrated in the drawings .

The register unit is a unit that obtains and sums up the commercial product information from a bar code of a commercial product read by the input unit at the time of selling the commercial product and performs a settlement process and the like. It is not related to the essentials of the present invention however so that the detailed description thereof will not be given.

The input unit includes not be particularly limited to a reading unit that reads commercial product information from a bar code or a Radio Frequency Identification RFID tag attached to the commercial product and an operation accepting unit such as an operation key a keyboard an operation button a switch a jog dial or a touch pad that accepts an operation of the store clerk. The input unit accepts the commercial product information or the input operation that the reading unit or the operation accepting unit has accepted and transmits it to the IP communication unit .

The touch panel may be with respect to the displaying function not be particularly limited to for example a liquid crystal display a plasma display an organic Electroluminescence EL display or the like. The touch panel may accept with respect to the operation accepting function not be particularly limited to an operation by a finger of a user an operation using a touch pen or a combination of these.

In the present exemplary embodiment when an emergency notification is issued from the management apparatus an emergency notification screen is displayed in pop up on the touch panel of the store terminal . This pop up display is displayed more preferentially than any other screen and in the event that a plurality of screens are displayed this pop up screen is displayed on the topmost surface.

As shown in in the present exemplary embodiment the IP telephone terminal includes an IP communication unit a handset unit an operation unit an alarm speaker and a touch panel .

A microcomputer is incorporated into the IP communication unit and integrates and controls each of the units such as the handset unit the operation unit the alarm speaker and the touch panel in accordance with the computer program on a mounted memory not illustrated in the drawings .

The handset unit has a handset speaker and a handset microphone . For example the handset unit may be a unit that can be removed from a main body of the IP telephone terminal as a construction capable of wireless communication with the IP telephone terminal . The user such as a site worker for example a store clerk of a store in the present exemplary embodiment may make a phone call over the IP telephone terminal using the handset speaker and the handset microphone of the handset unit .

The operation unit includes not be particularly limited to an operation key an operation button a switch a jog dial a touch pad or the like that accepts an input operation of a telephone number or other operations and after accepting these operations transmits them to the IP communication unit . The alarm speaker for example outputs a calling sound at the time of receiving a call and outputs a received voice. In the present exemplary embodiment when a call from the management apparatus is received a ring tone is rung from the alarm speaker .

The touch panel may be with respect to the displaying function not be particularly limited to for example a liquid crystal display a plasma display an organic EL display or the like. The touch panel may accept with respect to the operation accepting function not be particularly limited to an operation by a finger of a user an operation using a touch pen or a combination of these.

Hereafter a method of operating a notification apparatus in the notification system of the present exemplary embodiment constructed as shown above will be described. is a flowchart showing an example of an operation of the notification system of the present exemplary embodiment.

The method of the present exemplary embodiment is a method of operating a notification apparatus management apparatus that communicates with an information processing terminal store terminal used for a predetermined site work process by a site worker store clerk and an IP telephone terminal used for IP phone call which are located at one work site store S . The method includes making the management apparatus accept an emergency notification to the site worker store clerk YES of step S making the management apparatus display and output the accepted emergency notification on the store terminal step S and making management apparatus call the IP telephone terminal to make the site worker store clerk recognize the emergency notification step S .

Specifically in the management apparatus the accepting unit accepts an emergency notification YES of step S . The accepting unit allows the recording unit to record the emergency notification information to the history storing unit and instructs the display controlling unit and the calling unit to issue a notification.

In the management apparatus the display controlling unit allows the store server of the store serving as an object of notification to display and output the emergency notification via the network step S . The store server receives the emergency notification from the management apparatus and allows the touch panel of the store terminal to perform pop up display of the emergency notification screen for the emergency notification step S .

Further in the management apparatus the calling unit instructs the store server of the store serving as an object of notification to call the IP telephone terminal via the network step S . The store server receives the calling instruction of the emergency notification from the management apparatus and calls the IP telephone terminal so that the IP telephone terminal receives the call and sounds the ring tone through the alarm speaker step S . By this the store clerk of the store S can immediately notice the ring tone and take a procedure of responding over the IP telephone terminal .

The store clerk that has responded over the IP telephone terminal for example hears the notification message from the alarm speaker of the IP telephone terminal looks at the touch panel of the store terminal that is located at the same work site and confirms the emergency notification screen . When the store clerk has responded over the IP telephone terminal in the management apparatus the detecting unit detects that the IP telephone terminal has responded to the calling of the emergency notification YES of step S and the recording unit records the date and time of the confirmation and the like to the history storing unit step S .

Here although not illustrated in the drawings when no response has been made for more than a predetermined period of time to the calling by the emergency notification of the IP telephone terminal the calling by the calling unit is stopped and the recording unit records that there has been no response to the history storing unit .

As described above the notification system of the present exemplary embodiment can allow the store clerk to notice the emergency notification promptly and with certainty by allowing the store terminal that the store clerk of the store uses to perform a pop up display output of the message of the emergency notification by calling the IP telephone terminal that is used on the side of the store terminal and by ringing. Thus the store clerk can notice the notification outstandingly easily as compared with the case of using only the pop up display.

Also a case in which the store terminal outputs an alarm sound may be considered. However in the case of the store terminal placed in the store there is a possibility that the volume of the speaker is adjusted and lowered on the store side leaving a fear that the store clerk may not notice the alarm sound.

By using the IP telephone terminal in addition to ringing when the store clerk has answered the call a sound massage telling the presence or absence of the message of the emergency notification and a content itself of the message of the emergency notification can be output by sound thereby transmitting the message to the store clerk.

The notification system of the present exemplary embodiment can be easily constructed by newly introducing the IP telephone terminal to the store system using an existing POS terminal. As shown in it can be easily realized by being incorporated into an application software AS as a module software MS or a customizing software CS constituting the present notification system .

Also the notification system of the present exemplary embodiment can be applied for example to a food distribution site where various kinds of boxed meals are produced from a food processing factory such as prepared daily dishes and sold at a convenience store or a shop. For example in the event that any problem has been found in the source material of the food and the food must be recalled urgently the notification system of the present exemplary embodiment can issue an instruction of recalling the commercial product as an object of recall to each store to be recalled promptly and with certainty.

As shown above the exemplary embodiments of the present invention have been described. However these are exemplifications of the present invention so that one can adopt various constructions other than those described above.

For example in another exemplary embodiment the IP telephone terminal may include a reading apparatus not illustrated in the drawings that reads the certification information of the user store clerk of a medium for user certificate and the certification information of the medium for user certificate of the site worker store clerk is read in accordance with the calling of the emergency notification and transmitted to the management apparatus via the store server . The management apparatus may include a receiving unit not illustrated in the drawings that receives the certification information of the site worker store clerk that has responded to the calling to the IP telephone terminal from the IP telephone terminal via the interface unit and a certification unit not illustrated in the drawings that certifies the site worker store clerk based on the certification information of the site worker store clerk .

Further the recording unit of the management apparatus records to the history storing unit that the site worker store clerk has not responded to the calling of the emergency notification at the work site when the site worker store clerk has not been certified by the certification unit. Further recording unit records to the history storing unit the certified site worker store clerk as the site worker store clerk that has responded to the calling of the emergency notification at the work site when the site worker store clerk has been certified by the certification unit.

The medium for user certificate may be a magnetic card an ID card an RFID tag or the like. Alternatively it may be a biometric authentication so that various modes such as a fingerprint a vein an iris and a face are may be considered.

With this construction the site worker store clerk that has responded to the IP telephone terminal and recognized the emergency notification can be identified and whereby the site worker store clerk that confirms the emergency notification may possibly confirm the contents of the emergency notification with responsibility. Also when a person other than the person in charge or an outsider has confirmed the emergency notification the output of the emergency notification can be continued until the person in charge confirms the emergency notification so that the emergency notification can be transmitted to the person in charge with certainty.

Further the management apparatus may further include a controlling unit not illustrated in the drawings that allows the calling unit to call the IP telephone terminal with respect to a work site at which it is recorded that there is no response to the emergency notification by the site worker store clerk by making reference to the history information recorded in the history storing unit .

With this construction with respect to a store S that has not responded to the calling of the emergency notification the calling unit may be made to call the IP telephone terminal repetitively for each store S.

Also in the management apparatus the above controlling unit may allow the display controlling unit to display and output the emergency notification again on the store terminal of the store S.

Further the detecting unit may receive not only the response of the IP telephone terminal but also the confirmation notification of the emergency notification by an operation of the confirmation button of the emergency notification screen displayed on the touch panel of the store terminal and allow the recording unit to record them to the history storing unit .

Here in the above described exemplary embodiment a construction has been given in which the message of the emergency notification is popped up on the displaying unit touch panel of the information processing terminal store terminal however the present invention is not limited thereto. For example the IP telephone terminal may have a displaying unit touch panel having a screen size capable of displaying a message and the display controlling unit of the management apparatus may allow the touch panel of the IP telephone terminal to display and output a message of an emergency notification. Alternatively the display controlling unit of the management apparatus may allow the displaying unit not illustrated in the drawings of the store server to display and output a message of an emergency notification.

While the invention has been particularly shown and described with reference to exemplary embodiments thereof the invention is not limited to these embodiments. It will be understood by those of ordinary skill in the art that various changes in form and details may be made therein without departing from the spirit and scope of the present invention as defined by the claims.

