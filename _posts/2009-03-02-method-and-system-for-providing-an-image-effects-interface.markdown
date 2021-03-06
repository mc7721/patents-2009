---

title: Method and system for providing an image effects interface
abstract: A method and system for generating user-accessible effects. The method includes receiving a library of operators, each operator including a set of operations performable on an image. The method includes receiving an effect definition from a designer via a graphical user interface, wherein the effect definition includes a set of operators from the library to be executed on a user-provided image and parameters associated with each operator. The method includes saving the effect definition to an accessible memory. The method includes uploading the effect definition to a servers wherein the effect definition is accessible to a user over a network.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09483237&OS=09483237&RS=09483237
owner: BEFUN BILGI TEKNOLOJILERI A.S.
number: 09483237
owner_city: Istanbul
owner_country: TR
publication_date: 20090302
---
This application is a Continuation In Part of co pending U.S. patent application Ser. No. 12 371 243 entitled METHOD AND SYSTEM FOR GENERATING ONLINE CARTOON OUTPUTS filed on Feb. 13 2009 which claims the benefit of U.S. Provisional Patent Application Ser. No. 61 032 398 entitled METHOD SYSTEMS AND INTERFACES FOR GENERATING ONLINE CARTOONS IN 2D SCENES filed on Feb. 28 2008 and which are expressly incorporated by reference herein.

Multimedia is media and content that utilizes one or more content forms. For example multimedia can include text audio still images animation video and interactivity content forms. Multimedia can be transmitted over a network such as an Internet and be used to communicate. For example digital photos can be posted as a photo album online for viewing by any member of the public. In another example a user can utilize a digital photo as an online avatar or representative icon in user transactions online.

Digital images can be obtained in a variety of ways including from a digital camera a scanner scanning a physical paper or via various graphical applications for creating digital imagery. Such digital images can be stored in a variety of standard Raster file formats including JPEG BMP TIFF RAW PNG and GIF. Alternatively digital images can be stored in vector formats such as CGM and SVG.

Media including digital images can be manipulated via various operators which create or enhance media characteristics. Example operators for images include transforming clustering diffusion filtering and thresholding. For example filtering can removing undesired characteristics within an image such as a specific color or brightness.

Multiple operators can be combined to form effects that alter a digital image in a predetermined manner. For example an effect for converting a color image to a black and white image for transmission over the Internet can crop the image to a manageable size remove noise from the image and convert brightness of image pixels into a grayscale pixel. The effect thus provides a black and white image ready for distribution over the Internet.

A graphical user interface GUI is a type of user interface which allows people to interact with electronic devices such as computers hand held devices such as MP3 Players Portable Media Players or gaming devices household appliances and office equipment. A GUI offers graphical icons and visual indicators as opposed to text based interfaces typed command labels or text navigation to fully represent the information and actions available to a user. The actions are usually performed through direct manipulation of the graphical elements via devices such as pointer devices.

Thus there is a need to provide an improved user interface allowing designers to easily design effects from pre existing operators and to provide the effects to users over a network from a server.

A graphical user interface allows designers to create effects from available operators. For example image operators are coded by developers to manipulate digital images and compiled into an operator library. The operator library is compiled and distributed to the designers along with a GUI executable. The designers utilize the GUI to define a desired effect via manipulations of available operators. For example an effect can be defined by specifying which operators are used the order in which the operators are used and operator parameters. Once the effect is defined an effect definition is created and uploaded to a server. The server makes the effect available to users over a network. Example effects can include converting a user provided image into a cartoon

In a developer conceives and codes a new operator. The operator can be coded in a programming language such as C and exploit CPU and GPU capabilities.

 Please include brief description of each example operator Example operators include transforming clustering diffusion filtering and thresholding. Example transform procedures include fft image3D inv fft image3D correlation fft image3D.

Example diffusion operators include anisotropic diffusion image and coherence enhancing diffusion image.

Example filtering operators include generalized kuwahara image bump emboss image and simulate radial motion image wiener image.

Example thresholding operators include get local entropy threshold image get joint entropy threshold image get global entropy threshold image smooth threshold image solve system image svd and solve system image lu.

In a core library is recompiled with the new operator of . The library is then distributed along with a GUI executable providing a GUI for combining operators into effects. In one example embodiment updates are distributed as patches to the library and or the executable.

