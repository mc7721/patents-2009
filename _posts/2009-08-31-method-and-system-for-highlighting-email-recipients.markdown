---

title: Method and system for highlighting email recipients
abstract: A method and system for highlighting email recipients according to a user's social network are provided. The method includes receiving an email message at a user's email client, the email message having multiple recipients, one of the recipients being the user. The method further includes obtaining a social network list for the user and comparing the social network list for the user with the email message recipients and highlighting recipients in the email message who are also in the social network list. The social network list for a user may be obtained by different methods including using the user's contact resources, or using an aggregating social network system including weighting relationships between contacts.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09436932&OS=09436932&RS=09436932
owner: International Business Machines Corporation
number: 09436932
owner_city: Armonk
owner_country: US
publication_date: 20090831
---
This invention relates to the field of email messaging. In particular the invention relates to highlighting email recipients.

Many email messages both within organizations and outside the firewall are directed to a large amount of recipients. While in some cases it is not very interesting for the recipient of an email message to be aware of other recipients of the message in many other cases the recipient of the message is interested to know who else that he she knows received the message. For example a manager wants to see if any of his employees received the message or a user wants to observe whether any of his close friends received the message as well.

For emails addressed to many recipients the recipient list in the To and or Cc header field gets harder to digest for the reader as those headers become larger. Thus finding specific people on those lists becomes a time consuming problem.

According to a first aspect of the present invention there is provided a method for highlighting email recipients comprising receiving an email message at a user s email client the email message having multiple recipients one of the recipients being the user obtaining a social network list for the user comparing the social network list for the user with the email message recipients and highlighting recipients in the email message who are also in the social network list wherein any of said steps are implemented in either of computer hardware or computer software embodied in a computer readable medium.

The method may include determining if a received email message has greater than a threshold number of recipients and activating the highlighting step.

In one embodiment obtaining a social network list for the user may include accessing a contact list from one or more of the user s resources. The method may include combining multiple contact lists from the user s resources to obtain a social network list for the user.

In an alternative embodiment obtaining a social network list for the user may include aggregating social network information from sources external to the user. Aggregating social network information may include weighting relationships between contacts. This may include restricting the social network information to a given time range.

The method may include receiving notification from a server of highlighted recipients who have read the email message and providing additional highlighting of recipients of the email message who have read the email message.

The method may further include adapting the social network list according to the context of the email message.

According to a second aspect of the present invention there is provided a method of providing a service to a customer over a network the service comprising obtaining a social network list for a user comparing the social network list for the user with email message recipients of a received email message and highlighting recipients in the email message who are also in the social network list wherein any of said steps are implemented in either of computer hardware or computer software embodied in a computer readable medium.

According to a third aspect of the present invention there is provided a computer program product for highlighting email recipients the computer program product comprising a computer readable medium computer program instructions operative to receive an email message at a user s email client the email message having multiple recipients one of the recipients being the user obtain a social network list for the user compare the social network list for the user with the email message recipients and highlight recipients in the email message who are also in the social network list wherein said program instructions are stored on said computer readable medium.

According to a fourth aspect of the present invention there is provided a system for highlighting email recipients comprising an email client application at which an email message is received having multiple recipients one of the recipients being the user the email client including a social network retrieval component for obtaining a social network list for the user a comparison component for comparing the social network list for the user with the email message recipients and a display component for highlighting recipients in the email message who are also in the social network list wherein any of said email client application social network retrieval component comparison component and display component are implemented in either of computer hardware or computer software and embodied in a computer readable medium.

The system may include a user interface for setting parameters regarding the highlighting of recipients.

The system may include an activation component for determining if a received email message has greater than a threshold number of recipients and activating the highlighting step.

In one embodiment the social network retrieval component may include accessing contact lists from one or more of the user s resources. The social network retrieval component may combine multiple contact lists from the user s resources to obtain a social network list for the user.

In another embodiment the social network retrieval component may aggregate social network information from sources external to the user. The social network retrieval component may aggregate social network information including weighting relationships between contacts. The social network retrieval component may also include restricting the social network information to a given time range.

The system may include a server for receiving read events for email messages by recipients the email client application including a recipient read notification mechanism for receiving notification from the server of highlighted recipients who have read the email message and the display component providing additional highlighting of recipients of the email message who have read the email message.

The system may also include a context component for adapting the social network list according to the context of the email message.

