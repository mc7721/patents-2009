---

title: Information processing apparatus, data processing method and program
abstract: A configuration is achieved in which content copying between media and content downloading are performed effectively and under strict management. In content copying between media, the identification information (medium ID) of a copying destination medium is obtained using an API for providing a predefined processing, then the obtained medium ID is transmitted to a server to obtain copying permission information from the server, and then content copying is performed under the management of the server. This configuration allows a copying destination medium to be managed, which can eliminate the unauthorized use of the content. Also, the configuration in which content downloading from the server is performed according to, for example, a Java® program allows a ROM disc on which the content is recorded to store the program and to be provided to a user.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08914904&OS=08914904&RS=08914904
owner: Sony Corporation
number: 08914904
owner_city: Tokyo
owner_country: JP
publication_date: 20090812
---
This application is a National Stage under 35 U.S.C. 371 of PCT international application PCT JP2009 064239 entitled INFORMATION PROCESSING DEVICE METHOD FOR PROCESSING DATA AND PROGRAM filed on Aug. 12 2009 which claims priority to Japanese Application Serial No. 2008 212485 filed on Aug. 21 2008 each of which is hereby incorporated by reference in its entirety.

The present invention relates to an information processing apparatus a data processing method and a program. More particularly the present invention relates to an information processing apparatus a data processing method and a program for performing content recording and copying to a recording medium.

A DVD Digital Versatile Disc a Blu ray Disc and the like are commonly used as a medium for recording various contents including music movie and the like. These information recording media include a ROM type medium on which data is already recorded and additional data cannot be written and an R type RE type and the like on which data can be written. A data writable information recording medium enables a content recorded on another medium to be copied or moved. Also the data writable information recording medium enables a content to be downloaded for recording for example from a network or using an apparatus installed in a public place.

The content recording media also include a hard disk and a flash memory as well as the above described DVD and Blu ray Disc .

The aspects of the process for recording a content on a recording medium may include the following for example 

 a copying or moving from a medium e.g. ROM disc on which a content is already recorded to another medium 

However many of contents such as music data and image data are under copyrights distribution rights or the like owned by their authors or distributors. Therefore when a content is provided to a user a certain limitation is generally imposed on the use of the content such that the user may use the content only when the user is given an authorized right to use the content and unauthorized duplication and the like are not allowed.

For example one known standard for content usage control is AACS Advanced Access Content System . According to AACS standard performing content copying between media mentioned in a above requires obtaining copying permission information from a management server. Thus the copying is permitted only under predetermined management. This copying processing is referred to as Managed Copy MC .

The content providing scheme mentioned in b above content providing by downloading is referred to as EST Electric Sell Through . The content providing by a shared terminal mentioned in c above is referred to as MoD Manufacturing on Demand . According to AACS standard these processings also need to be performed according to a predetermined rule.

Managed Copy MC is a processing in which for example as shown in a of a user sets an information recording medium disc on which a content is already recorded in an information processing apparatus for data recording reproducing then the content read from the information recording medium disc is copied to a second information recording medium such as an R RE type data writable disc hard disk and flash memory.

In order to perform this content copying the data recording reproducing apparatus needs to connect with a management server via a network to obtain content copying permission from the management server .

Although shows a configuration in which one information processing apparatus a single apparatus performs content copying between media another configuration may be used in which one apparatus for loading a medium as copying source and another apparatus for loading a medium as copying destination are connected by for example a USB cable.

The processing of downloading a content from a server and recording the content to an information recording medium is referred to as EST Electric Sell Through . EST is a processing in which as shown in b of a user sets a medium for example R or RE type disc data writable medium owned by the user in an information processing apparatus of a PC or the like owned by the user then a content is received from a content server EST server via a network and recorded.

The content providing by a shared terminal is referred to as MoD Manufacturing on Demand . As shown in c of in Mod a user uses a content server as a terminal installed in for example a convenience store or a public place such as station to purchase a content by recording the content to a medium. More specifically Mod is a processing in which a data writable medium owned by the user for example R or RE type disc is set in the content server Mod server as the terminal installed in a convenience store and a desired content is recorded to the disc through an operation such as content selection by the user .

In this way the user can record a content to a data recordable medium and use for example reproduce the recorded content. However when the content is for example a copyright protected content or the like usage control needs to be performed in order to prevent illegal use.

As described above one known standard for content copyright protection technology is AACS Advanced Access Content System . AACS standard configures usage control in which a usage control information Usage Rule defined for each content and a content is used according to the usage control information Usage Rule . Furthermore AACS standard provides strict usage control in which a content is configured to be an encrypted content by dividing the content into units defining a unit key for each unit and allowing only a specified user to obtain the unit keys.

