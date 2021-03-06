---

title: Print control method and print control apparatus for controlling printing of structured document
abstract: A print control method causes a printing apparatus to print an image on the basis of a structured document containing a plurality of hierarchical elements. In the print control method, a print preview image and a tree view showing a hierarchy of the elements contained in the structured document are displayed. In the tree view, the elements are displayed in a selectable manner When an instruction to specify an element is input, an updated print preview image including the specified element is displayed. Thus, the user can easily remove unnecessary part of a Web page on a print preview screen and print the resulting Web page.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09141587&OS=09141587&RS=09141587
owner: Canon Kabushiki Kaisha
number: 09141587
owner_city: Tokyo
owner_country: JP
publication_date: 20090508
---
This application is a National Stage filing of PCT Application No. PCT JP2009 002014 filed on May 8 2009 which claims priority from Japan Patent Application No. 2008 130763 filed on May 19 2008 the disclosures of each of which are hereby incorporated by reference herein in their entirety.

The present invention relates to print control methods for controlling printing of a structured document. In particular the present invention relates to a print control method and a print control apparatus for selecting one or more elements contained in a structured document and causing a printing apparatus to print the selected one or more elements.

In recent years it has been possible to obtain various kinds of information by accessing Web pages on the Internet. These Web pages are structured documents written in a structured language such as hyper text markup language HTML or extensible hyper text markup language XHTML . The Web pages can be displayed on a display in a viewable manner by software called browser supporting such a structured document. Typically a Web page to be printed is displayed on a display by a browser and the displayed page is printed. Japanese Patent No. 3588337 describes a method in which within a Web page displayed by a browser an area selected by the user with a pointing device e.g. mouse is printed.

However in the known method described above no consideration is given to cases where a plurality of parts the user wants to print are scattered within the Web page. Therefore to print the Web page except a plurality of unnecessary parts scattered therewithin the user has to edit the Web page and thus has to perform complicated operations.

In view of the problem described above the present invention provides a print control method which allows the user to easily remove unnecessary parts scattered within a Web page and print the resulting Web page.

The present invention provides a print control method in which to print a Web page parts of the Web page can be easily removed and the resulting Web page can be printed.

Specifically the present invention provides a print control method for causing a printing apparatus to print an image on the basis of a structured document containing a plurality of elements. The print control method includes causing a display device to display a first image including elements contained in a structured document in such a manner that elements included in the first image and being selectable as a print target are displayed separately from each other determining when an instruction to select one or more elements in the first image is input the one or more elements selected in accordance with the instruction as elements to be printed and causing the printing apparatus to print an image where the selected elements in the displayed first image are arranged and the one or more not selected elements are omitted.

Hereinafter exemplary embodiments of the present invention will be described in detail with reference to the attached drawings. The following exemplary embodiments are not intended to limit the scope of the present invention. At the same time not all combinations of features explained in the exemplary embodiments are essential to solving means of the present invention.

A USB interface is an interface to which a USB cable is connected. Data communication with the printer is made via the USB cable. Alternatively data communication with the printer may be made via a small computer system interface SCSI or wirelessly.

A display device includes a cathode ray tube CRT or a liquid crystal display and a graphics controller. The display device displays Web pages downloaded from servers a print preview image a graphical user interface GUI etc.

An input device is operated by the user to give various instructions to the PC . Examples of the input device include a mouse and a keyboard. The PC inputs various instructions from the user and performs various control operations in accordance with the instructions.

A local area network LAN interface is an interface to which a LAN cable is connected. Data communication with the external WWW servers is made via a router not shown and the Internet . Alternatively this data communication may be made wirelessly for example via an interface supporting wireless communication.

The PC illustrated in is a so call notebook PC which combines the display device and the input device with a controller including the CPU and the RAM . However the present invention is not limited to this. The present invention may be applied to a so called desktop PC which includes a controller and is externally provided with a display device and an input device.

