---

title: Information processing apparatus and secured printing system for preventing a data leakage
abstract: An information processing apparatus includes an application that encrypts document data using a public key of a spooler and stores the document data encrypted as a spool file. A printer driver decrypts the encrypted document data using a secret key of the spooler and performs rendering to generate print data. Subsequently, the application decrypts the print data using the public key of the printing apparatus. The printing apparatus decrypts the encrypted print data using the secret key of its own.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08390848&OS=08390848&RS=08390848
owner: Canon Kabushiki Kaisha
number: 08390848
owner_city: Tokyo
owner_country: JP
publication_date: 20090212
---
The present invention relates to a printing system and an information processing apparatus capable of performing secured printing. More specifically preventing document data encrypted by an application from leakage.

When a user generates a document by an application and prints the document by a printing apparatus it is essential to prevent the document from being browsed printed illegally by a third person. Such a printing technology is referred to as secured printing.

For example Adobe Acrobat that is an application for generating a Portable Document Format PDF file adopts a system in which document is encrypted and can be printed only when a password for permitting printing is presented. When such an application receives a printing instruction from a user the application requests the password from the user. Upon obtaining the password the application encrypts document by the application and passes the data to a spooler for printing.

Further a unit method is used in which when a printer driver in a printing system receives data via the application spooler the print driver encrypts and transmits the data provided with password information to a printer. Thus secret information can be prevented from leakage that may occur between the printer driver and the printer refer to Japanese Patent Application Laid Open No. 2002 342061 .

As another method a printer driver receives certificate information and document encrypted by an application. Subsequently the encrypted document provided with certificate information including a password is transmitted to a printer as print data and the printer performs print processing on the decrypted data refer to Japanese Patent Application Laid Open No. 2004 287824 .

However in an environment where an application is connected with a printing system via a network it is likely that secret information is leaked when the data is transmitted from the application to a spooler. In order to address this problem for example as described in Japanese Patent Application Laid Open No. 2004 287824 a unit method is discussed where the data that is encrypted by the application and provided with the certificate information is transmitted to the printing apparatus.

However this method cannot be employed in the printing performed by a host rendering printer that requires a host computer to perform rasterization processing. The host rendering printer requires decryption prior to rasterization so that the printer driver can perform rasterization. At this point a spooler could decrypt document data. However if the document data is decrypted before a spool file is generated the document data can be browsed by extracting the spool file in the printing system.

Supposing that in a printing system the document data is encrypted immediately before being transmitted from the spooler to the printer driver and a printer driver has a filter configuration. In this case it is likely that the document data is leaked when the decrypted data is transmitted to the printer driver.

An object of the present invention is directed to secured printing in which document data encrypted by an application is prevented from leakage via at least a spooler or a printer driver during print processing.

Further an object of the present invention is directed to secured printing in which the document data encrypted by the application is prevented from leakage via the processing by the spooler the printer driver and overall printing apparatus.

According to an aspect of the present invention a method for controlling an information processing apparatus that includes a storage unit configured to store a program that realizes a spooler for managing a print command based on a print instruction about document data via an application from a user and a program that realizes a printer driver which transmits print data for printing the document data to a printing apparatus the method includes obtaining a public key of the spooler from the spooler and encrypting the document data using the obtained public key of the spooler by the application upon receiving the print instruction about the document data from the user obtaining the encrypted document data via the application and temporarily storing the encrypted document data that is obtained by the printer driver obtaining a secret key of the spooler from the spooler and decrypting the encrypted document data using the obtained secret key of the spooler and generating print data based on the decrypted document data.

Further features and aspects of the present invention will become apparent from the following detailed description of exemplary embodiments with reference to the attached drawings.

Various exemplary embodiments features and aspects of the invention will be described in detail below with reference to the drawings.

In a central processing unit CPU performs programs such as an application and an operating system OS recorded in a read only memory ROM for a program in a ROM or loaded from a hard disk HD to a random access memory RAM . Processing illustrated by each flowchart can be realized by performing the program. The RAM functions as a primary memory and a working area of the CPU . A key board controller KBC controls a key input from a key board or a pointing device not illustrated .

A cathode ray tube CRT controller CRTC controls a display on a CRT display . A disk controller DKC controls data access to the HD and a floppy disk FD that record various data. A printer controller PRTC controls communication of signals between the information processing apparatus and the printing apparatus connected with each other. Various connection types such as a local area network LAN and a universal serial bus USB can be applied to a connecting line . A network controller NC is connected to the network to perform communication control for communicating with other devices connected to the network. The information processing apparatus may be configured to connect to other printing apparatuses and peripheral apparatuses via the network.

In the printing apparatus a CPU controls each block connected to a system bus according to a control program recorded in a ROM and an external memory . An image signal generated by the CPU is output to a printing unit printing engine via a printing unit interface I F as output information. Further the CPU can perform communication with the information processing apparatus via an input unit to notify information about the printing apparatus to the information processing apparatus.