When a disc on which a content is recorded is a medium allowing only reproducing and not allowing recording of new data such as ROM type disc additional recording of a new content or editing will not be performed on the medium. Thus the content specific usage control information Usage Rule for each content recorded on the medium and the unit keys can be recorded together to the medium and provided to the user.

On the other hand when a content is recorded on a medium such as R or RE type data writable disc hard disk and flash memory the content recorded on the medium is not fixed and updating such as recording of a new content or deleting of a recorded content can be performed. So usage control information and unit keys also need to be updated according to the update of the content stored in the medium.

Thus when recording a content to a medium the user needs to perform complicated operations such as recording various ancillary data for each recorded content as well as recording the content. So for example in performing Managed Copy MC described above a program in which a series of processing sequences is defined in advance is generally used to perform copying.

For example many of information processing apparatuses conforming to AACS standard store a program a player application for performing Managed Copy MC described above. When using such an AACS certified apparatus to perform Managed Copy MC the user runs the player application stored in the apparatus. When the program is run a series of processings including connecting with a management server and obtaining copying permission information from the management server is performed then copying is performed with the copying permission information obtained.

Even when a content recorded on a Blu ray Disc is copied to another medium Managed Copy MC is performed using the player application stored in the AACS certified apparatus.

 b starting BD J Blu ray Disc Java application which is a Java application program stored on a disc on which a content is recorded then starting the player application through a BD J application.

The player application is a program stored in an apparatus that performs content reproducing recording and designed to be commonly used for various contents. On the other hand the BD J application can be recorded on a disc and can also be configured specific to each content recorded on the disc. In other words the BD J application is a program that a content author can design according to the content recorded on the disc.

Thus the BD J application is a program that can be designed with some freedom by the content author and can be variously configured according to various configuration of the content. So if the BD J application is configured to perform Managed Copy MC the content author can also design the BD J application to perform processing unique to each content according to the content configuration or the like.

However in Managed Copy MC when the copying destination medium of a content is for example a freely portable medium such as R RE type data writable disc inadequate management of the copying destination medium may allow unauthorized use of the content.

In view of the above for example it is an object of the present invention to provide an information processing apparatus a data processing method and a program in which in performing content copying between media managed by a server a copying destination medium for a content can be reliably managed to protect the content from unauthorized use.

For example it is an object of the present invention to provide an information processing apparatus a data processing method and a program in which the identification information medium ID of a copying destination medium e.g. an R RE type disc is obtained using an API Application Programming Interface for providing a predefined processing then the medium ID is transmitted to a server to obtain copying permission information from the server and then content copying is performed under the management of the server.

It is another object of the present invention to provide an information processing apparatus a data processing method and a program in which content downloading from a server is performed according to a program defining processing sequences for example a Java program.

an information processing apparatus including a data processor for reading data from a medium and communicating with a server 

medium ID reading processing of reading the medium ID of a second medium to which a content recorded on a first medium is to be copied 

wherein the medium ID reading processing is performed using an API Application Programming Interface defining the medium ID reading processing.

Furthermore according to an embodiment of the information processing apparatus of the invention the data processor executes a Java application program on a virtual machine as a virtual hardware environment for program execution.

Furthermore according to an embodiment of the information processing apparatus of the invention with the copying permission information obtained the data processor copies the content recorded on the first medium to the second medium.

Furthermore according to an embodiment of the information processing apparatus of the invention the data processor provides the copying permission information to a second data processor for performing content copying and the second data processor performs content copying with the copying permission information obtained.

an information processing apparatus including a data processor for reading data from a medium and communicating with a server 

receives a list of contents obtainable from the server corresponding to contents stored in the medium 

Furthermore according to an embodiment of the information processing apparatus of the invention the program is a Java application program and the data processor executes the Java application program on a virtual machine as a virtual hardware environment for program execution.

Furthermore according to an embodiment of the information processing apparatus of the invention the data processor when performing content recording to the medium records a downloaded content from the server and a copied content from another medium in different directories.

medium ID reading step of reading the medium ID of a second medium to which a content recorded on a first medium is to be copied 

wherein the medium ID reading processing is performed using an API Application Programming Interface defining the medium ID reading processing.

 a obtaining from the server a list of contents obtainable from the server corresponding to contents stored in the medium 

medium ID reading step of reading the medium ID of a second medium to which a content recorded on a first medium is to be copied 

wherein the medium ID reading step is defined to be performed using an API Application Programming Interface defining the medium ID reading.

