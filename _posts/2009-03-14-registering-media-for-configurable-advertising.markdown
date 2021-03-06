---

title: Registering media for configurable advertising
abstract: A method for registering a media for configurable advertising is described herein. Advertising policies from a publisher of the media may be received at a video advertising platform. A request from the publisher to register the media for advertising may be received at a video advertising platform. The request may have media metadata. A media manifest may be generated at the video advertising platform. The media manifest may be based on the media metadata and the advertising policies. The media manifest may be configured to be received by a media player. The media player may play the media with one or more advertisements as specified by the media manifest.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08370198&OS=08370198&RS=08370198
owner: Microsoft Corporation
number: 08370198
owner_city: Redmond
owner_country: US
publication_date: 20090314
---
According to current models of advertising breaks to show advertisements may be defined according to a schedule. As a result the broadcasting of video programs such as television broadcasting may be designed to accommodate the advertising schedule. When the time for an advertising break arrives the television program is interrupted. At the end of the advertising break the television program may resume or another television program may start.

One drawback with this model is that the producer of the program cannot control the occurrence or timing of the advertising breaks. This may lead to incongruous inappropriate or ineffective advertisements being displayed to viewers. Advertising breaks according to a fixed schedule can be disruptive to the natural flow of a television program. As a result the viewer experience when watching a program may be degraded and the effectiveness of the advertisements may decrease.

Similar issues arise when advertising within Internet based video. Videos that are distributed within an IP based system typically have advertising breaks hardwired into specific time slots which may also degrade the viewer experience and the effectiveness of advertising.

Described herein are implementations of various technologies for registering media for configurable advertising. The media may include audio video or other multimedia presentations that is distributed over the Internet. A publisher of the media may register the media with a video advertising platform VAP . The VAP may receive ad policies and a registration request from the publisher.

The ad policies may specify information such as how much and what types of advertising are to be shown within the media. The possible ad policies may be extensive and can be configured by the publisher. Ad policies may be assigned to specific media or to more general categories.

The registration request may include media metadata such as a title a video length actors or any information the publisher wants to provide that describes the media.

The VAP may generate a media manifest that maps the applicable ad policies to the registered media. The media manifest may describe a specific advertising schedule for the registered media. The media manifest may also specify an ad delivery server that provides the specific advertisements.

Upon registering the VAP may expose web service application programming interfaces APIs to the publisher. The publisher may use the web service APIs to update the media metadata and the ad policies. Updates from the publisher trigger a re generation of the media manifest with new or updated policies.

The claimed subject matter is not limited to implementations that solve any or all of the noted disadvantages. Further the summary section is provided to introduce a selection of concepts in a simplified form that are further described below in the detailed description section. The summary section is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter.

In general one or more implementations of various technologies described herein are directed towards registering media for configurable advertising. The various implementations will be described in more detail in the following paragraphs.

Implementations of various technologies described herein may be operational with numerous general purpose or special purpose computing system environments or configurations. Examples of well known computing systems environments and or configurations that may be suitable for use with the various technologies described herein include but are not limited to personal computers server computers hand held or laptop devices multiprocessor systems microprocessor based systems set top boxes programmable consumer electronics network PCs minicomputers mainframe computers distributed computing environments that include any of the above systems or devices and the like.

The various technologies described herein may be implemented in the general context of computer executable instructions such as program modules being executed by a computer. Generally program modules include routines programs objects components data structures etc. that perform particular tasks or implement particular abstract data types. The various technologies described herein may also be implemented in distributed computing environments where tasks are performed by remote processing devices that are linked through a communications network e.g. by hardwired links wireless links or combinations thereof. In a distributed computing environment program modules may be located in both local and remote computer storage media including memory storage devices.

The network may be any network or collection of networks that facilitates communication between the client the publisher and the VAP as described herein. In one implementation the network is the Internet.

The client may be a computing system on which the media player is executed. The media player may be software that plays back multimedia files such as a media . The media may be an audio file a video file streaming versions of the same or the like.

In one implementation the media player may only play back video such as television shows movies and on line video segments. In such an implementation the media player may be known as a video player. In another implementation the media player may play back both audio and video files such as the Windows Media Player .

A user may operate the media player to request the media from the publisher for playback on the client . The publisher may be a computing system that provides access to the media . The publisher may be operated by a media distribution company such as television networks Internet portals and the like.

In one implementation the media may be provided to the publisher by a content owner not shown that produces the media . For example the content owner may specialize in producing video media and send a video to the publisher for distribution to the user. The content owner may be a movie production studio a television production company or the like.

The publisher may provide access to the video for the user via a content delivery network CDN . The CDN not shown may be a system of computers networked together across the Internet that cooperate transparently to deliver content i.e. media to users. The CDN is typically used for the purpose of delivering the media with high performance scalability and cost efficiency. Some examples of CDNs include Amazon Cloudfront Limelight Networks and BitGravity .

The media may be used to generate revenue through advertising. The VAP may facilitate advertising with the playback by the media player . In one implementation the VAP may provide a manifest to the media player .