A program ROM in the ROM records a control program of the CPU . A font ROM in the ROM records font data used to generate output information. A data ROM in the ROM records information used by the information processing apparatus when the printing apparatus does not include an external memory such as a hard disk.

A RAM functions as a main memory and a working area of the CPU and is configured so that a memory capacity can be expanded by an option RAM that can be connected to an expanded port not illustrated . Further the RAM is used as a region for expanding output information a region for storing environment data and a non volatile RAM NVRAM .

A memory controller MC controls the access of the external memory to the printing apparatus. The external memory is connected to the printing apparatus as an option and stores font data emulation program and form data. Further an operation switch includes a switch and a light emitting diode LED display for performing an operation.

A scanner unit I F performs compensation processing and edition on image data received from a scanner unit . The scanner unit inputs reflection light generated by exposing and scanning an image of a document to a charge coupled device CCD sensor to convert image information into electric signals.

Further the scanner unit converts the electric signals into brightness signals formed of each color of RGB and reads the brightness signals as image data. When a user issues an instruction to start reading via the operation unit the scanner unit is instructed via the scanner unit I F to read a document. Upon receiving the instruction the scanner unit operates to read the document.

Reading of the document may be performed by an automatically feeding method in which the document is set on a document feeder not illustrated or by a method in which the document is placed on a glass surface not illustrated and an exposure unit is moved for scanning the document.

In the printing apparatus including the scanner unit is described. However if the printing apparatus includes at least the printing unit the present invention can be applied.

A spooler controls a print instruction generated in the information processing apparatus . Even when a plurality of print instructions is simultaneously issued the document data is temporarily stored as a spool file and the print instructions can be sequentially performed. The spooler obtains a public key that is an encryption key used for encrypting data and a secret key used for decrypting the data encrypted by the public key .

A printer driver is a printer driver set provided by a printer vendor and is stored in a recording apparatus in the information processing apparatus . The printer driver generates print data to be transmitted to a printing apparatus and performs processing for transmitting the data to the printing apparatus .

A decryption processing unit is a module that performs decryption processing on the spool file received from the spooler . A raster generation processing unit is a module that generates an image from information in a vector form or outline font form to generate page description language PDL data. A PDL generation processing unit is a module that converts the image into a data form that the printing apparatus can interpret and includes a printer control command such as a finisher added to a compressed image data. An encryption processing unit is a module that again encrypts the PDL data and transmits the encrypted data.

The printing apparatus receives the print data and performs print output. A decryption processing unit is a module that decrypts the encrypted data received from the printer driver . A public key and a secret key are used respectively for encryption processing by the printer driver and decryption processing by the printing apparatus and are held in the printing apparatus .

A network is used for a local area network LAN inside an office and a plurality of apparatuses such as a client apparatus and a server apparatus are connected to each other via the network .

According to the present exemplary embodiment the server apparatus includes the spooler and the printer driver . Both of the applications and included respectively in the client apparatus and the server apparatus that are connected to each other via the network are a subject of the present exemplary embodiment.

A printing apparatus corresponds to the printing apparatus . A printing apparatus may be connected to the server apparatus via an interface such as the network and the USB or may be directly connected to the network .

In step S upon receiving a print instruction from the user the application generates the document data to be printed using a graphic function for example. Detailed generation processing of the document data depends on the application and the OS. For example PDF is generated as a document for Mac OS and PostScript is generated for Linux.

In step S the application requests the public key from the spooler in the information processing apparatus .

In step S it is determined whether the public key requested in step S is obtained. When the public key described in step S can be obtained in step S YES in step S the encryption processing unit encrypts the document data using the public key in step S. Since the encryption is performed according to a known method using a public key details of encryption processing are not described here. In step S the application transmits the document data encrypted in step S to the spooler .

When the public key cannot be obtained due to an occurrence of an error or the like in step S NO in step S the application displays a screen to notify the user that printing is stopped and ends the printing processing in step S. The display processing in step S is displayed in a message dialog by the application .

Referring to a flowchart of processing by the spooler will be sequentially described. The spooler holds the public key for encryption performed by the application and the secret key for decryption performed by the printer driver .

In step S the spooler receives the document data to be printed from the application . The reception processing varies depending on the spooler . For example the spooler may receive the document data simply via a local path or via the network according to Internet Printing Protocol IPP .

In step S the spooler generates the spool file and temporarily stores the document data in the recording apparatus in the information processing apparatus .

In step S the spooler obtains information about the secret key to be held and records the information about the secret key in a memory accessible only by the spooler .

In step S the spooler activates the printer driver that generates the print data which is an object to be printed by the printing apparatus . Regarding activating of the printer driver in step S the spooler activates the printer driver as one of the processes and further as a child process of the spooler . At this point the spooler provides a path of the spool file as an argument for activating.

If the spooler provides the path of the spool file as an argument for activating other users can easily confirm a status of a process in the information processing apparatus using a system command. Therefore it is possible to refer to the spool file . However since the spool file is encrypted the spool file cannot be decrypted without the information about the secret key . Thus other users cannot browse the document.

The spooler transmits the secret key to the printer driver when activating the printer driver in step S. Accordingly a pipe is generated to connect a process of the spooler to that of the printer driver .