a program for causing an information processing apparatus to perform data processing including the steps of 

obtaining from the server a list of contents obtainable from the server corresponding to contents stored in the medium 

Note that the program in accordance with the invention is for example a computer program that can be provided in a computer readable form from a recording medium or communication medium to a general purpose computer system that can execute various program codes. Providing such a program in the computer readable form allows the computer system to perform processing according to the program.

Still another purpose feature and advantage of the invention will be apparent from the following more detailed description based on the embodiments of the invention and accompanying drawings. Note that as used herein system refers to a logical group configuration including multiple devices that is not limited to a configuration in which the components are within the same enclosure.

According to one embodiment of the invention in content copying between media the identification information medium ID of a copying destination medium e.g. an R RE type disc is obtained using an API Application Programming Interface for providing a predefined processing then the obtained medium ID is transmitted to a server to obtain copying permission information from the server. With this copying permission information obtained content copying is performed. This configuration allows a copying destination medium to be managed which can eliminate the unauthorized use of the content. Also content downloading from the server is performed according to for example a Java program. This configuration allows a ROM disc on which the content is recorded to store the program and to be provided to a user.

An information processing apparatus a data processing method and a program in accordance with the invention is described in detail below with reference to the drawings.

First a processing example of Managed Copy MC performed by the information processing apparatus in accordance with the invention is described with reference to . As described above Managed Copy MC is a processing of copying a content to another medium with copying permission information obtained from a management server.

The data recordable second recording medium as content copying destination is for example a recording medium such as hard disk R RE disc and flash memory.

The information processing apparatus includes for example a PC a recording reproducing device and the like and can read data from the disc and record the read data to the second information recording medium .

The BD J application is a program to be executed by the information processing apparatus when content copying Managed Copy MC is performed and for example a program for performing processing such as communicating with the management server . Note that the BD J application may be configured as a single application program or may be configured as a combination of two or more BD J applications each performing a specific processing.

For example they are a BD J application for communicating with the server a BD J application dedicated to billing and the like. When performing content copying these BD J applications are executed by the information processing apparatus .

The copying management file MCMF is a file to be used when content copying is performed and for example a data file written in XML including the following information 

 a a content ID that is an identifier ID for uniquely identifying the content recorded on the information recording medium disc 

 b a URI URL that is information for connecting with the management server for providing copying permission generating a token by binding or performing another processing when content copying is performed for example information for accessing the management server and

 c a directory name file name that is information on names of a directory and a file storing data for permitting copying.

The management data is for example management data defined by AACS Advanced Access Content System that is a standards management system for content copyright protection technology and data including a CPS unit key file storing keys unit keys to be used to decrypt the encrypted content usage control information a content certificate CC for showing the validity of the content an MIKE Media Key Block that is an encryption key block storing key information Media Key for obtaining the CPS unit keys and the like.

The encrypted content is for example an encrypted content conforming to AACS standard. For example the encrypted content is an AV Audio Visual stream of moving image content such as an HD High Definition movie content that is high definition moving image data or a content including music data a game program an image file sound data text data and the like.

The encrypted content is for example an encrypted content having a configuration in which usage management for each content management unit CPS unit is possible and to which the unit keys CPS unit keys differing for each content management unit CPS unit are applied. The encrypted content is encrypted with the keys CPS unit keys differing for each unit allocated and is stored.

A first data processor is a BD JVM BD J Virtual Machine . The BD JVM BD J Virtual Machine is configured to be a virtual machine as a virtual hardware environment in which the BD J application recorded on the disc is executed.

A second data processor is an AACS layer . The AACS layer is configured to be a data processor for performing data processing according to AACS standard including the handling of highly secured information such as obtaining an ID recorded on the disc and the data transformation in content copying.

Thus when a content recorded on the disc is to be copied to another medium the BD JVM BD J Virtual Machine as an execution domain for the BD J application recorded on the disc and the AACS layer that is a program execution domain for performing processing according to AACS standard are configured and passing a processing request and a processing result and the like are performed between them.

An API Application Programming Interface is used for such passing a processing request and a processing result and the like between the BD J application and the AACS layer. The API is a group of functions and the like for executing various processings necessary for content copying. The API is stored in the BD J application or another area that can be read by the information processing apparatus . A specific example of the API is described in detail later.

The information processing apparatus executes the BD J application in the BD JVM to communicate with the management server and perform processing such as obtaining copying permission information .

In order to copy the content stored on the disc to the second information recording medium processing such as transforming the content and usage control information Usage Rule to adapt to a destination medium is required. These processings are executed in the program execution domain AACS layer for performing processing according to AACS standard.

