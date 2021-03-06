---

title: Apparatus and method for creating widget in portable terminal
abstract: Provided are an apparatus and a method for creating a widget of a portable terminal. The method includes: determining a building block that a user selects on a widget creating screen including building blocks necessary for widget creation; generating a tag of data corresponding to the confirmed building block; and generating a widget code including the building block and the tag.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08443291&OS=08443291&RS=08443291
owner: Samsung Electronics Co., Ltd.
number: 08443291
owner_city: Suwon-si
owner_country: KR
publication_date: 20091230
---
The present application is related to and claims priority under 35 U.S.C. 119 of a Korean patent application filed in the Korean Intellectual Property Office on Dec. 30 2008 and assigned Serial No. 10 2008 0136305 the entire disclosure of which is hereby incorporated by reference.

The present invention relates generally to an apparatus and a method for creating a widget in a portable terminal. More particularly the present invention relates to an apparatus and a method for directly creating a widget format that a user wants.

That is the present invention provides an apparatus and a method for allowing a common user to create a widget without difficulties which typically only can be created by a widget specialized software company or a professional developer.

Recently as portable terminals have been drastically developed they are being used by men and women of all ages as necessities and also are used as media for wireless voice communication and information exchange.

At the beginning portable terminals were recognized as tools for just wireless voice communication but as their technologies are developed service providers and portable terminal manufacturers have competitively developed products or services in order to distinguish them from others.

For example the portable terminals are being developed as multimedia devices capable of providing different functions such as a phone book short message service SMS E mail morning call an MP3 player scheduling a digital camera and wireless internet service so that a variety of services can be provided.

In addition as web 2.0 technology has been extensively used in the portable terminals a certain widget of a personal computer for providing an additional function is being applied to the portable terminals.

The widget is a service provided from a mobile communication provider and is used to organize a screen of a portable terminal. For example a dog may run around or a weather forecast may be checked in advance through a downloaded weather widget on the screen of the portable terminal.

In relation to the widget a user needs to complete a simple widget resource disposition through a basic resource editor and also needs to directly code eXtensible Markup Language XML and java script. However this method makes utilizing a widget difficult for a user who has no coding experience. That is the widget is typically created by widget specialized software companies such as portals.

Additionally the widget only has a limited available service such as displaying of information set by a user and providing an application shortcut function and information of the portable terminal. Accordingly when a user of the portable terminal wants to display information using a user preference applied setting value the information is displayed through setting information e.g. fonts fixed by a widget which is set during creating of the widget and not by user preference of the portable terminal.

Accordingly in order to resolve the above limitation an apparatus and a method allowing a user to create a widget to which user preference is applied without difficulties are required.

To address the above discussed deficiencies of the prior art it is a primary aspect of the present invention to solve at least the above problems and or disadvantages and to provide at least the advantages below. Accordingly an object of the present invention is to provide an apparatus and a method for creating a widget in a portable terminal.

Another aspect of the present invention is to provide an apparatus and a method for applying user preference when a widget is created in a portable terminal.

Yet another aspect of the present invention is to provide an apparatus and a method for creating a widget in a portable terminal through a drag and drop method by a user.

In accordance with an aspect of the present invention an apparatus for creating a widget of a portable terminal includes a widget creating unit generating a tag of data corresponding to a building block that a user selects on a widget creating screen that includes building blocks necessary for widget creation.

In accordance with another aspect of the present invention a method for creating a widget of a portable terminal includes determining a building block that a user selects on a widget creating screen including building blocks necessary for widget creation generating a tag of data corresponding to the determined building block and generating a widget code including the building block and the tag.

Before undertaking the DETAILED DESCRIPTION OF THE INVENTION below it may be advantageous to set forth definitions of certain words and phrases used throughout this patent document the terms include and comprise as well as derivatives thereof mean inclusion without limitation the term or is inclusive meaning and or the phrases associated with and associated therewith as well as derivatives thereof may mean to include be included within interconnect with contain be contained within connect to or with couple to or with be communicable with cooperate with interleave juxtapose be proximate to be bound to or with have have a property of or the like. Definitions for certain words and phrases are provided throughout this patent document those of ordinary skill in the art should understand that in many if not most instances such definitions apply to prior as well as future uses of such defined words and phrases.