In email messages addressed to a large amount of people it is often hard for a recipient of the message to observe other relevant co recipients who appear on the message. Highlighting of recipients is proposed from the user s social network who also appear as recipients of the message.

It is proposed that email clients are adapted to highlight for the user recipients who are found to be related to him. In this way the user can easily detect who he knows who also received the message.

It will be appreciated that for simplicity and clarity of illustration elements shown in the figures have not necessarily been drawn to scale. For example the dimensions of some of the elements may be exaggerated relative to other elements for clarity. Further where considered appropriate reference numbers may be repeated among the figures to indicate corresponding or analogous features.

In the following detailed description numerous specific details are set forth in order to provide a thorough understanding of the invention. However it will be understood by those skilled in the art that the present invention may be practiced without these specific details. In other instances well known methods procedures and components have not been described in detail so as not to obscure the present invention.

Upon viewing an email message in a user s email client the described method and system allow highlighting of recipients within the user s social network. The highlighting can be done in any appropriate manner for example by using a larger font bold and or a different color. An option mechanism such as a button or menu option is provided that allows the user control over the highlighting feature.

2 . Social network highlighting for all messages is set and upon user selection highlighting will stop.

3 . Social network highlighting for messages with above X recipients is set for example X 20. Upon user selection highlighting un highlighting will occur. Controlling X can be allowed to the user through user preferences.

The core of the highlighting mechanism is retrieving the appropriate social network for the user according to which highlighting will occur. Two possible embodiments are described for this.

The first embodiment uses an unweighted social network list that can be retrieved from the user s contact lists in the user s own sources. For example the user s contact lists may include his address book instant messaging IM buddylist or a social network service SNS contacts for example IBM s IBM is a trade mark of International Business Machines Corporation internal Enterprise Social Network Site see Dimicco J. M. Geyer W. Millen D. R. Dugan C. and Bronholtz B. People Sensemaking and Relationship Building on an Enterprise Social Network Site 2009 1 10 or Facebook Facebook is a trade mark of Facebook Inc. . The social network list can be retrieved as the contact list from one of the user s sources or it can be retrieved by using combinations of the user s sources by union or intersection. The final outcome is a flat list of user IDs. These user IDs will be highlighted upon receiving of messages on whose header they co occur with the user.

A second embodiment uses an aggregating social network system for example a system such as SONAR SOcial Networking ARchitecture see reference Harvesting with SONAR The Value of Aggregating Social Network Information I. Guy M. Jacovi E. Shahar N. Meshulam V. Soroka S. Farrell In proc. of CHI 2008 . An aggregating social network system such as SONAR can provide a weighted social network list with scores representing the strength of relationships based on various data sources. The data source may be from across an organization or other social network sources. Using SONAR to retrieve the user s social network more parameters can be taken into account while making a decision of which recipients to highlight. These parameters may include 

Referring to a block diagram shows an email system as described. The email system includes an email client application hosted by a user s system which retrieves email messages from a remote email server via a network . The email client application receives email messages which include a recipient list in the email message s header in the to and cc fields. The email client application also includes an address list of the email addresses used by the user.

The email client application is extended to include a social network highlighting mechanism as described. The social network highlighting mechanism includes an activation component to determine if the social network highlighting is to be activated when an email message is received. The social network highlighting mechanism also includes a social network retrieval component for retrieving a social network list to be used by the highlighting mechanism . The highlighting mechanism includes a comparison component for comparing the recipient list of an email message with the social network list . The social network highlighting mechanism also includes a display component for changing the display of the recipients in the email message . A user settings component is provided in the social network highlighting mechanism in order for the user to set user preferences relating to the highlighting.

The user system may also include other sources of contact information such as an instant messaging application including a contacts list . The user system may also include a web browser application for accessing other sources of contact information such as social network services via a network .

In one embodiment the social network retrieval component of the highlighting mechanism uses user s sources of contact information such as the email address list an instant messaging contact list and social network service contact lists to determine the social network list .

In another embodiment the social network retrieval component of the highlighting mechanism uses external sources of contact information such as an aggregating social network system which gathers and weights social network information relating to the user from external sources as described further below.

While the social network highlighting mechanism may provide appropriate defaults for the parameters of the highlighting the user may have control over them as well by inputting preferences in the user settings component . A preference menu is provided in which the user can control parameters such as the strength threshold the time window to consider and the data sources to take into account. This is shown further in relation to .

After automatically retrieving the user s social network by the social network retrieval component the user may be given manual control over the list by removing or adding people.