The BD J application is a program for performing processing necessary for content copying and is executed in the BD JVM of the information processing apparatus . For example the following processings are performed using the BD J application 

 e obtaining and checking copying permission information from the server and providing the copying permission information to a recording controller 

 g monitoring the process of writing data downloaded from the server performed by the recording controller.

Note that as described above the BD J application may be configured as a single application program or may be configured as a combination of two or more BD J applications each performing a specific processing. For example the above described processings a to g may be performed by two or more BD J applications.

Processing using the BD J application is described with reference to . In step S shown in the BD J application is started in the BD JVM BD J Virtual Machine configured in the information processing apparatus .

Note that when this processing is performed a guide screen as user interface such as a menu offered by the BD J application is displayed on a display of the information processing apparatus . According to an instruction from the user a series of processings for performing content copying Managed Copy is started.

Based on the user instruction the BD J application first uses the server URI included in the copying management file MCMF to access the management server . At this point the content ID corresponding to the content to be copied is transmitted to the management server .

In step S based on the content ID received from the information processing apparatus the management server generates an allowed processing list listing processings allowed for the content and transmits the list to the information processing apparatus . For example the list includes information on whether content copying is allowed or not copying fee and the like.

The information processing apparatus receives an allowed processing list from the management server and in step S displays the allowed processing list on the display from which the user selects processing to be performed.

When the user selects the processing to be performed the information processing apparatus performs payment processing with the management server by transferring payment data . For example the user enters and transmits data necessary for payment such as a credit card number on a payment screen. Next in step S the management server permits the processing to transmit copying permission information to the information processing apparatus .

The information processing apparatus receives copying permission information from the management server and provides the copying permission information to the AACS layer . In the AACS layer the processings in step S and later are performed. The AACS layer transforms the management data read from the disc to management data adapted to the medium type of the second recording medium the copying destination such as hard disk R RE disc and flash memory. For example the AACS layer adds encryption keys unit keys for the content to be copied and transforms the usage control information the content certificate and the like to data for the content to be copied. Information necessary for these data transformations is included in the copying permission information . The transformed management data will be recorded to the second recording medium .

Furthermore in step S the information processing apparatus loads the encrypted content recorded on the disc and outputs copied content data on which data transformation such as format transformation is performed. In this way the copied data of the content recorded on the disc will be recorded to the second recording medium as encrypted content . Note that the management data to be recorded to the second recording medium includes usage control information a content certificate an MKB a CPS unit key file a token and the like for the content to be recorded to the second recording medium .

Note that in content copying between the information processing apparatus and the management server for example a token may be generated and included as management data by checking the medium identifier serial number of the second recording medium and signing with the secret key of the management server with respect to the medium identifier. In the management data including this token and the like is shown as management data in the management server . These token information may be included in the management data CP data to be recorded to the second recording medium .

Thus the overview of content copying has been described with reference to . As described above content copying is performed using the BD J application and the program executed in the AACS layer. So passing necessary information between the BD J application and the execution program in the AACS layer is required. In order to achieve this the API in which various processings are defined is used.

Next processing examples using a server performed by an information processing apparatus in accordance with the invention are described with reference to . shows the following two processings 

An information processing apparatus user apparatus downloads a content A from a server and stores the content A in a local storage and

The information processing apparatus copies the content A stored in the local storage to a data recordable R RE type disc.

Processing Example 1 represents content downloading corresponding to EST Electric Sell Through already described with reference to b of .

Processing Example 2 represents processing corresponding to Managed Copy MC already described with reference to of obtaining copying permission information from the server and performing content copying between media.

First the information processing apparatus loads a ROM disc on which a content such as a movie is recorded. Next a data processor executes a program recorded on the ROM disc to download the content A from the server . For example when the ROM disc is a Blu ray Disc the program is a BD J application program that is a Java program conforming to BD standard.

Next the data processor transmits a content downloading request to the server according to the program . In response to the request the server provides the content A to the information processing apparatus . The data processor of the information processing apparatus stores the content A downloaded from the server to the local storage including e.g. a hard disk or the like in the apparatus .

Note that the following processing may also be performed in conjunction with downloading the content from the server the information processing apparatus transmits the ID of the information processing apparatus device binding ID and a random number binding nonce to the server and in response to these data the server signs with the server secret key and generates server authentication information token to be provided to the information processing apparatus .

In order to use the downloaded content in the information processing apparatus the server authentication information token is checked to verify that the valid server authentication information token is obtained. Only if it is verified decrypting and reproducing the downloaded content is permitted. This configuration permits only a specified device information processing apparatus to use the downloaded content.