Throughout the drawings like reference numerals will be understood to refer to like parts components and structures.

Hereafter an apparatus and a method for creating a widget of a portable terminal to which user preference is directly applied will be described according to the present invention.

The controlling unit of the portable terminal performs the overall operations of the portable terminal for example processing and controlling operations for voice and data communications. The widget creating unit allows a user to directly create a desired widget.

In more detail when a user of the portable terminal creates a widget the controlling unit instructs the widget creating unit to display a widget creating screen for outputting data necessary for widget creation such that a user can create a widget.

Next the controlling unit determines a building block that a user selects among building blocks that constitute a widget that a user of the portable terminal creates and also determines property information such as font types and font sizes constituting a widget.

Accordingly the controlling unit creates a widget by generating widget codes that include tags for property information to which user personality is applied in a corresponding building block. The widget code means a code that can request data related to a corresponding building block.

The widget creating unit receives an instruction from the controlling unit and outputs a widget creating screen in order to allow a user to directly create a widget. At this point a user of the portable terminal creates a widget by selecting items necessary for creating the widget from the widget creating screen through a drag and drop method.

The memory unit includes ROM RAM and flash ROM. The ROM stores micro codes of a program and various reference data for processing and controlling the controlling unit .

The RAM is a working memory of the controlling unit for storing temporary data generated during various program executions. Additionally the flash ROM stores various updatable data for archive such as a phone book sent messages and received messages.

The input unit includes a plurality of function keys such as 0 to 9 number key buttons a menu button a cancel button or a delete button a OK button a call button an end button an internet connection button navigation key or a direction key buttons and letter input key buttons and also provides key inputted data e.g. a widget creating request corresponding to a user pressed key to the controlling unit . Additionally the input unit includes a touch input unit for sensing a touch input and senses a touch input of a user and then provides the sensed touch input to the controlling unit .

The display unit displays state information generated during an operation of the portable terminal the limited number of letters and a plurality of moving or still pictures. The display unit uses a color Liquid Crystal Display LCD device.

The widget engine as mentioned above includes an API mapping unit and an API calling unit and drives widgets created by the widget creating unit .

When the widget engine senses a request for executing a widget created by a user it processes the request by mapping an Original Equipment Manufacturer OEM API corresponding to the request to call a corresponding OEM API.

The API mapping unit of the widget engine maps an instruction for a widget executing method e.g. a phone book searching method into the OEM API i.e. API corresponding to a mapping widget execution and then delivers it to the API calling unit . Accordingly the API calling unit calls the OEM API that controls phone book information that is an internal function of the portable terminal. Next the API calling unit generates a calling result of the OEM API and then delivers it to the API mapping unit and the API mapping unit provides data that a user requests using the calling result delivered from the API calling unit .

That is the API mapping unit manages data necessary for widget creation as eXtensible Markup Language XML tags and links them with a corresponding API.

Although the role of the widget creating unit may be performed herein by the controlling unit of the portable terminal its configuration and operations are just one example for convenience of description and are not intended to limit the scope of the present invention. It is apparent to those skilled in the art that various modifications are possible within the scope of the present invention. For example all of these may be configured to be processed in the controlling unit .

The above is described with respect to an apparatus for creating a widget of a portable terminal to which user preference is directly applied according to the present invention and a method for creating a widget to which user preference is directly applied to using the above apparatus according to one embodiment of the present invention will be described.

Referring to the portable terminal determines whether a widget creating event occurs or not in step . Here the widget creating event is an event for directly creating a widget by a user of the portable terminal.

If the widget creating event does not occur in step the portable terminal proceeds to step to perform a corresponding function e.g. a standby mode .

On the contrary if the widget creating event occurs in step the portable terminal proceeds to step to display a widget creating screen and then proceeds to step to select a building block for widget creation.

Here the widget creating screen is a screen where data necessary for widget creation are outputted to create a widget directly and simply by a user of the portable terminal i.e. an authorized tool execution screen for widget creation. Additionally the building block means blocks constituting a widget created by a user of the portable terminal and includes a weather information block a schedule managing block and an address block.

Next the portable terminal proceeds to step to convert data related to a corresponding building block into one appropriate for widget creation and proceeds to step and then generates a widget code related to a corresponding building block. That is step is a step for generating a code to request data related to a corresponding building block.