The programs illustrated in are stored in the ROM and the hard disk illustrated in . The CPU executes the programs using the RAM as a temporary storage area.

A browser is an application for displaying Web pages. The browser downloads Web pages from the WWW servers to the hard disk and displays them on the display device . Web pages are structured documents written in HTML or XHTML. The Web pages are composed of text and images called elements which are written using tags. Additionally there is a separate file called cascading style sheet hereinafter abbreviated as CSS which defines display styles of the elements and is specified within a structured document.

A structured document has a hierarchical structure. Elements constituting the hierarchical structure have hierarchical relationships with one another.

Referring back to a print module is a module for printing structured documents. The print module is plug in software called by the browser . When the user instructs the browser to print a structured document or display a print preview of the structured document the print module is executed and reads out the structured document through the browser . This structured document is first analyzed by a document analyzing unit of the print module .

The document analyzing unit analyzes elements of a Web page the elements being within the structured document and creates hierarchically structured data called document object model DOM tree in the RAM .

From the elements of the DOM tree the document analyzing unit removes those not reflected in printing and creates a print target element tree in the RAM . Examples of the elements not reflected in printing include an element representing a Web page title.

An element selecting unit reads from the RAM the print target element tree created by the document analyzing unit . Then the element selecting unit performs display control such that the display device displays an element tree view as a GUI. The user uses a mouse a keyboard or the like to give an instruction to select each item of the element tree view. Thus an element to be printed is specified.

A print layout unit determines a print layout of elements selected by the user and included in the print target element tree. The print layout is determined in accordance with attributes of the elements analyzed by the document analyzing unit arrangement information defined in the CSS file and print settings. The print settings include information such as paper size resolution and printable area and are obtained from a printer driver through an OS . The arrangement information indicating the determined layout may be stored in the RAM .

In accordance with the layout determined by the print layout unit a print preview unit generates a print preview image in which the elements of the print target element tree are arranged and performs display control to display the print preview image on the display device .

When an instruction to start printing is input from the user a print processing unit executes drawing processing for the printer driver through the OS in accordance with the element arrangement information indicating the layout determined by the print layout unit .

For the print module the OS provides an application programming interface API for transmitting and receiving print setting data to and from the printer driver and also provides an API for performing drawing processing. Although not described in detail here the OS includes various control software programs such as a spooler system that manages print jobs and a port monitor that outputs a printer command to a port.

The printer driver generates print data in accordance with the drawing processing executed by the print processing unit converts the print data into a printer command and transmits the printer command through the OS to the printer .

When the print control described above is performed the printer receives the print command and performs a print operation. Thus an image containing elements arranged in the layout indicated by the above described arrangement information is recorded on a sheet.

The DOM tree of has as a root node a node representing the entire document. The node has a node and an node as child nodes. The node has a node as a child node.

Each element node holds data such as a pointer to a parent element node a pointer to a brother element node a pointer to a child element node list attribute information and text information.

A display state and arrangement information of each element are defined in the CSS file and are stored in the RAM as information about each element node of the DOM tree. Examples of the information about each element node include font type font size font color and display position of the element.

When a Print Preview button of the browser is pressed the print module for printing a structured document is activated and processing of the document analyzing unit starts step S . The document analyzing unit reads a specified Web page and a CSS file through the browser analyzes the Web page creates a DOM tree such as that illustrated in and stores the DOM tree in the RAM step S .

From element nodes within the DOM tree the document analyzing unit removes those not reflected in printing and specifies print target elements step S . Specifically in the node a node a node and a node are removed from the DOM tree as they are elements not reflected in printing.

Then last the document analyzing unit creates a print target element tree with the element nodes specified in step S and stores the print target element tree in the RAM step S . The processing thus ends step S .

In accordance with the processing procedure described above the document analyzing unit creates a print target element tree.

As illustrated the browser first displays a Web page on the screen. When the Print Preview button arranged within the displayed screen is clicked the browser calls the print module using a structured document file corresponding to the displayed Web page as a parameter. The print module analyzes the structured document file corresponding to the displayed Web page and displays a print preview screen .