In step S the spooler provides information about the secret key developed in a memory space which is accessible only by the spooler to the printer driver which is instructed by the spooler to activate. The spooler writes the information into the pipe connected to the printer driver . Since only the spooler delivers and the printer driver receives the secret key via the pipe other users or other processes cannot obtain the information about the secret key . Accordingly even if the encrypted data should be leaked the data cannot be decrypted by anything but the printer driver resulting in preventing the secret information from leakage.

Referring to a flowchart of processing for generating print data by the printer driver will be described in detail.

In step S the printer driver activated by the spooler as the child process of the spooler opens the spool file using the information about the path of the spool file provided as an activating argument by the spooler .

In step S a decryption processing unit of the printer driver performs decryption processing. In the decryption processing performed in step S the secret key is read from the pipe connecting the spooler to the printer driver and developed in the memory space accessible only by the printer driver . Further the spool file opened in step S is read into the same memory space accessible only by the printer driver .

The decryption processing by the decryption processing unit is performed according to a known decryption method using secret key information. The decryption processing unit stores the data decrypted in step S in a memory space accessible only by the printer driver . In step S the raster generation processing unit in the printer driver refers to the document data that is decrypted in step S and stored in the memory space and performs raster generation processing for converting the data into bitmap data.

The raster generation processing is generally referred to as rendering and a module that performs the raster generation processing is referred to as a renderer. The raster generation processing performed in step S may use a unique renderer provided by a printer vender as well as a renderer called out from the system.

However when the system renderer is used for example the raster generation processing unit directly calls out the system renderer via an application programming interface API of the system renderer so that the document data cannot be referred from an outside. The raster generation processing unit stores the raster data in the memory space accessible only by the printer driver .

In step S the PDL generation processing unit in the printer driver refers to the data that is converted into the raster data in step S and stored in the memory space and performs PDL generation processing for converting the data into PDL data appropriate for the printing apparatus . The PDL generation processing unit stores the PDL data in the memory space accessible only by the printer driver .

In step S the encryption processing unit in the printer driver requests the public key in order to again encrypt the data converted into the PDL data in step S.

In step S if the public key can be obtained by the processing in step S YES in step S the process proceeds to step S and the encryption processing unit refers to the data that is converted into the PDL data in step S and stored in the memory space and performs decryption processing using the public key .

Decryption in step S may be performed according to a known method of decryption using a public key as well. In step S the encryption processing unit transmits the data encrypted in step S to the printing apparatus . When the data is transmitted in step S for example the encryption processing unit sets a flag indicating the encrypted data at a head portion of the data to be transmitted so that encrypted data can be discriminated.

A transmission method varies depending on a form of connection between the information processing apparatus and the printing apparatus . For example when the network is used for the connection a protocol such as line printer daemon LPD is used for transmission. On the other hand when the USB is used a method is determined based on a specification of the interface.

In step S when the public key cannot be obtained for some reason for example when the printing apparatus is not adapted to receive the encrypted data the encryption processing unit proceeds to step S without performing the encryption processing in step S.

In step S the encryption processing unit transmits the unencrypted data as it is to the printing apparatus and the printer driver ends the processing. At this point the flag indicating the decrypted data is not set at the head of the data to be transmitted.

When the public key is not obtained in step S a screen indicating that printing is stopped may be displayed for the user and the print processing is ended. In display processing a message dialog is displayed on the information processing apparatus that includes the application.

The printing apparatus holds the public key for encryption by the printer driver and the secret key for decryption by the printing apparatus . Referring to a flowchart of a flow of processing performed by the printing apparatus will be specifically described.

In step S the decryption processing unit of the printing apparatus determines whether the print data received in step S is the encrypted data. The encrypted print data can be determined in step S according to whether the flag indicating the encrypted data is set at the head portion of the received print data.

In step S if the flag indicating the encrypted data is set at the head of the received print data the decryption processing unit determines that the received print data is encrypted. In step S the decryption processing unit performs the decryption processing using the secret key held by the printing apparatus itself. The decryption processing is performed in step S according to a known decryption processing using a secret key. In step S the print processing unit of the printing apparatus performs the print processing on the data decrypted by the decryption processing unit .

When the received print data is checked in step S if it is determined that the print data is not the encrypted data the processing proceeds to step S without performing the decryption processing in step S.

In step S the print processing unit performs the print processing and ends the print processing in the printing apparatus .

According to the exemplary embodiment as above described the application encrypts the data using the public key obtained from the spooler . The printer driver activated by the spooler decrypts the encrypted document data using the secret key held by the spooler . Further the printer driver encrypts the PDL data using the public key obtained from the printing apparatus . The printing apparatus decrypts the data using the secret key and prints out the decrypted data.

In the configuration as described above the secured printing system can be established in which the document data is not illegally browsed during the printing process performed by the application in the printing apparatus.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims priority from Japanese Patent Application No. 2008 030322 filed Feb. 12 2008 which is hereby incorporated by reference herein in its entirety.

