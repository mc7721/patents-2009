---

title: Method and equipment for improving communication confidentiality
abstract: The present invention relates to a method for improving communication confidentiality including the following steps:


url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08380717&OS=08380717&RS=08380717
owner: Alcatel Lucent
number: 08380717
owner_city: Paris
owner_country: FR
publication_date: 20090325
---
The present invention relates to the field of telecommunication networks and more specifically of communication confidentiality and communications in confidential environment.

For a company keeping information confidential is crucial for economic security or political reasons and is often a key point of the strategy of a company or a department. Working in confidential environments research laboratories defence departments financial companies implies the use of specific equipments and the respect of specific rules in order to ensure the safety of confidential information or data. Thus great efforts are made to secure the communication means and prevent spies or hackers from trespassing into confidential network areas or listening to confidential calls. Nevertheless leakage of confidential information often occurred because of a lack of care in the internal exchanges. Indeed it is not always easy for the different collaborators to be aware of the subjects that are authorized or prohibited to their interlocutors or to know the confidential status of some information.

It is therefore an object of the present invention to overcome the precited drawbacks of the state of the art and provide a method for improving communication confidentiality.

storing in a data repository data about authorized and non authorized confidential subjects for users of a telecommunication network 

receiving a request with identity information of a first and a second users from a user telecommunication device of said first user 

comparing data about authorized and non authorized confidential subjects for said first and second users in said data repository 

selecting a second type of data about confidential subjects authorized to said first user and non authorized to said second user 

sending selected data about confidential subjects of said first and second type to said first user telecommunication device.

selecting a third type of data about confidential subjects non authorized to said first user and authorized to said second user 

sending selected subject data about confidential subjects of said first and third type to a telecommunication device of said second user.

It is also provided a method for improving communication confidentiality including the following steps 

sending a request with identity information of a first and a second users from a user telecommunication device of said first user 

receiving data about confidential subjects authorized to said first user and non authorized to said second user 

displaying data about confidential subjects authorized to both users and data about confidential subjects authorized to said first user and non authorized to said second user.

Said method furthermore comprises one or several of the following features as stand alone or in combination 

scrutinizing within a detection area of said first user telecommunication device the presence of a second user telecommunication device before sending a request 

the communication comprises a voice communication and the step of sending said request is initiated when a call is launched from said first user telecommunication device to a second user telecommunication device 

the communication comprises sending an email and the step of sending said request is initiated when the destination address section of said first user telecommunication device is filled in with an address of said second user 

the communication comprises instant messaging and the step of sending said request is initiated when a communication exchange is launched by said first user 

the communication comprises conferencing system and the step of sending said request is initiated when a conference is launched by said first user.

The invention also relates to a confidentiality server comprising at least one processing means being adapted to perform 

storing in a data repository data about authorized and non authorized confidential subjects for users of a telecommunication network 

receiving a request with identity information of a first and a second users from a user telecommunication device of said first user 

comparing data about authorized and non authorized confidential subjects for said first and second users in said data repository 

selecting a second type of data about confidential subjects authorized to said first user and non authorized to said second user 

sending selected data about confidential subjects of said first and second type to said first user telecommunication device.

In addition said at least one processing means of said confidentiality server are preferably able to perform 

selecting a third type of data about confidential subjects non authorized to said first user and authorized to said second user 

sending selected subject data about confidential subjects of said first and third type to a telecommunication device of said second user .

The invention relates furthermore to a user telecommunication device comprising at least one processing means being adapted to perform 

sending a request with identity information of a first and a second users from a user telecommunication device of said first user 

receiving data about confidential subjects authorized to said first user and non authorized to said second user 

displaying data about confidential subjects authorized to both users and data about confidential subjects authorized to said first user and non authorized to said second user.

Said user telecommunication device might include the feature wherein said at least one means are able to scrutinize within a detection area of said first user telecommunication device the presence of a second user telecommunication device before sending a request.

As used herein the term server refers to a part of a telecommunication network. It may be provided through the use of dedicated hardware as well as hardware capable of executing software in association with appropriate software. It can be a single dedicated processor a single shared processor or a plurality of individual processors some of which may be shared. Moreover explicit use of the term processor should not be construed to refer exclusively to hardware capable of executing software and may implicitly include without limitation digital signal processor DSP hardware network processor application specific integrated circuit ASIC field programmable gate array FPGA read only memory ROM for storing software random access memory RAM and non volatile storage. Other hardware conventional and or custom may also be included.

As used herein the term confidential subjects refers to topics subjects or projects being known and accessible only to a limited number of persons and needing to remain so for strategic reasons.

In the following description reference numbers below 100 refer to devices apparatus equipments or parts of them whereas reference numbers above 100 refer to the steps of a method.

The present invention offers to improve communication confidentiality by informing users of a telecommunication network of the confidential subjects prohibited to their interlocutors. It refers to the use of a confidentiality server comprising a data repository with the registered users and their authorization status with respect to a list of confidential subjects.