An element tree view of is a representation of a print target element tree displayed by the element selecting unit . The element tree view is composed of user selectable items. The items of the element tree view correspond to respective elements of a structured document. A character string contained in each element of the structured document is displayed as an item. Therefore by comparing character strings displayed as items with character strings contained in the elements of the structured document the user can recognize which item corresponds to which element in a print preview image. If an element contains no character string a character string contained in its child element may be displayed as an item.

Each item in the element tree view has a corresponding check box. On the basis of whether the check box is checked the element selecting unit of determines whether the corresponding element is selected by the user. Therefore when the user changes the checked state the print target element tree is updated so that a new print target element tree is created with elements corresponding to checked items.

By checking a check box with the mouse or keyboard the user can select an element corresponding to the check box as a print target. Conversely by deselecting a check box the user can remove an element corresponding to the check box from a list of print targets. In particular by changing the checked state of a higher level element in the print target element tree determinations for a plurality of elements including lower level elements can be made as to whether they are print targets.

A print preview image generated by the print preview unit of is displayed in a print preview display section . Since the print preview image is generated on the basis of the print target element tree only elements selected in the element tree view by the user are arranged in the print preview image. Therefore by checking check boxes in the element tree view the user can not only select elements to be printed but can also view a print preview of the selected elements.

On the print preview screen a Start Printing button is used to give an instruction to start printing. Clicking the Start Printing button causes the printer to print an image displayed in the print preview display section on a recording medium such as a sheet.

A Cancel button is used to give an instruction to stop printing. A print settings menu is a drop down menu for making various print settings. The user uses the print settings menu to specify paper size print quality margin etc.

A cursor appears on the print preview screen. When the user operates the mouse the cursor moves on the screen accordingly. In the cursor is placed on an item which is focused and highlighted. A rectangular area within the print preview display section is an element corresponding to the item . When the item is focused the display color of the rectangular area is changed. As illustrated the rectangular area is displayed translucently in a color different from that of the other area. This allows the user to easily recognize which part of the print preview image corresponds to the element corresponding to the item . Alternatively the change in display color of the rectangular area may take place when the user clicks the item on which the cursor is placed.

When the Print Preview button is pressed only items corresponding to higher level elements in the print target element tree may be displayed in the element tree view . In this case when the user gives an instruction to display lower level elements the displayed items in the element tree view may be expanded to display items corresponding to the lower level elements.

When the cursor appears in the print preview display section and the user performs a mouse drag operation a position at which the drag operation has been performed is detected. Then a rectangular area at the detected position is displayed translucently in a color different from that of the other area.

On the basis of the detected position and information indicating the layout of the print preview image such as arrangement information stored in the CSS and the RAM it is possible to determine which item in the element tree view corresponds to an element selected by the user. In an item corresponding to the rectangular area is highlighted. This allows the user to easily recognize which item in the element tree view corresponds to an area of the print preview image and thus facilitates selection of an item.

Thus when selection of elements to be printed is changed the element selecting unit of updates the print target element tree and the print layout unit changes the layout of the print preview image.

Arrangement information indicating the updated layout may be stored in the RAM by the print layout unit . In this case each time the layout of the print preview image is updated arrangement information indicating the layout is updated.

As described above in the present exemplary embodiment elements of a structured document are displayed as an element tree view so that the user can select elements to be printed. Therefore the user can easily select and print necessary part of the Web page.

In the present exemplary embodiment described above each check box in the element tree view allows selection of an area to be printed. Alternatively an area selected by a drag operation on the print preview image by the user may be removed from the print preview image. This is advantageous in that the step of deselecting a check box can be skipped.

In the present exemplary embodiment described above character strings contained in respective elements are displayed as items in the element tree view . Alternatively reduced size images corresponding to respective elements may be used to create an element tree view.