Note that the local storage stores various contents including the content obtained by downloading from the server as described above and the content copied from the ROM disc as already described with reference to that is the content copied by Managed Copy MC performed under the server management with the copying permission information obtained from the server.

In the directories and the copied content and the downloaded content are organized by title and stored respectively. When these contents are to be further copied to another medium such an organization by title enables the contents to be selected and copied in a group. That is these contents and management data stored in the local storage may be further copied to another medium e.g. R RE type disc. For example Processing Example 2 shown in applies to this case.

Processing Example 2 shown in is described. This processing further copies the content A stored in the local storage to another medium that is an R RE type disc shown. The content A is a content copied from the ROM disc or downloaded from the server and subject to usage control. So copying the content A requires copying permission information obtained from the server .

The program for performing the series of copying processing is for example a program stored in the local storage e.g. a BD J application . This program for copying is for example the program used in Processing Example 1 which was obtained from the ROM disc or the server and stored in the local storage .

Note that a program is different from the program recorded on the ROM disc shown in . The program is for content downloading and the program is for content copying. The ROM disc may have these different programs recorded thereon.

The R RE type disc is an R type or RE type disc to which data can be recorded by a user. The R RE type disc has the medium ID as disc specific identifier recorded thereon. When copying requiring copying permission information obtained from the server that is Managed Copy MC is to be performed the medium ID recorded on the R RE type disc is transmitted to the server to request the copying permission information.

The data processor of the information processing apparatus reads the program BD J from the local storage and executes it. The data processor performs the following series of processings according to the program reading the medium ID recorded on the R RE type disc transmitting the medium ID to the server and obtaining the copying permission information from the server . After these processings the content A stored in the local storage is copied to the R RE type disc .

The information processing apparatus performs the series of processings shown in by executing the program the BD J application program shown in stored in the ROM disc the ROM disc shown in in the data processor. The BD J application program is a Java application program. The data processor of the information processing apparatus executes the Java application program on a virtual machine as a virtual hardware environment for program execution.

When the data processor of the information processing apparatus starts the program BD J application program a user interface for allowing the user to input an instruction is displayed on the display. The user inputs an instruction such as a request to the information processing apparatus through the user interface displayed on the display or through another input means.

First in step S the user requests a list of downloadable contents from the information processing apparatus user apparatus . This is the list of contents that can be obtained corresponding to the contents stored in the ROM disc loaded in the information processing apparatus . More specifically this is the list of contents also referred to as subsequent data or trailer allowed to be downloaded from the server corresponding to the contents stored in the ROM disc.

step S in response to the user request the information processing apparatus requests the list of downloadable contents from the server . In step S the server transmits the list to the information processing apparatus .

The information processing apparatus displays the list received from the server on the display and in step S detects the input of selection information from the user based on the list. That is the user inputs selection information of a content to be downloaded. In step S the information processing apparatus transmits the downloaded content selection information to the server to request the content to be downloaded.

In step S the server provides the content to the information processing apparatus . In step S the information processing apparatus stores the content downloaded from the server in the local storage including e.g. a hard disk.

In this storing process as already described with reference to the data processor of the information processing apparatus stores the downloaded content from the server and the copied content from another medium in different directories.

Next the detailed sequence of the content copying described with reference to Processing Example 2 in is described with reference to a sequence diagram shown in . This is the sequence of copying a content stored in the local storage to another medium such as an R RE type disc.

The data processor of the information processing apparatus user apparatus executes the program the BD J application program shown in stored in the local storage such as a hard disk the local storage shown in . The series of processings shown in is performed by this program execution. The ED J application program is a Java application program. The data processor of the information processing apparatus executes the Java application program on a virtual machine as a virtual hardware environment for program execution.

When the user inputs an instruction such as a request for copying to the information processing apparatus through the user interface displayed on the display or through another input means the data processor of the information processing apparatus user apparatus starts the program BD J application program .

First in step S the user requests the information processing apparatus user apparatus to copy a content stored in the local storage. Specifically the user inputs an instruction to start copying a content stored in the local storage of the information processing apparatus to another medium.

In response to the user request the information processing apparatus instructs the user to set a content copying destination medium in the apparatus. In step S the user sets the copying destination medium in this example R RE type disc . Then in step S the information processing apparatus reads the identifier of the set R RE type disc medium ID .

For example an API Application Programming Interface defined in the program BD J application program is used to read the medium ID. The API is a program unit defined by functions and the like for performing a predefined processing.