In each of the two embodiments unweighted and weighted social networks the IDs of the people on the entire network are mapped to email addresses. Based on these addresses highlighting takes place.

An extension to the highlighting feature may be provided to display information about which recipients in the user s social network have already read an email message. This can be done by a second different form of highlighting font and or color . Providing this information may facilitate collaboration for the user around the subject of the message and in some cases may even spare him the need to read the whole message.

The general case is considered where the email client application and the social network from which information about relationships is drawn are different. In this case the email client application would store in a server information per user and per message for which the user is a recipient which will indicate whether the user has already read the message. This will be done based on events sent to the server upon opening a message on the client side. Then when one of the message recipients opens it and ask for the feature of highlighting the social network as well as highlighting who from the social network has read the message the email client application would issue a call for the server with all the relevant people the recipients of the message who are part of the user s social network . The server will return for each of the individuals the read unread status per the information stored. Based on this information highlighting of read unread is performed.

Read notification highlighting is very useful in the workplace in fostering collaboration around email messages. In some cases it may help a user in deciding whether to skip reading a message. A second line manager may be able to get an indication of which of his first liners have already read the message. A project team member can also get an indication of whether a message has been read by other team members.

Referring to the email system of is shown with the extension of a recipient read notification mechanism provided in the email client application .

A read notification server is provided which maintains a record of users and email messages . Email recipients of an email message send read events for the message to the read notification server which updates its records of users who have read a message .

The recipient read notification mechanism at the user s email client application calls the read notification server with the social network list to find out which of the recipients on the social network list have read the email message . A return status is returned allowing the social network highlighting mechanism of the user s email client application to additionally highlight recipients of the email message in the user s social network list who have read the email message .

A further embodiment is provided in which the social network based on which the highlighting occurs is adapted to the specific context of the email message. For differing types of messages differing highlighting will take place. This can be implemented with an aggregating social network system such as SOcial Networking ARchitecture SONAR and a search engine as implemented in Social Networks and Discovery SaND see reference Ronen I. Shahar E. Ur S. Uziel E. Yogev S. Zwerdling N. Carmel D. Guy I. Har el N. and Ofek Koifman S. Social networks and discovery in the enterprise SaND In 2009 836.

The SaND system allows combining social network and content information and supports querying for a user s social network within a given context. The context can be described by a search query by combining several keywords e.g. recommender systems . Using a system like SaND which is an extension to SONAR the email application may ask for the social network of the user with respect to the context of the email message. The context of the email message can be derived for example by the title or by extracting the most meaningful keywords from the message s body. The user can then choose to highlight the social network with or without the context of the message.

Referring to an exemplary system for implementing the described systems is shown includes a data processing system suitable for storing and or executing program code including at least one processor coupled directly or indirectly to memory elements through a bus system . The memory elements can include local memory employed during actual execution of the program code bulk storage and cache memories which provide temporary storage of at least some program code in order to reduce the number of times code must be retrieved from bulk storage during execution.

The memory elements may include system memory in the form of read only memory ROM and random access memory RAM . A basic input output system BIOS may be stored in ROM . System software may be stored in RAM including operating system software . Software applications may also be stored in RAM .

The system may also include a primary storage means such as a magnetic hard disk drive and secondary storage means such as a magnetic disc drive and an optical disc drive. The drives and their associated computer readable media provide non volatile storage of computer executable instructions data structures program modules and other data for the system . Software applications may be stored on the primary and secondary storage means as well as the system memory .

The computing system may operate in a networked environment using logical connections to one or more remote computers via a network adapter .

Input output devices can be coupled to the system either directly or through intervening I O controllers. A user may enter commands and information into the system through input devices such as a keyboard pointing device or other input devices for example microphone joy stick game pad satellite dish scanner or the like . Output devices may include speakers printers etc. A display device is also connected to system bus via an interface such as video adapter .

Referring to a flow diagram is shown as carried out by an email client application implementing the described social network highlighting of recipients in an email message.

An email message is opened in a window on the user s system. The window shows a single message or a preview of it that includes all recipients. The email application checks if social network highlighting is selected and optionally checks the number of recipients if the highlighting is dependent on the number. It is determined if highlighting is required. If it is not required the email message is displayed without social network highlighting.

If the highlighting is required the email application accesses the user s social network list for highlighting as it retrieved according to the description above and considering the corresponding parameters. The recipients of the message are compared to the social network list. The recipients of the message also in the user s social network list are highlighted and the message is displayed .