In a designer utilizes the core library and included operators to design an effect. The executable can provide a GUI allowing a designer to create an effect by defining which operators to use in what order to use the operators and define parameters for the operators. For example an effect can be designed via a user interface as depicted in .

In the designer saves the effect designed in as an effect definition. For example the GUI executable can allow the designer to preview the effect as applied to one or more test images. Once the designer is satisfied with the effect the effect is saved as an effect definition. For example the effect definition can define the effect in terms of operators and parameters. The effect definition is uploaded to the server.

In the server automatically generates a script language module from the effect definition. For example the scripting language can support low level communication between operators and the library and enhance performance. The script language module can be a translation of the uploaded effect definition.

In the server updates relevant application programming interfaces API . The API can interface between user requests received over a network and the script language module created in .

In the effect is made available online. Users are able to select an effect upload images and receive a processed image in accordance to the effect. For example effects can be accessed by users via a user interface as depicted in .

The terminal communicates with a server over a network . The network can be any network configured to carry digital communications such as the Internet. The server can be a computing device configured to serve one or more terminals as illustrated in .

The server is in communications with a memory . The memory can store computer readable instructions for providing an interface to generate a cartoon responsive to predefined algorithms and user provided parameters. The computer readable instructions can be part of an effects module discussed below.

It will be appreciated that functionality providing effects can be split between the server and the terminal . For example simple pre processing of the image such as cropping or color correction can occur at the terminal . More intensive processing can occur at the server .

In in operation the user submits an image to the server for processing. The user interacts with the server via an effects user interface. Processing includes adding effects to the image. The server executes the module with parameters received from the user which processes the image . A resulting processed image is provided back to the user . It will be appreciated that no physical transmission of the image or processed image is necessary. For example URL addresses can be provided allowing the terminal and the server to retrieve relevant files from locations accessible over the network .

In the terminal optionally receives a GUI executable. As discussed above a GUI executable can be distributed by developers along with a library of available operators. The GUI executable can be configured to provide a GUI allowing a designer to design an effect as illustrated in .

In the terminal tests whether the library of operators has been received. As discussed above the library can be received along with the GUI executable or separately. The library can be compiled by developers and include all pre defined operators available to the designer.

If the library has been received the terminal proceeds to . If the library has not been received the terminal can wait at .

In the terminal tests whether an effect definition has been received from a GUI. The terminal can provide a GUI to the designer for example by executing the GUI executable received in . The GUI can receive designer inputs specifying a new effect such as which operators to use in what order the operators are used and parameters for each operator.

If the effect definition has been received the terminal proceeds to . If the effect definition has not been received the terminal awaits designer input via the GUI at .

In the terminal optionally previews the effect definition as applied to a test image. For example the designer can specify an image on which to test the effect definition as inputted in .

It will be appreciated that the designer can return to to revise the effect definition after previewing.

In the terminal saves the effect definition received in and previewed in to memory. For example the effect definition can be saved to volatile or non volatile memory accessible to the terminal locally or over a network.

In the terminal uploads the effect definition received in and previewed in to a server. The server can be as illustrated in and process the effect definition into a module accessible to users over a network.

The GUI includes tools for the user to define the effect. The tools can include a delete select move a zoom and other tools.

The GUI includes an input output portion . The input output portion can allow a designer to specify an input image to use and an output image to write a processed image to.

The GUI includes a list of available operators . For example available operators can be stored in a compiled library received by the terminal as discussed above.

The GUI includes a graphical view of the current effect definition. The GUI can be a node based interface in which each operator is depicted as a node. Operators can be linked to each other to indicate order of execution. Each node can also include a preview thumbnail of an image illustrating the result of the operator.

The GUI includes operator parameters . The designer can select specific nodes or operators and a set of available parameters will appear. The designer can manipulate various parameters via standard GUI input fields such as slider bars buttons text fields etc.

It will be appreciated that screen shot can illustrate a more advanced interface for designers desiring more control over the definition process. By removing the GUI more parameters are accessible to the designer for manipulation.

The screen shot can include an upload tab . The upload tab can provide functionality related to uploading an image or digital photo for processing.