The API to be used here is an API Get Media ID that defines the reading of the medium ID of an R RE type disc. The processing sequence performed by this API may be included within the program BD J application program or may be recorded in a library or the like in the memory of the information processing apparatus . Or it may be obtained from the server and recorded in the memory in advance. The information processing apparatus performs the sequence defined by the API Get Media ID to read the medium ID from the R RE type disc.

Next in step S the information processing apparatus transmits the medium ID read from the R RE type disc to the server to request copying permission information. In this process of requesting the copying permission information the information processing apparatus transmits information including the content ID that is the identification information of the content to be copied as well as the medium ID of the copying destination medium.

On receiving the copying permission information from the information processing apparatus the server verifies and registers the received data in step S then transmits the copying permission information to the information processing apparatus in step S. Note that the copying permission information generated by the server includes for example data referred to as token generated by signing with the secret key of the server with respect to the medium ID of the copying destination medium.

After receiving the copying permission information the information processing apparatus performs content copying between media in step S. Specifically the information processing apparatus copies the content stored in the local storage to the R RE type disc. In this copying the copying permission information received from the server is also recorded to the R RE type disc.

Note that content copying in step S may be performed by the program BD J application program used for obtaining the copying permission information or may be performed by another program recorded in the information processing apparatus. In order to achieve content copying data transformation and recording according to a specific format such as data transformation and management information recording according to the type of a recording destination medium is required. Then a program dedicated to these copying processings may be stored in the information processing apparatus in advance and the processings using this program may be performed in content copying.

Next with reference to a flowchart shown in the processing sequence for content copying is described with respect to the information processing apparatus. As described with reference to the information processing apparatus performs Managed Copy MC which is performed with the copying permission information obtained by using for example the program BD J application program stored in the local storage. Note that as already described the program BD J application program may be obtained from the ROM disc on which the content is recorded and then executed.

When the user inputs a request for copying in step S the program BD J application program is executed in step S and the medium ID of the copying destination medium R RE type disc is read in step S.

As described above the reading of the medium ID is performed using the API Get Media ID . In step S according to the program BD J application program the medium ID read from the copying destination medium R RE type disc flash memory HDD and the like is transmitted to the server to request the copying permission information.

In step S according to the program BD J application program the copying permission information is obtained downloaded from the server. Finally in step S according to the program BD J application program the content recorded in the local storage is recorded to the copying destination medium R RE type disc .

In this copying the copying permission information received from the server is also recorded to the R RE type disc. Note that as described above this content copying may be performed by a program different from the program used for obtaining the copying permission information BD J application program for example a program recorded in the memory of the information processing apparatus resident program .

Next with reference to the specific sequence of the content copying between media described with reference to and the data processing configuration of the information processing apparatus are described. As described with reference to content copying is performed by the program BD J application program stored in the local storage executed by the information processing apparatus.

The BD J application program is a Java program conforming to BD Blu ray Disc standard. In order to execute the BD J application program an information processing apparatus configures a BD JVM BD J Virtual Machine as shown in . The BD JVM BD J Virtual Machine is a virtual machine as a virtual hardware environment in which a BD J application that is a Java program stored in a local storage is executed.

The BD JVM BD J Virtual Machine serving as a first data processor executes the BD J application stored in the local storage to communicate with a server and obtain copying permission information from the server .

Content copying after obtaining the copying permission information may be performed in the BD JVM using the BD J application or may be performed using a dedicated program recorded in the memory of the information processing apparatus in advance. In the configuration shown in content copying is performed in an AACS layer as a second data processor. The AACS layer performs BD Blu ray Disc format transformation and recording according to the type of a content recording destination medium or the like.

The local storage includes for example a hard disk. The information processing apparatus includes for example a PC a recording reproducing device and the like. As shown in the local storage records the following data 

The BD J application is a program to be executed by the information processing apparatus when content copying Managed Copy MC is performed and for example a program for performing a series of processings for content copying such as communicating with the server . Note that the BD J application may be configured as a single application program or may be configured as a combination of two or more BD J applications each performing a specific processing.

For example they are a BD J application for communicating with the server a BD J application dedicated to obtaining the copying permission information and the like. When performing content copying these BD J applications are executed by the information processing apparatus .

The copying management file MCMF is a file to be used when content copying is performed and for example a data file written in XML including the following information 

 a a content ID that is an identifier ID for uniquely identifying the content recorded in the local storage 

 b a URI URL that is information for connecting with the server for providing copying permission generating a token by binding or performing another processing when content copying is performed for example information for accessing the server and

 c a directory name file name that is information on names of a directory and a file recording data for permitting copying.