Although processing is performed on the PC in the present exemplary embodiment described above the present invention is not limited to this. That is processing according to an exemplary embodiment of the present invention may be performed on a printer so that a print preview may be displayed on a display screen of the printer.

In the above explanation an element tree view is created and displayed for a print preview for one page. However the present invention is not limited to this. illustrates an example of an element tree view representing a print target element tree created for a plurality of pages to be printed.

Referring to four pages and to be printed are displayed in the print preview display section and an element tree view contains items Page Page Page and Page corresponding to the four pages and respectively. Each of these items has one or more sub items corresponding to one or more elements contained in each page. The element tree view is thus structured.

Another exemplary embodiment of the present invention will now be described. The present exemplary embodiment differs from the above described exemplary embodiments only in that the print layout unit of does not display a tree view but displays a layout view showing positions of elements in a print preview image. In the present exemplary embodiment a configuration and processing identical to those of the above described exemplary embodiments will not be described.

The selected element frame corresponds to each element in the print target element tree. An element selected as a print target is surrounded by the selected element frame whereas an element not selected as a print target is not surrounded by the selected element frame .

A click operation on or inside the selected element frame selects and deselects an element surrounded by the selected element frame . A double click operation removes the selected element frame divides the element into child elements and displays individual selected element frames for all the child elements.

An Enlarge button and a Reduce button on the print preview screen are used to enlarge and reduce respectively the display within the layout view . The display within the layout view is enlarged or reduced with reference to the center of the layout view .

If the thumbnail of the Web page does not fit in the layout view at least one of a vertical scroll bar and a horizontal scroll bar appears. The vertical scroll bar and the horizontal scroll bar are moved to allow the user to view the entire thumbnail of the Web page.

A print preview display section displays on the GUI a print preview image generated by the print preview unit . The print preview display section displays a print preview where only elements selected on the layout view are arranged in a print layout.

On the print preview screen a Start Printing button and a Cancel button are buttons used to start and stop printing respectively and a Print Settings menu is a drop down menu for making various settings for printing. The user uses the Print Settings menu to specify paper size print quality margin etc.

In the layout view of child elements and are all selected as print targets. illustrates a GUI screen displayed after some child elements within the layout view are deselected by a mouse click.

In the layout view of the child elements and which are deselected are not surrounded by selected element frames and are displayed with translucent shading. The deselected child elements and are not displayed in the print preview display section and other elements are slid upward and rearranged.

As described above by operating the element selecting unit and the print preview unit through GUI operation and the print layout unit the user can easily select and deselect elements to be printed.

A storage medium in which software program code for realizing the functions of the above described exemplary embodiments is stored may be supplied to a system or an apparatus. The present invention can be provided when a computer or CPU or micro processing unit MPU of the system or apparatus reads and executes the program code stored in the storage medium. In this case the program code read out of the storage medium realizes the functions according to the above described exemplary embodiments. Therefore the storage medium storing the program code constitutes the present invention.

Examples of the storage medium for supplying the program code include a flexible disk a hard disk an optical disk a magneto optical disk a compact disk read only memory CD ROM a CD recordable CD R a magnetic tape a non volatile memory card a ROM and a digital versatile disk DVD .

As described above the functions of the above described exemplary embodiments are realized by executing the program code read out by the computer. Additionally for example in accordance with an instruction of the program code an OS running on the computer may perform all or part of the actual processing so that the functions according to the above described exemplary embodiments are realized by this processing.

Furthermore after the program code is read out of the storage medium it can be written to a function expansion board inserted in the computer or to a memory provided in a function expansion unit connected to the computer. In this case in accordance with an instruction of the program code a CPU or the like mounted on the function expansion board or function expansion unit may perform all or part of the actual processing so that the functions of the above described exemplary embodiments are realized by this processing.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all such modifications and equivalent structures and functions.

This application claims the benefit of Japanese Patent Application No. 2008 130763 filed May 19 2008 which is hereby incorporated by reference herein in its entirety.