The screen shot can include a cartoonizer tab . The cartoonizer tab can provide functionality related to converting the image into a cartoon as discussed elsewhere.

The screen shot can include an extra tab . The extra tab can include extra functionality not belonging in either the upload tab or the cartoonizer tab .

The screen shot can include a restore button . The restore button can roll back all user changes to an image. For example user changes can be made via functionality provided with the cartoonizer tab . In an alternative embodiment the restore button can undo a last user change to the image.

The screen shot can include a save button . The save button can save all user changes to an image. In one embodiment the image can be saved on the server and a Uniform Resource Locator URL address pointing to the image provided to the user. In another embodiment the image can be saved to a user specified location.

The screen shot can include an advertisement . For example the advertisement can relate to products and services relevant to the image processing. Example products and services include hardcopy photographs and merchandise printed or otherwise illustrated with the processed image.

The screen shot can include an upload button . The upload button can allow a user to select a local image from the user s terminal for upload to the server.

The screen shot can include a snapshot via webcam button . The snapshot button can allow a user to provide an image taken with a locally available webcam or other photo taking device such as a digital camera.

The screen shot can include an upload from URL button . The URL button can allow a user to provide an URL address pointing to an image. The server the retrieves the image for processing.

The screen shot can include a crop button . The crop button can trigger an interface allow the user to crop an uploaded photograph. For example unnecessary background can be removed. The photograph can be cropped to reduce size and processing time.

The screen shot can include a help button . The help button can provide a help interface describing functionality associated with each tab and button in the screen shot .

The screen shot can include the uploaded image . After the user has uploaded an image the uploaded image can be displayed for user review. The user can for example crop the image and save the image as discussed above.

The screen shot can include a selected cartoonizer tab . As discussed above the cartoonizer tab can provide the user with functionality associated with processing the image.

The screen shot can include a sketch button . The sketch button can provide functionality associated with a sketch function as illustrated later. Sketch functionality can include receiving user specified parameters and processing the image in accordance with predefined algorithms utilizing the received parameters as discussed.

The screen shot can include a color button . The color button can provide functionality associated with a colorization function as illustrated later. Colorization functionality can include receiving user specified parameters and processing the image in accordance with predefined algorithms utilizing the received parameters as discussed.

The screen shot can include a warp button . The warp button can provide functionality associated with a warping function as illustrated later. Warping functionality can include receiving user specified parameters and processing the image in accordance with predefined algorithms utilizing the received parameters as discussed.

It will be appreciated that other functionality can be associated with processing the image as discussed elsewhere. Additional tabs can be provided in the user interface and each tab can be associated with additional buttons to support an additional functionality.

Once the sketch button has been selected the user interface provides the screen shot to receive user specified parameters for the sketch function.

The screen shot can include sketch detail radio buttons . The user can specify a level of detail to be produced in the sketch such as low medium or high . It will be appreciated that alternative input fields can be used such as a text field a slider or other input field.

The screen shot can include a brightness slider . The user can specify a level of brightness to be produced in the sketch. As above alternative input fields can be used.

The screen shot can include an apply button . Once the user has specified the required parameters and any optional parameters the user clicks the apply button . The server then processes the image in accordance with the user specified parameters.

It will be appreciated that other parameters can be associated with processing the image into a sketch as discussed. Additional input fields can receive parameters from the user to provide greater user control over the sketch function.

The screen shot can include a color level slider bar . The color level slider allows the user to specify a color level as discussed.

The screen shot can include an apply button . Once the user has specified the required parameters and any optional parameters the user clicks the apply button . The server then processes the image in accordance with the user specified parameters.

The terminal can include a processor . The processor can be a general purpose processor configured to execute computer readable instructions operating the terminal and associated peripherals. It will be appreciated that any number of processors can be included in the terminal including specialized processors such as graphics processing units GPU . The processor can also be configured to execute the effects module as discussed below.

The terminal can include a clock . The clock can provide a local time. The clock can be periodically updated from a server in communications with the terminal .

The terminal can include sensors . Sensors can include audio input devices or optical input devices. Audio input devices can include microphones. Optical input devices can include cameras or light sensors. The sensors can be configured to detect appropriate input and convert the input into input signals transmitted to the processor .