The management data is for example management data defined by AACS Advanced Access Content System that is a standards management system for content copyright protection technology and data including a CPS unit key file storing keys unit keys to be used to decrypt the encrypted content usage control information a content certificate CC for showing the validity of the content an MKB Media Key Block that is an encryption key block storing key information Media Key for obtaining the CPS unit keys and the like.

The encrypted content is a content copied from the ROM disc or downloaded from the server. For example the encrypted content is an encrypted content subject to usage control conforming to AACS standard. For example the encrypted content is an AV Audio Visual stream of moving image content such as an HD High Definition movie content that is high definition moving image data or a content including music data a game program an image file sound data text data and the like.

The encrypted content is for example an encrypted content having a configuration in which usage management for each content management unit CPS unit is possible and to which the unit keys CPS unit keys differing for each content management unit CPS unit are applied. The encrypted content is encrypted with the keys CPS unit keys differing for each unit allocated and is stored.

The first data processor is the BD JVM BD J Virtual Machine . The BD JVM BD J Virtual Machine is configured to be a virtual machine as a virtual hardware environment in which the BD J application recorded in the local storage is executed.

The second data processor is the AACS layer . The AACS layer is configured to be a data processor for performing data processing according to AACS standard including the handling of highly secured information and the data transformation in content copying.

Thus when a content recorded in the local storage is to be copied to another medium the BD JVM BD J Virtual Machine as an execution domain for the BD J application stored in the local storage and the AACS layer that is a program execution domain for performing processing according to AACS standard are configured and passing a processing request and a processing result and the like are performed between them.

Note that an API Application Programming Interface is used for such passing a processing request and a processing result and the like between the BD J application and the ARCS layer. The API is a group of functions and the like for executing various processings necessary for content copying. The API is recorded in the BD J application or another area that can be read by the information processing apparatus .

The information processing apparatus executes the BD J application in the BD JVM to communicate with the server and perform processing such as obtaining copying permission information .

In order to copy the content stored in the local storage to an R RE type disc as the second recording medium processing such as transforming the content and usage control information Usage Rule to adapt to a destination medium is required. In this example these processings are configured to be executed in the program execution domain for performing processing according to AACS standard AACS layer . As already described these processings may also be performed using the BD J application .

The BD J application is a program for performing processing necessary for content copying and is executed in the BD JVM of the information processing apparatus . For example the following processings are performed using the BD J application 

 e obtaining and checking copying permission information from the server and providing the copying permission information to a recording controller 

 g monitoring the process of writing data downloaded from the server performed by the recording controller.

Note that as described above the BD J application may be configured as a single application program or may be configured as a combination of two or more BD J applications each performing a specific processing. For example the above described processings a to g may be performed by two or more BD J applications.

Processing using the BD J application is described with reference to . In step S shown in the BD J application is started in the BD JVM BD J Virtual Machine configured in the information processing apparatus .

Note that when this processing is performed a guide screen as user interface such as a menu offered by the BD J application is displayed on a display of the information processing apparatus . According to an instruction from the user a series of processings for performing content copying Managed Copy is started.

Based on the user instruction the BD J application first uses the server URI included in the copying management file MCMF to access the server . At this point the content ID corresponding to the content to be copied is transmitted to the server .

In step S based on the content ID received from the information processing apparatus the server generates an allowed processing list listing processings allowed for the content and transmits the list to the information processing apparatus . For example the list includes information on whether content copying is allowed or not copying fee and the like.

The information processing apparatus receives an allowed processing list from the server and in step S displays the allowed processing list on the display from which the user selects processing to be performed.

When the user selects the processing to be performed the BD JVM BD J Virtual Machine in step S reads the medium ID from the R RE type disc that is the copying destination medium and transmits a copying permission information request to the server .

As already described the API get Media ID that defines the reading of a medium ID is used to read the medium ID from the R RE type disc that is the copying destination medium.

The copying permission information request including the medium ID read by the API from the R RE type disc that is the copying destination medium is transmitted to the server . The copying permission information request includes the medium ID of the copying destination medium the content ID of the content to be copied and the like. Next in step S the server verifies the request and registers the information then transmits the copying permission information to the information processing apparatus .

With copying permission information obtained from the server the information processing apparatus starts to copy the content stored in the local storage to the R RE type disc the copying destination. This processing may be performed using the BD J application executed by the BD JVM BD J Virtual Machine or may be performed using a dedicated program.

In the configuration shown in content copying is performed by the AACS layer as the second data processor that executes the dedicated program. The BD JVM BD J Virtual Machine receives the copying permission information from the server and provides the copying permission information to the AACS layer .