The manifest may specify how and when the advertisements are shown with the playback of the media . For example the manifest may specify that the advertisements are shown during a break at the 15 minute mark of the playback. In one implementation the manifest may be in an XML format.

The VAP may include a manifest service a registration service and an ad delivery service . The manifest service may receive a request for the manifest from the media player . In response the manifest service may determine the manifest for the media and the media player . The manifest service may then send the manifest to the media player .

The manifest may also specify one or more uniform resource locators URLs from which the media player obtains the advertisements . In one implementation the URL may specify the ad delivery service or a third party ad delivery service not shown .

The manifest may be generated based on preferences provided to the registration service by the publisher . In one implementation the publisher may register the media for advertising with the VAP . In such an implementation the registration service may receive a registration request from the publisher .

The registration request may include media metadata. The media metadata may describe the media itself. Media metadata may include a title participants such as actors writers and directors a time length a release date and the like.

Additionally the registration service may receive ad policies from the publisher . The ad policies may describe rules for presenting the advertisement to the user. The policies may be defined by the publisher at several levels of hierarchy. For example policies may be defined for the publisher for a particular piece of media a class of media such as television movies and a type of the media player that performs the playback.

Ad policies may include an ad program ratio e.g. a ratio between the time length of the advertisement and the video an ad duration an ad replay policy e.g. how frequently the advertisement can be played a number of ad positions available during the playback a maximum number of ads per ad position a click to continue option e.g. whether user is allowed to click an input device on the client to continue the playback without completion of the advertisement and an ad skip threshold e.g. a number of advertisements the user is allowed to skip during playback or a duration of the advertisement that is shown before the user is allowed to skip the remainder of the advertisement .

The number of ad positions available during the playback may specify how many opportunities for advertising the publisher allots in the media. For example the publisher may allot ad positions within a video. Each ad position may specify a time during playback of the video when the media player may show the advertisements .

However all available ad positions may not be used during the playback. Other ad policies may affect the number of ad positions used. For example a low ad program ratio for example may limit the number of ad positions that the media player may use for advertising.

Ad policies may also include an ad type. The ad type may describe a format for advertising during the playback. For example ad types may include linear non linear pre roll and post roll advertisements. In one implementation ad policies may include the enablement of specified ad types.

The linear type advertisement may indicate that the advertisement may be shown while the playback is paused and the playback is resumed when the advertisement completes. The non linear type advertisement may indicate that the advertisement is shown during the playback typically in a format like a graphic overlay or rolling text.

The pre roll type advertisement may indicate that the advertisement is shown prior to starting the playback. Similarly the post roll type advertisement may indicate that the advertisement is shown after finishing the playback.

In one implementation the registration service may store the registration request ad policies media metadata and advertising metadata in the registration database . Additionally the registration service may create the manifest for the registered media based on the ad policies media metadata and advertising metadata.

It should be understood that the ad policies ad types media metadata and advertising metadata described above are merely for illustration and not intended to be limiting. Implementations of the various techniques described herein may include other ad policies ad types media metadata and advertising metadata.

In implementations of the various techniques described herein the VAP may be a single server or multiple distributed servers interoperating across the network . Further the components of VAP manifest service registration service and ad delivery service may be implemented on these distributed devices.

At step the registration service may receive the ad policies from the publisher . In addition to the description of ad policies described above the ad policies may be dynamically configurable by the publisher to customize advertising schemes.

For example the ad policies may be defined in an extensible format such as XML. Advantageously by using XML to define the ad policies the publisher may create new types of ad policies in order to create highly customized advertising schemes.

For example the publisher may define an ad policy based on a type of client . The type of client may include a variety of viewer devices such as set top boxes mobile phones personal computers gaming system and the like.

In such a case that ad policy for the click to continue option may be varied based on the client type. For example one ad policy may specify that the click to continue option is not available for ads sent to a television set. Another ad policy may specify that the click to continue option is available for ads sent to a personal computer.

At step the registration service may receive the registration request. As stated previously the registration request may contain metadata about the media . In one implementation the registration request may also include advertising metadata such as the number of available ad positions in the media .

Further the media metadata may be used to assign an ad policy to one or more media. For example the media metadata may include a producer a title and an age based rating. A particular ad policy may be defined for all media from the same producer all media with the same title or all media rated for viewers 13 years of age and older.

In one implementation the registration request may also include reporting preferences for the media . Reporting may show how successful the ad policies are for the media and provide information that can help improve advertising through updates to the ad policies etc. For example reporting may show how often the user uses the click to continue option or how often the user buys a product in response to the advertisement .

At step the registration service may validate the request. The validation may apply standard edits to the metadata in the request to ensure the registration request is valid. For example the registration service may edit for spelling punctuation etc.

In one implementation the registration service may compare ad policies to verify that ad policies do not conflict. For example if one ad policy states that the click to continue option is not available for television but another ad policy states that the click to continue option is available for television the registration request may be rejected as invalid.