The terminal can include a network interface . For example the network interface can communicate with a cellular wireless network a wired network such as Ethernet or a short range wireless network such as Bluetooth or Wi Fi. The terminal can include multiple network interfaces or a network interface configured to interface with multiple networks.

An Ethernet network allows the terminal to communicate when plugged in. The terminal can be assigned an IP address on the wired network. A short range wireless network can be a Wi Fi Wi Bree or Bluetooth network.

The terminal can include an input output interface . The interface can receive user inputs from an input device and convert the user inputs into user commands. For example input devices can include a touch screen display a keypad a microphone an optical device a pointer device a scroll wheel or other input devices.

The interface can also transmit output to an output device in a form accessible to the user . For example output devices can include a touch screen a display screen a speaker an audio out jack an electromechanical motor for providing tactile output or other output devices.

The terminal can include a memory . The memory can be read only or read write persistent or volatile memory accessible to the processor . The memory can store data required by the terminal for operation and applications for execution.

The terminal can store an effects module in the memory for execution. Upon execution the effects module can interact with a server to provide effects to user selected images. For example the effects module can pre process an image by cropping or performing color correction. For example the effects module can interact with the server to provide a user interface to the user .

The server includes a display . The display can be equipment that displays viewable images graphics text and other output generated by the server to a server administrator. For example the display can be a cathode ray tube or a flat panel display such as a TFT LCD. The display includes a display surface circuitry to generate a viewable picture from electronic signals sent by the server and an enclosure or case. The display can interface with an input output interface which converts data from a central processor unit to a format compatible with the display .

The server includes one or more additional output devices . The output device can be any hardware used to communicate outputs to the administrator. For example the output device can include audio speakers and printers or other devices for providing output.

The server includes one or more input devices . The input device can be any hardware used to receive inputs from the administrator. The input device can include keyboards mouse pointer devices microphones scanners video and digital cameras etc.

The server includes an input output interface . The input output interface can include logic and physical ports used to connect and control peripheral devices such as output devices and input devices . For example the input output interface can allow input and output devices and to communicate with the server .

The server includes a network interface . The network interface includes logic and physical ports used to connect to one or more networks. For example the network interface can accept a physical network connection and interface between the network and the workstation by translating communications between the two. Example networks can include Ethernet the Internet or other physical network infrastructure. Alternatively the network interface can be configured to interface with a wireless network. Alternatively the server can include multiple network interfaces for interfacing with multiple networks.

As illustrated the network interface communicates over a network . Alternatively the network interface can communicate over a wired network. It will be appreciated that the server can communicate over any combination of wired wireless or other networks.

The server includes a central processing unit CPU . The CPU can be an integrated circuit configured for mass production and suited for a variety of computing applications. The CPU can sit on a motherboard within the server and control other workstation components. The CPU can communicate with the other components via a bus a physical interchange or other communication channel.

The server includes memory . The memory can include volatile and non volatile storage memory accessible to the CPU . The memory can be random access and provide fast access for graphics related or other calculations. In an alternative embodiment the CPU can include on board cache memory for faster performance.

The server includes mass storage . The mass storage can be volatile or non volatile storage configured to store large amounts of data. The mass storage can be accessible to the CPU via a bus a physical interchange or other communication channel. For example the mass storage can be a hard drive a RAID array flash memory CD ROMs DVDs HD DVD or Blu Ray mediums.

The server can execute an effect module stored in memory . The cartoon generation module can process images in accordance with predefined algorithms and user specified parameters as discussed above. The processed image can be provided to the user over the network .

It will be understood that each block of the flowchart illustrations discussed above and combinations of blocks in the flowchart illustrations above can be implemented by computer program instructions. These program instructions may be provided to a processor to produce a machine such that the instructions which execute on the processor create means for implementing the actions specified in the flowchart block or blocks. The computer program instructions may be executed by a processor to cause a series of operational steps to be performed by the processor to produce a computer implemented process such that the instructions which execute on the processor provide steps for implementing the actions specified in the flowchart block or blocks.

Accordingly blocks of the flowchart illustration support combinations of means for performing the specified actions combinations of steps for performing the specified actions and program instruction means for performing the specified actions. It will also be understood that each block of the flowchart illustration and combinations of blocks in the flowchart illustration can be implemented by special purpose hardware based systems which perform the specified actions or steps or combinations of special purpose hardware and computer instructions.