On accepting the copying permission information the AACS layer performs the processings in step S and later. The ARCS layer transforms the management data read from the local storage to management data adapted to the medium type of for example the R RE type disc the copying destination. For example the AACS layer adds encryption keys unit keys for the content to be copied and transforms the usage control information the content certificate and the like to data for the content to be copied. Information necessary for these data transformations is included in the copying permission information . Transformed management data is recorded to the R RE type disc as copying destination medium.

Furthermore in step S the information processing apparatus loads the encrypted content recorded in the local storage and outputs copied content data on which data transformation such as format transformation is performed. In this way the copied data of the content recorded in the local storage is recorded as an encrypted content to the R RE type disc as copying destination medium. Note that the management data to be recorded to the R RE type disc as copying destination medium includes usage control information a content certificate an MKB a CPS unit key file copying permission information and the like for the content to be recorded to the R RE type disc .

Note that as described above the copying permission information generated by the server is for example data referred to as token generated by signing with the secret key of the server with respect to the medium ID of the copying destination medium. The information processing apparatus records this token to be included in the management data to be recorded to the R RE type disc .

Note that in the processing configuration shown in the two data processors the BD JVM BD J Virtual Machine for executing the BD J application and the ARCS layer are configured and perform their own processings. When processings need to be performed by the AACS layer the BD J application appropriately selects and uses two or more of prepared APIs to request the AACS layer to perform various processings. Note that the APIs may be recorded in the BD J application program or may be stored in an area that can be read by the BD J application for example may be recorded on the disc or stored in the memory of the information processing apparatus. Thus the BD J application can perform Managed Copy using APIs to request the AACS layer to perform required processings.

Data copied between media and data generated by the server and the like in performing content copying between media are described with reference to .

When the encrypted content recorded in the local storage is to be copied for use to the R RE type disc that is the copying destination medium all of the MKB as key information required to decrypt the encrypted content the CPS unit key file and the CPS unit usage control information file are required to be copied to the R RE type disc . An MKB a CPS unit key file a CPS unit usage control information file and an encrypted content on the R RE type disc shown in the drawing are copied from the local storage .

Furthermore copying permission information token needs to be obtained from the server and recorded. In order to obtain the copying permission information token the medium ID of the R RE type disc is transmitted to the server . In this example furthermore a binding nonce including random number data is transmitted along with a medium ID to the server . Note that the binding nonce may not necessarily be data recorded on the R RE type disc in advance but may use a random number generated by the information processing apparatus .

The server receives the binding nonce and the medium ID from the information processing apparatus and generates the copying permission information token signed with the secret key of the server with respect to these received data and then transmits the copying permission information token to the information processing apparatus . The information processing apparatus records the copying permission information token to the R RE type disc which is the copying permission information token shown in the drawing.

Note that the processing example shown in is just an example and another processing example is also possible. For example as shown in the MKB to be used to obtain the key for decrypting the encrypted content may be provided by the server . As shown in an MKB included in the server is transmitted to the information processing apparatus which records the MKB to the R RE type disc as the MKB shown in the drawing.

Thus the invention has been described in detail with reference to the specific embodiment. However it is apparent that modifications and substitution may be made on the embodiment by those skilled in the art without departing from the spirit and scope of the invention. In other words the invention has been disclosed in an exemplary manner and should not be construed as restrictive. In order to determine the scope of the invention the appended claims should be considered.

Also the series of processings described herein can be implemented using hardware or software or a combination thereof. In order to perform a processing implemented using software a program including the processing sequence may be installed and executed in the memory of a computer embedded in a dedicated hardware or may be installed and executed in a general purpose computer capable of performing various processings. For example the program can be recorded in a recording medium in advance. Then the program can be installed from the recording medium into the computer. Also the program can be received from a network such as a local area network LAN or Internet and installed into a recording medium such as hard disk in the computer.

Note that the various processings described herein may be performed in parallel or separately depending on the capability of the apparatus for performing the processings or depending on the necessity as well as being performed in the time series according to the description. Also as used herein system refers to a logical group configuration including multiple devices that is not limited to a configuration in which the components are within the same enclosure.

As described above according to one embodiment of the invention in content copying between media the identification information medium ID of a copying destination medium e.g. an R RE type disc is obtained using an API Application Programming Interface for providing a predefined processing then the obtained medium ID is transmitted to a server to obtain copying permission information from the server. With this copying permission information obtained content copying is performed. This configuration allows a copying destination medium to be managed which can eliminate the unauthorized use of the content. Also content downloading from the server is performed according to for example a Java program. This configuration allows a ROM disc on which the content is recorded to store the program and to be provided to a user.