Optionally information can be obtained of highlighted recipients who have read the message and an additional form of highlighting applied to the recipients who have read the message.

Referring to flow diagrams show two embodiments of methods of obtaining the social network lists as accessed in step of .

In the flow diagram of contact lists are retrieved from user s sources for example the email address list instant messaging contacts list and social network service contact lists to which the user subscribes. The contact lists are combined using any required combination method for example a union of the list or an intersection of the lists. The overall user s social network list is obtained on which the highlighting is to be based and sent to the social network highlighting mechanism.

In the flow diagram of contact lists are retrieved for the user and aggregated by a system from various sources. The sources may be from a single organization such as organizational charts internal address lists etc. Alternatively the sources may be from publicly available sources. The sources may optionally be restricted . The contacts obtained for the user from the sources are evaluated by the strength of relationship to the user. The evaluation may be restricted by date . The evaluation may also be restricted to a context of the message. The overall user s social network list is obtained on which the highlighting is to be based and sent to the social network highlighting mechanism.

In one embodiment a social network aggregating service such as SONAR SOcial Networking ARchitecture is used. SONAR is an API and architecture for retrieving and sharing social network data in an organization and aggregating it across applications. SONAR extracts information on who s connected to whom with what strength and based on what evidence. SONAR is implemented as a service using a REST API and can be used by various clients. It is currently in use by a Lotus Sametime client SonarBuddies Lotus and Sametime are trade marks of International Business Corporation and the web client of an employee profile application.

SONAR adheres to privacy restrictions thus data extracted from emails and chats will be exposed only to their owner s . SONAR aggregates the data retrieved from its sources and extracts a weighted social network of a person and the artifacts connecting the people in that network. The weight factor expresses the strength of the connection between people. SONAR can also enable the extraction of a person s network according to a specific topic.

Referring to a graphical user interface is shown of an email client with the described functionality of highlighting social network recipients.

An email message has a header with a from field a to field and a cc field . The to and cc fields each have a selection button for selecting to highlight recipients who are on a user s social network list. The selection button may include an activation for example a right click of the button to open a preference page . Multiple recipients in the to and cc fields then include some recipients highlighted as belonging to the user s social network list. In addition a second form of highlighting shows the recipient belongs to the user s social network list and has read the email message .

The preference page includes one or more of the following user setting options. An option is provided to turn the highlighting on or off. A threshold option for the number of recipients above which the highlighting is activated. An option is provided to manually add or remove recipients from the social network list by the user. The option to manually add or remove recipients includes a browse button to select recipients to add or remove.

In addition the preference page may include social network source selection option . The social network sources may be selected from user sources or external sources and a browse button is provided to select sources. A combination type option for the combination of social network sources is provided with options of different types of combination.

For weighted social network systems a relative strength threshold option is provided. A time range option to include in source selection is also provided.

Finally a read notification option may be selected by a user to activate a second form of highlighting to highlight recipients on the user s social network list that have read the email message .

The described features are added to existing email applications which adapts email to Web 2.0 where social network information is ubiquitous. The system highlights people from within the user s network over email messages.

Many user s address books provide fairly sparse information whereas social network sites are becoming more and more popular providing social network information for a user. The described method and system tap into external social network information to enrich the user s social network based on which highlighting in an email message takes place.

A social network highlighting system for email applications may be provided as a service to a customer over a network.

The invention can take the form of an entirely hardware embodiment or an embodiment containing both hardware and software elements. In a preferred embodiment the invention is implemented in software which includes but is not limited to firmware resident software microcode etc.

The invention can take the form of a computer program product accessible from a computer usable or computer readable medium providing program code for use by or in connection with a computer or any instruction execution system. For the purposes of this description a computer usable or computer readable medium can be any apparatus that can contain store communicate propagate or transport the program for use by or in connection with the instruction execution system apparatus or device.

The medium can be an electronic magnetic optical electromagnetic infrared or semiconductor system or apparatus or device or a propagation medium. Examples of a computer readable medium include a semiconductor or solid state memory magnetic tape a removable computer diskette a random access memory RAM a read only memory ROM a rigid magnetic disk and an optical disk. Current examples of optical disks include compact disk read only memory CD ROM compact disk read write CD R W and DVD.

Improvements and modifications can be made to the foregoing without departing from the scope of the present invention.