As discussed above one embodiment of the present invention can be a method for a method for generating user accessible effects. The method includes receiving a library of operators each operator including a set of operations performable on an image. The method includes interacting with a designer via a node based graphical user interface to receive an effect definition wherein the effect definition defines a set of operators to be executed on an image and a set of parameters associated with each operator. The method includes responsive to a change of the effect definition previewing a result of the effect definition applied to a developer specified image. The method includes saving the effect definition to an accessible memory. The method includes uploading the effect definition to a server for compilation into a script module for execution responsive to a user request. The method includes receiving a template effect definition wherein the template effect definition is displayed in the node based graphical user interface for editing. The method includes receiving a graphical user interface executable with the library of operators and the template effect definition. New operators can be coded by developers and compiled into the library of operators. The operators can include at least one of transforming clustering diffusion filtering and thresholding. The server can receive a user specified image to process with the script module. The server can execute the script module on the user specified image and provides a processed image to a user.

Another embodiment of the present invention can be a workstation for generating user accessible effects. The workstation includes a processor. The processor can be configured to receive a library of operators each operator including a set of operations performable on an image. The processor can be configured to interact with a designer via a node based graphical user interface to receive an effect definition wherein the effect definition defines a set of operators to be executed on an image and a set of parameters associated with each operator. The processor can be configured to responsive to a change of the effect definition preview a result of the effect definition applied to a developer specified image. The processor can be configured to save the effect definition to an accessible memory. The processor can be configured to upload the effect definition to a server for compilation into a script module for execution responsive to a user request. The processor can be configured to receive a template effect definition wherein the template effect definition is displayed in the node based graphical user interface for editing. The processor can be configured to receive a graphical user interface executable with the library of operators and the template effect definition. New operators can be coded by developers and compiled into the library of operators. The operators can include at least one of transforming clustering diffusion filtering and thresholding. The server can receive a user specified image to process with the script module. The server can execute the script module on the user specified image and provides a processed image to a user.

Another embodiment of the present invention can be a computer readable storage medium including instructions adapted to execute a method for generating user accessible effects. The method includes receiving a library of operators each operator including a set of operations performable on an image. The method includes interacting with a designer via a node based graphical user interface to receive an effect definition wherein the effect definition defines a set of operators to be executed on an image and a set of parameters associated with each operator. The method includes responsive to a change of the effect definition previewing a result of the effect definition applied to a developer specified image. The method includes saving the effect definition to an accessible memory. The method includes uploading the effect definition to a server for compilation into a script module for execution responsive to a user request. The method includes receiving a template effect definition wherein the template effect definition is displayed in the node based graphical user interface for editing. The method includes receiving a graphical user interface executable with the library of operators and the template effect definition. New operators can be coded by developers and compiled into the library of operators. The operators can include at least one of transforming clustering diffusion filtering and thresholding. The server can receive a user specified image to process with the script module. The server can execute the script module on the user specified image and provides a processed image to a user.

The specific embodiments described in this document represent examples or embodiments of the present invention and are illustrative in nature rather than restrictive. In the above description for purposes of explanation numerous specific details are set forth in order to provide a thorough understanding of the invention. It will be apparent however to one skilled in the art that the invention can be practiced without these specific details.

Reference in the specification to one embodiment or an embodiment or some embodiments means that a particular feature structure or characteristic described in connection with the embodiment is included in at least one embodiment of the present invention. Features and aspects of various embodiments may be integrated into other embodiments and embodiments illustrated in this document may be implemented without all of the features or aspects illustrated or described. It will be appreciated to those skilled in the art that the preceding examples and embodiments are exemplary and not limiting.

While the system apparatus and method have been described in terms of what are presently considered to be the most practical and effective embodiments it is to be understood that the disclosure need not be limited to the disclosed embodiments. It is intended that all permutations enhancements equivalents combinations and improvements thereto that are apparent to those skilled in the art upon a reading of the specification and a study of the drawings are included within the true spirit and scope of the present invention. The scope of the disclosure should thus be accorded the broadest interpretation so as to encompass all such modifications and similar structures. It is therefore intended that the application includes all such modifications permutations and equivalents that fall within the true spirit and scope of the present invention.