A possible organization of the present invention is schematically represented on . It shows a telecommunication network comprising a first user telecommunication device belonging to a first user a second user telecommunication device belonging to a second user and a confidentiality server .

Said telecommunication network can be of any type with fixed and or mobile telecommunication and set up with any technology radio based technology optical technology Voice over IP etc . Preferentially the telecommunication network is a network internal to a company that can be connected to other external networks. Access to the data contained in said confidentiality server is limited to authorized persons of the administration .

Said user telecommunication devices and can be of any type among the following list but not limited to a cell phone a fixed telephone a computer a personal data assistant PDA etc.

To better understand the present invention the different steps of the offered method are represented on with respect to the devices in the telecommunication network and in in form of a flowchart. The first step refers to the storage of a data repository defining for each registered user of said telecommunication network an authorization status with respect to different confidential subjects. Said data repository contains data about authorized and non authorized confidential subjects for users of the telecommunication network and can be organized in a matrix or a table form. It can be also organized in a database.

Thus said data repository defines the compatibility between users and authorized and non authorized confidential subjects. Any user of said telecommunication network can therefore be registered.

In practice the registration and the modifications in said data repository are achieved by authorized people through secured managing applications. In the present example the users associated with the first and second user telecommunication devices and have been registered in the data repository of the confidentiality server . The first user telecommunication device is Mister Smith s device whereas the second user telecommunication device is Miss Wayne s device.

Thus when Mister Smith initiates in step a communication exchange with Miss Wayne by using his telecommunication device a request for retrieving confidential information concerning Miss Wayne is automatically sent in step to the confidentiality server . When receiving said request the confidentiality server starts in step by determining the identity of the user having sent the request Mister Smith in the present example and the identity of its interlocutor Miss Wayne as well. This identification can be done thanks to the data included in the request.

Then the compatibility between both users concerning confidential subjects needs to be determined. This is achieved by comparing in step the information associated with both users in the data repository of the confidentiality server . From this comparison data about subjects authorized to both users are selected in step and the data about subjects authorized to only one of them are selected in step and . Then the data about subjects authorized to Mister Smith and authorized or not to Miss Wayne are sent back to Mister Smith s telecommunication device in step . The data received by Mister Smith s are then displayed on his telecommunication device in step to inform him of the confidential subjects authorized to Miss Wayne and those non authorized to Miss Wayne and therefore prohibited.

Besides said confidentiality server may provide secured application programming interfaces API in order to interact with any network equipment dealing with confidentiality for example a communication server such as a presence server an email client system or a conferencing system.

Thus the present invention allows reminding users of the telecommunication network of the confidential subjects authorized to their interlocutors and the subjects prohibited during their communication exchange.

The present invention can be applied to different types of communication as presented in the following part of the description.

In a first embodiment the present invention is associated with a voice based communication network for example a private automatic branch exchange PABX to connect user telecommunication devices such as phones personal digital assistants PDA or computers. In such configuration the communication between said user telecommunication devices and the confidentiality server can be direct or through a presence server managing the different communications.

In a second embodiment communication exchanges are made thanks to an instant messaging application wherein a presence server determines the presence status of the users and organizes the communication exchanges. In this case the request to the confidentiality server is made through the presence server when a first user initiates a discussion with a second user. Confidentiality information is then displayed for example when said first user plots or clicks on the avatar of said second user.

In a third embodiment a communication exchange is realized by a conferencing system. In the same way as previously for the instant messaging case the request is made through a presence server when the conference is initiated and the results of the request are displayed on the respective user conference system devices computers TVs . . . .

In a fourth embodiment communication exchanges are made by email. As the information about the confidential status of the recipient needs to be displayed before sending the message the request is made as soon as the section comprising the recipient address is filled in. The confidentiality information is then displayed for example either automatically in a new window or by clicking or plotting on the recipient address with a cursor.

In a fifth embodiment user telecommunication devices are equipped with detectors to scrutinize the surrounding environment in order to detect the presence of another similar device in the neighborhood. Said detectors comprise for example a radio wave communication protocol system. With this type of devices radio waves are continuously sent out by said device to search for the presence of other users. Therefore when another device is detected a request is sent to the confidentiality server to know the status of the detected user with respect to confidential subjects and the data about authorized and non authorized confidential subjects are displayed on said user telecommunication device. The advantage is that a user may adapt his behaviour in presence of other users and might need to switch subject of discussion with a second authorized user if a third non authorized user is approaching. A warning system can also be set up in order to inform users of the presence in their neighbourhood of persons non authorized to confidential subjects.

It has also to be noted that the present invention can be adapted in the case of a communication exchange with several interlocutors or the detection of several user telecommunication devices in the surroundings. The non authorized subjects are then the union of the subjects non authorized to each of the interlocutors in order to prevent from leakage to any of them.

Thus the present invention offers a solution to reinforce confidentiality in the communication exchanges occurring inside a communication network of a company or a department by informing the users of said communication network of the confidential subjects needing to remain undisclosed during said communication exchanges