Next the portable terminal proceeds to step and then determines whether widget creation is completed or not.

If the widget creation is not completed in step the portable terminal proceeds to step and then repeats the above operations until the widget creation is completed. That is the portable terminal repeats the above operations until all building blocks that a user wants to add to a widget are created.

In addition if the widget creation is completed in step the portable terminal terminates this algorithm.

Referring to the portable terminal determines whether a widget creating event occurs or not in step . Here the widget creating event is an event for creating a widget through which a user of the portable terminal personally manages a phone book.

If the widget creating event does not occur in step the portable terminal proceeds to step to perform a corresponding function e.g. a standby mode .

Otherwise if the widget creating event occurs in step the portable terminal proceeds to step to display a widget creating screen and then proceeds to step to select a building block for widget creation.

Here the widget creating screen is a screen where data necessary for widget creation are outputted to create a widget directly and simply by a user of the portable terminal i.e. an authorized tool execution screen for widget generation. Additionally the building block are blocks constituting a widget created by a user of the portable terminal and a building block related to a phone book widget includes one block in which data stored in a phone book are searched by a name and another block in which the data stored in a phone book are searched by a number .

Next the portable terminal proceeds to step and processes to convert phone book data stored in the portable terminal into XML and to link the converted XML with the widget.

Next the portable terminal proceeds to step to set property information that represents information such as font types and font sizes of a corresponding widget screen according to user preference and then proceeds to step to generate tags e.g. search tags for each number and search tags for each name for the phone book data converted in step . Using the above method the portable terminal reflects property information on the widget User Interface UI such that a widget to which user personality is applied can be used.

Later the portable terminal proceeds to step to generate widget codes related to a corresponding building block through the tags. That is step is a step for generating codes for requesting data related to a corresponding building block.

Next the portable terminal proceeds to step and then determines whether widget creation is completed or not.

If the widget creation is not completed the portable terminal proceeds to step and then repeats the above steps until the widget creation is completed.

Although operations for creating a widget in the portable terminal are described with reference to according to one embodiment of the present invention the present invention may be applied to a personal computer in order to create a widget other than a portable terminal and then may allow the portable terminal to download a widget created by the personal computer.

Referring to the portable terminal is in a state in which a widget is created and downloaded and thus the widget engine proceeds to step first and then executes the widget. At this point if it is assumed that the widget is a widget related to a phone book widget execution may be an operation for searching phone book data. For one example the widget execution is an operation in which a user of the portable terminal searches phone book data using a name or a phone number through the widget.

Next the widget engine proceeds to step to allow an API mapping unit to map an instruction for a phone book searching method that a user selects into an OEM API API corresponding to a mapping widget execution defined in the widget engine and then proceeds to step to call a corresponding API using an API calling unit. That is the API calling unit which receives an instruction from the controlling unit calls the OEM API that controls phone book information that is an internal function of the portable terminal.

Next the widget engine proceeds to step to search data for a corresponding method and allows the API calling unit to generate a calling result of the OEM API and then delivers the calling result to the API mapping unit.

Accordingly the widget engine proceeds to step and allows the API mapping unit to provide data that a user requests using the calling result delivered from the API calling unit. That is the widget engine provides a result about a searching method that a user requests as a widget execution result.

As shown in a widget code generated using OEM API of a widget authorizing tool includes class XML tag DOM API etc. defined in the widget engine.

Accordingly a widget engine of a portable terminal parses a widget class pb for a phone book containing user information predetermined name tag and a getElementsByname method in step and reads user information of the portable terminal by calling the corresponding OEM API to deliver its result value as a widget method result value in step .

As mentioned above the present invention relates to an apparatus and a method for allowing a common user to create a widget without difficulties which typically only can be created by a widget specialized software company or a professional developer. In addition the present invention makes it possible to create a widget of a portable terminal to which user personality is applied such that it can give pleasure to a user of the portable terminal.

While the invention has been shown and described with reference to certain preferred embodiments thereof it will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the spirit and scope of the invention as defined by the appended claims. Therefore the scope of the invention is defined not by the detailed description of the invention but by the appended claims and all differences within the scope will be construed as being included in the present invention.