At step the media manifest may be generated. The media manifest may be generated by determining all of the applicable ad policies for the media . Each applicable ad policy may then be translated into a specific advertising scheme for the media.

For example the ad policies may specify that the media include a pre roll advertisement and that the program ad ratio is 10 . If the media is 30 minutes long the media manifest may specify that 3 minutes 10 of 30 minutes of advertising be shown before the playback.

At step an application programming interface API may be provided for the publisher to view and update the registration and ad policies. The APIs may enable the publisher to update or create new ad policies media metadata and advertising metadata. In one implementation the API may be a web service API.

If the publisher sends updates for a particular media the method may be repeated to generate a new media manifest . The new media manifest may be provided for all future requests for playback of the media .

The system bus may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. By way of example and not limitation such architectures include Industry Standard Architecture ISA bus Micro Channel Architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards Association VESA local bus and Peripheral Component Interconnect PCI bus also known as Mezzanine bus.

The system memory may include a read only memory ROM and a random access memory RAM . A basic input output system BIOS containing the basic routines that help transfer information between elements within the VAP such as during start up may be stored in the ROM .

The VAP may further include a hard disk drive for reading from and writing to a hard disk a magnetic disk drive for reading from and writing to a removable magnetic disk and an optical disk drive for reading from and writing to a removable optical disk such as a CD ROM or other optical media. The hard disk drive the magnetic disk drive and the optical disk drive may be connected to the system bus by a hard disk drive interface a magnetic disk drive interface and an optical drive interface respectively. The drives and their associated computer readable media may provide nonvolatile storage of computer readable instructions data structures program modules and other data for the VAP .

Although the VAP is described herein as having a hard disk a removable magnetic disk and a removable optical disk it should be appreciated by those skilled in the art that the VAP may also include other types of computer readable media that may be accessed by a computer. For example such computer readable media may include computer storage media and communication media.

Computer storage media may include volatile and non volatile and removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Computer storage media may further include RAM ROM erasable programmable read only memory EPROM electrically erasable programmable read only memory EEPROM flash memory or other solid state memory technology CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can be accessed by the VAP .

Communication media may embody computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and may include any information delivery media. The term modulated data signal may mean a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal. By way of example and not limitation communication media may include wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of the any of the above may also be included within the scope of computer readable media.

A number of modules may be stored on the hard disk magnetic disk optical disk ROM or RAM including an operating system one or more application programs the manifest service the registration service the ad delivery service and a database system . The operating system may be any suitable operating system that may control the operation of a networked personal or server computer such as Windows Vista Mac OS X Unix variants e.g. Linux and BSD and the like.

The registration service may receive registration requests from the publisher and generate manifests for delivery by the manifest service . The registration service may also provide an interface to the publisher that the publisher may use to view and update a registration. The ad delivery service may receive advertisement requests from the media player and send the advertisement in response.

A user may enter commands and information into the VAP through input devices such as a keyboard and pointing device . Other input devices may include a microphone joystick game pad satellite dish scanner or the like. These and other input devices may be connected to the CPU through a serial port interface coupled to system bus but may be connected by other interfaces such as a parallel port game port or a universal serial bus USB . A monitor or other type of display device may also be connected to system bus via an interface such as a video adapter . In addition to the monitor the VAP may further include other peripheral output devices such as speakers and printers.

Further the VAP may operate in a networked environment using logical connections to one or more remote computers such as a remote computer . The remote computer may be another personal computer a server a router a network PC a peer device or other common network node. Although the remote computer is illustrated as having only a memory storage device the remote computer may include many or all of the elements described above relative to the VAP . The logical connections may be any connection that is commonplace in offices enterprise wide computer networks intranets and the Internet such as local area network LAN and a wide area network WAN .

When using a LAN networking environment the VAP may be connected to the LAN through a network interface or adapter . When used in a WAN networking environment the VAP may include a modem wireless router or other means for establishing communication over a wide area network such as the Internet. The modem which may be internal or external may be connected to the system bus via the serial port interface . In a networked environment program modules depicted relative to the VAP or portions thereof may be stored in a remote memory storage device . It will be appreciated that the network connections shown are exemplary and other means of establishing a communications link between the computers may be used.

It should be understood that the various technologies described herein may be implemented in connection with hardware software or a combination of both. Thus various technologies or certain aspects or portions thereof may take the form of program code i.e. instructions embodied in tangible media such as floppy diskettes CD ROMs hard drives or any other machine readable storage medium wherein when the program code is loaded into and executed by a machine such as a computer the machine becomes an apparatus for practicing the various technologies. In the case of program code execution on programmable computers the computing device may include a processor a storage medium readable by the processor including volatile and non volatile memory and or storage elements at least one input device and at least one output device.

One or more programs that may implement or utilize the various technologies described herein may use an application programming interface API reusable controls and the like. Such programs may be implemented in a high level procedural or object oriented programming language to communicate with a computer system. However the program s may be implemented in assembly or machine language if desired. In any case the language may be a compiled or interpreted language and combined with hardware implementations.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts described above are disclosed as example forms of implementing the claims.

