---

title: Systems and methods for imaging a three-dimensional volume of geometrically irregular grid data representing a grid volume
abstract: Systems and methods for imaging a 3D volume of geometrically irregular grid data. The systems and methods utilize various types of probes and displays to render the geometrically irregular grid data, in real-time, and analyze the geometrically irregular grid data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08736600&OS=08736600&RS=08736600
owner: Landmark Graphics Corporation
number: 08736600
owner_city: Houston
owner_country: US
publication_date: 20090605
---
The priority of U.S. Provisional Patent Application No. 61 059 716 filed on Jun. 6 2008 is hereby claimed and the specification thereof is incorporated herein by reference.

The present invention relates generally to systems and methods for imaging a three dimensional 3D volume of geometrically irregular grid data representing a grid volume. More particularly the present invention relates to imaging geometrically irregular grid data in real time using various types of probes and corresponding displays.

Typical commercialized petroleum reservoir visualization software helps petroleum and reservoir engineers and geoscientists see the results from static or dynamic simulations and visually compare iterative what if scenarios. Many reservoir models are often described as a disconnected curvilinear grid volume also called a 3D grid where each grid cell has clearly defined hexahedronal geometry. The software shows different views of the reservoir with particular attributes e.g. gas saturation of the reservoir. The edges top and bottom of the reservoir can be seen by rotating the view.

Visualization can be used at four different points in the reservoir characterization and simulation process 1 after gridding 2 after initialization 3 during simulation and 4 after simulation. Visualization software typically allows the representation of any simulation attribute instant switching between attributes and the ability to set data thresholds with unique displays of cells that are restricted to specified data ranges. A visualization model may include a single layer or multi layer views wherein cells are stripped away to reveal the inside of the model. They can also be constructed to show a full display of corner points and local refinement for grid volumes. The traditional approach to setting up a modeling framework is a step wise process not done in real time that employs two dimensional 2D interface dialog boxes with input fields and progress bars.

Geoscientists examine a variety of data types in the effort to find oil or gas. Seismic data is generally used to identify continuous reflections representing horizons and discontinuities representing faults or other structural components that form the structural framework of reservoirs containing hydrocarbons. This data type provides high resolution horizontal information but lacks vertical detail. During oil and gas exploration well data provides petrophysical and geological information from wire line logs and cores. This well data contains high resolution vertical information but lacks horizontal detail between wells. Sophisticated earth modeling tools integrate information from these two data types thus optimizing both horizontal and vertical resolution. The result is a static model that can be used to build reservoir models to predict the oil and or gas fluid flow and facilitate hydrocarbon production planning.

Visualization shows simulation effects on a specific area of the reservoir represented in a model through the use of 3D graphics objects. Simulation attributes display as color on the graphics objects and represent reservoir structure. As a result physical changes in the reservoir such as gas cap movement or pressure changes can be easily evaluated. The ability to visualize a simulation model at any angle during the course of the simulation improves reservoir understanding.

A 3D reservoir model may be presented as hexahedral grid cells which can be topologically structured or unstructured and geometrically regular or irregular. Curvilinear grid volumes which are topologically structured and geometrically irregular are more typical in reservoirs and are therefore of particular interest. A 3D grid may be defined as cell where v v. . . and vare eight vertices for the cell and a a. . . and aare attributes. 3D grids are I layers thick J cells wide K cells deep which contain cells with coordinates I J K referred to as grid coordinates. Grid Coordinates I J K are typically used in an index domain while Cartesian world coordinates x y z are typically used in a sampling domain.

Some commercial applications and research can visualize 3D grids and provide basic 3D scene interactive manipulations such as rotation and zoom capabilities. However 2D menus are used to define particular features such as I J or K layers. For large or complicated volumes image generation requires so much time that the software must display a progress bar. Although users can be trained to set parameters in 2D menus while working in 3D they may become frustrated by this awkward interaction.

As referenced above a 3D reservoir model is either topologically structured or unstructured and volumes are geometrically regular or irregular. Unstructured volumes can easily be resampled to a regular structured volume using a rendering algorithm. Research for unstructured volume visualization includes the widely used Projected Tetrahedral technique. Many other extended and enhanced algorithms have also been published. Another algorithm used for visualizing geoscience data is incremental slicing which was first introduced by Yagel et al. in IEEE Visualization 1996 pp. 55 62. The basic idea behind this algorithm is to slice the whole grid volume along the viewing direction and render the slices from back to front. For surface volume rendering the well known Marching Cubes algorithm can be used for rendering both regular and irregular grid cells. The challenge of volume visualization however lies in determining which algorithm best fits a particular domain and task.

Volume roaming resizing or moving a region is a common visualization technique used to focus on a dynamic subvolume of the entire data set in several oil and gas applications. GeoProbe which is a commercial software package marketed by Landmark Graphics Corporation for use in the oil and gas industry employs this basic technique using a sampling probe. The Geoprobe sampling probe is described in U.S. Pat. No. 6 765 570 which is assigned to Landmark Graphics Corporation and is incorporated herein by reference. The sampling probe described in U.S. Pat. No. 6 765 570 however only renders structured data voxels in real time. In other words the sampling probe does not address the need to render unstructured grids much less geometrically irregular grid data in real time.

Although other publications e.g. Speray and Kennon in Volume Probes Interactive Data Exploration on Arbitrary Grids Computer Graphics Vol. 24 No. 5 November 1995 pp. 5 12 describe a probe none appear capable of rendering geometrically irregular grid data in real time.

There is therefore a need for imaging rendering 3D grids of geometrically irregular grid data in real time.

The present invention meets the above needs and overcomes one or more deficiencies in the prior art by providing systems and methods for imaging 3D grids of geometrically irregular grid data in real time.

In one embodiment the present invention includes a method for imaging a three dimensional volume of geometrically irregular grid data representing a grid volume using a computer processor which comprises i selecting a grid probe within the grid volume the grid probe defined by a bounding box in a sampling domain the grid volume comprising multiple cells and the grid data comprising a normal vector and a geometry for each face of each cell split flag data for each cell an attribute for each cell and an attribute data value for each cell wherein the split flag data comprises data representing each face of a respective cell and its position relative to a face of another cell ii mapping extents of the bounding box from the sampling domain to an index domain iii rendering an image of the grid probe within the grid volume the image comprising the grid data only within at least a portion of the extents of the bounding box and iv repeating the rendering step in response to movement of the grid probe within the grid volume so that as the grid probe moves the image of the grid probe is redrawn at a rate sufficiently fast to be perceived as moving in real time.

In another embodiment the present invention includes a non transitory program carrier device tangibly carrying computer executable instructions for imaging a three dimensional volume of geometrically irregular grid data representing a grid volume. The instructions are executable to implement i selecting a grid probe within the grid volume the grid probe defined by a bounding box in a sampling domain the grid volume comprising multiple cells and the grid data comprising a normal vector and a geometry for each face of each cell split flag data for each cell an attribute for each cell and an attribute data value for each cell wherein the split flag data comprises data representing each face of a respective cell and its position relative to a face of another cell ii mapping extents of the bounding box from the sampling domain to an index domain iii rendering an image of the grid probe within the grid volume the image comprising the grid data only within at least a portion of the extents of the bounding box and iv repeating the rendering step in response to movement of the grid probe within the grid volume so that as the grid probe moves the image of the grid probe is redrawn at a rate sufficiently fast to be perceived as moving in real time.

Additional aspects advantages and embodiments of the invention will become apparent to those skilled in the art from the following description of the various embodiments and related drawings.

The subject matter of the present invention is described with specificity however the description itself is not intended to limit the scope of the invention. The subject matter thus might also be embodied in other ways to include different steps or combinations of steps similar to the ones described herein in conjunction with other present or future technologies. Moreover although the term step may be used herein to describe different elements of methods employed the term should not be interpreted as implying any particular order among or between various steps herein disclosed unless otherwise expressly limited by the description to a particular order. While the following description refers to the oil and gas industry the systems and methods of the present invention are not limited thereto and may also be applied to other industries to achieve similar results.

The need for real time displays in today s modeling world is critical waiting even a single minute can often seem painful and frustrating. Therefore the visualization design goal is to render large 3D grids of geometrically irregular grid data representing a grid volume responsive to input at rendering rates sufficiently fast to be perceived in real time. To penetrate and analyze such data in real time a number of visualization techniques are addressed herein. In order to fully understand these techniques it is necessary to describe some details around 3D grids and their topology.

Referring now to a layer of geometrically irregular grid data from a 3D grid is illustrated. The layer may be used to map grid data from a grid volume onto a probe. To specify the continuity of adjacent cells a byte representing multiple split flags is used. Six of the bits in a byte are used to indicate whether the cell split occurred left right up down near or far relative to adjacent cells. The seventh bit is used to specify a dead cell. The eighth bit is used for inactive cells. Inactive cells are not dead but are invisible for particular probes. The data representing each bit split flag may be referred to collectively as split flag data.

Cell has coordinates of 1 1 1 . The only splits relative to cell occurred left and up which are shown by no cell to the left or above the cell .

Cells that do not exist as in cell are referred to as dead cells and are not displayed. The cells adjacent to the dead cells possibly represent geological discontinuities such as faults other structural features or stratigraphic changes. Geological or petrophysical attributes are displayed as color on the cells. The shading and color must be per cell but cannot be per vertex. Any form of interpolation of color or vertex is not desired because petroleum geoscientists and engineers want to see and understand the attribute magnitude at each cell. Each cell therefore includes an attribute and a corresponding attribute data value. In addition each face of each cell represents a particular geometry and includes a normal vector that controls the shading for that face. Thus each cell includes grid data associated therewith that comprises a normal vector and a geometry for each face of the cell split flag data an attribute and its corresponding data value. The attribute and its corresponding data value the geometry and the normal vector are commonly referred to as 3D graphics quads.

Cell has coordinates of 1 4 1 . The splits relative to cell occurred left and down which are shown by no cell to the left or below the cell .

Cell has coordinates of 1 4 5 . The splits relative to cell occurred right and down which are shown by no cell to the right or below the cell .

Cell has coordinates of 1 4 6 . The splits relative to cell occurred left right and down which are shown by no cell to the left right or below the cell .

Cell has coordinates of 1 1 6 . The splits relative to cell occurred left right and up which are shown by no cell to the left right or above the cell .

Because interpolation of vertices and colors should be avoided polygon reduction e.g. using a polygon for the faces of cells on the same plane can not be applied. These requirements reaffirm the need for the different types of probes and displays provided herein by the present invention.

The present invention reduces image generation rendering time by use of a probe based interface where users can identify the appropriate parameter selection without the need of a 2D interface. A probe based interface like the GeoProbe sampling probe renders a dynamic subset of the entire data volume which may be used to focus on a region of interest. The present invention extends the probe concept to interface with grid data including split flag data from a grid volume comprising multiple cells. As used herein the term probe refers to a grid probe which may include for example a Box Probe a Quad Probe a Cut Probe a Slice Probe and a Filter Probe.

Referring now to an image illustrates Local Grid Refinement LGR which is applied to add detail where it is justified by data availability and to keep coarse resolution where less data is available. To handle LGR each probe contains multiple display objects and each display object is connected with one LGR grid. A parent child relationship between grid cells is passed into the display object. According to the parent range information a child queries its own range from grid data retrieves a sub grid and then builds geometry for a particular display. There are 18 LGR grid cells in the image .

Different types of visualization displays may be used in connection with certain probes which include for example a ShellDisplay a PlaneDisplay a CellDisplay and a FilterDisplay. Each type of display may be used to examine different geological layering the distribution of geological faces and their internal petrophysical properties such as for example outside geometry ShellDisplay layers or cross sections PlaneDisplay distribution of flow units or geobodies FilterDisplay or the internal grid cell geometry CellDisplay . Each type of display may therefore be used to validate or identify potential problems using the probe thereby eliminating the need to stop initiate a new set of commands and then wait for a particular display to render. The present invention therefore provides interactive real time images that respond to changes in the probe size shape and location.

The present invention may be implemented through a computer executable program of instructions such as program modules generally referred to as software applications or application programs executed by a computer. The software may include for example routines programs objects components and data structures that perform particular tasks or implement particular abstract data types. The software forms an interface to allow a computer to react according to a source of input Picasso which is a commercial software application marketed by Landmark Graphics Corporation may be used as an interface application to implement the present invention. The software may also cooperate with other code segments to initiate a variety of tasks in response to data received in conjunction with the source of the received data. The software may be stored and or carried on any variety of memory media such as CD ROM magnetic disk bubble memory and semiconductor memory e.g. various types of RAM or ROM . Furthermore the software and its results may be transmitted over a variety of carrier media such as optical fiber metallic wire free space and or through any of a variety of networks such as the Internet.

Moreover those skilled in the art will appreciate that the invention may be practiced with a variety of computer system configurations including hand held devices multiprocessor systems microprocessor based or programmable consumer electronics minicomputers mainframe computers and the like. Any number of computer systems and computer networks are acceptable for use with the present invention. The invention may be practiced in distributed computing environments where tasks are performed by remote processing devices that are linked through a communications network. In a distributed computing environment program modules may be located in both local and remote computer storage media including memory storage devices. The present invention may therefore be implemented in connection with various hardware software or a combination thereof in a computer system or other processing system.

Referring now to a block diagram of a system for implementing the present invention on a computer is illustrated. The system includes a computing unit sometimes referred to a computing system which contains memory application programs a client interface and a processing unit. The computing unit is only one example of a suitable computing environment and is not intended to suggest any limitation as to the scope of use or functionality of the invention.

The memory primarily stores the application programs which may also be described as program modules containing computer executable instructions executed by the computing unit for implementing the methods described herein and illustrated in . The memory therefore includes a visualization module referred to as the GridProbe Module in which enables the methods illustrated and described in reference to . The GridProbe Module may also interact with Picasso and other related software applications as further described in reference to .

Although the computing unit is shown as having a generalized memory the computing unit typically includes a variety of computer readable media. By way of example and not limitation computer readable media may comprise computer storage media and communication media. The computing system memory may include computer storage media in the form of volatile and or nonvolatile memory such as a read only memory ROM and random access memory RAM . A basic input output system BIOS containing the basic routines that help to transfer information between elements within the computing unit such as during start up is typically stored in ROM. The RAM typically contains data and or program modules that are immediately accessible to and or presently being operated on by the processing unit. By way of example and not limitation the computing unit includes an operating system application programs other program modules and program data.

The components shown in the memory may also be included in other removable nonremovable volatile nonvolatile computer storage media. For example only a hard disk drive may read from or write to nonremovable nonvolatile magnetic media a magnetic disk drive may read from or write to a removable non volatile magnetic disk and an optical disk drive may read from or write to a removable nonvolatile optical disk such as a CD ROM or other optical media. Other removable non removable volatile non volatile computer storage media that can be used in the exemplary operating environment may include but are not limited to magnetic tape cassettes flash memory cards digital versatile disks digital video tape solid state RAM solid state ROM and the like. The drives and their associated computer storage media discussed above provide storage of computer readable instructions data structures program modules and other data for the computing unit.

A client may enter commands and information into the computing unit through the client interface which may be input devices such as a keyboard and pointing device commonly referred to as a mouse trackball or touch pad. Input devices may include a microphone joystick satellite dish scanner or the like.

These and other input devices are often connected to the processing unit through the client interface that is coupled to a system bus but may be connected by other interface and bus structures such as a parallel port or a universal serial bus USB . A monitor or other type of display device may be connected to the system bus via an interface such as a video interface. In addition to the monitor computers may also include other peripheral output devices such as speakers and printer which may be connected through an output peripheral interface.

Although many other internal components of the computing unit are not shown those of ordinary skill in the art will appreciate that such components and their interconnection are well known.

Referring now to a block diagram of a program for implementing the present invention on software is illustrated.

The present invention may be implemented using hardware software or a combination thereof and may be implemented in a computer system or other processing system. One embodiment of a software or program structure for implementing the present invention is shown in . At the base of program structure is an operating system . Suitable operating systems include for example the UNIX operating system or Windows NT from Microsoft Corporation or other operating systems as would be apparent to one of skill in the relevant art.

Windowing software overlays operating system . Windowing software is used to provide various menus and windows to facilitate interaction with the user and to obtain user input and instructions. Windowing software can include for example Microsoft Windows X Window System registered trademark of Massachusetts Institute of Technology and MOTIF registered trademark of Open Software Foundation Inc. . As would be readily apparent to one of skill in the relevant art other menu and windowing software could also be used.

A 3D graphics library overlays Windowing software . The 3D graphics library is an application programming interface API for 3D computer graphics. The functions performed by 3D graphics library include for example geometric and raster primitives RGBA or color index mode display list or immediate mode viewing and modeling transformations lighting and shading hidden surface removal alpha blending translucency anti aliasing texture mapping atmospheric effects fog smoke haze feedback and selection stencil planes and accumulation buffer.

A particularly preferred 3D graphics library is OpenGL . The OpenGL API is a well known multi platform industry standard that is hardware window and operating system independent. OpenGL is designed to be callable from C C FORTRAN Ada and Java programming languages. OpenGL performs each of the functions listed above for 3D graphics library . Some commands in OpenGL specify geometric objects to be drawn and others control how the objects are handled. All elements of the OpenGL state even the contents of the texture memory and the frame buffer can be obtained by a client application using OpenGL . OpenGL and the client application may operate on the same or different machines because OpenGL is network transparent. OpenGL is described in more detail in the OpenGL Programming Guide ISBN 0 201 63274 8 and the OpenGL Reference Manual ISBN 0 201 63276 4 the entirety of both of which are incorporated herein by reference.

3D graphics utilities overlay the 3D graphics library . The 3D graphics utilities is an API for creating real time multi processed 3D visual simulation graphics applications. The 3D graphics utilities provide functions that bundle together graphics library state control functions such as lighting materials texture and transparency. These functions track state and the creation of display lists that can be rendered later. A particularly preferred set of 3D graphics utilities is offered in Picasso.

A GridProbe program overlays 3D graphics utilities and the 3D graphics library . The GridProbe program interacts with and uses the functions carried out by each of the 3D graphics utilities the 3D graphics library the windowing software and the operating system in a manner known to one of skill in the relevant art.

The GridProbe program of the present invention is preferably written in an object oriented programming language to allow the creation and use of objects and object functionality. A particularly preferred object oriented programming language is Java . In carrying out the present invention the GridProbe program creates one or more probe objects. As noted above the probe objects created and used by the GridProbe program are also referred to herein as grid probes or probes. GridProbe program manipulates the probe objects so that they have the following attributes.

A probe corresponds to a sub volume of a larger grid volume. Particularly a probe defines a sub set that is less than the complete data set of cells for a grid volume. A probe could be configured to be equal to or coextensive with the complete data set of cells for a grid volume but the functionality of the present invention is best carried out when the probe corresponds to a sub volume and defines a sub set that is less than the complete data set of cells for a grid volume.

By using probes that are a sub volume of the larger grid volume the quantity of data that must be processed and re drawn for each frame of an image is dramatically reduced thereby increasing the speed with which the image can be re drawn. The volume of a three dimensional cube is proportional to the third power or cube of the dimensions of the three dimensional cube. Likewise the quantity of data in a grid volume is proportional to the third power or cube of its size. Therefore the quantity of data in a sub volume of a larger grid volume will be proportional to the cubed root of the quantity of data in the larger grid volume. As such the quantity of data in a probe of the present invention may be proportional to the cubed root of the quantity of data in the grid volume of which it is a sub volume. By only having to process the sub set of data that relates to the sub volume of the probe the present invention can re draw an image in response to user input at a rate sufficiently fast that the user perceives an instantaneous or real time change in the image without perceptible delay or lag. In other words an image that is rendered at a rate of at least 10 frames per second.

The probes of the present invention can be interactively changed in shape and or size and interactively moved within the larger grid volume. The outside geometry or surfaces of a probe can be interactively drawn while the probe is being changed in shape and or size or while the probe is being moved. As a result the internal structures or features of the probe may be revealed.

A probe can be used to cut into another probe and the intersection of the two probes can be imaged. A probe can also be used to filter data in accordance with filter criteria representing an attribute data range.

The 3D graphics utilities include a User Interface Module UIM a Graphics Processing Module GPM and a Volume Sampling Module VSM . The GridProbe program includes a GridProbe Module . UIM and GPM communicate via a bi directional pathway . UIM sends instructions and requests to VSM through GPM and GridProbe Module via bi directional pathways . UIM interacts with Grid Volume through pathway .

Grid data from Grid Volume is transferred to VSM via pathway . VSM transfers data to GPM through GridProbe Module via bi directional pathways . Grid Volume stores the grid data in a manner well known to one of skill in the relevant art which may include grid data representing multiple different volumes.

UIM handles the user interface to receive commands instructions and input data from the user. UIM interfaces with the user through a variety of menus through which the user can select various options and settings either through keyboard selection or through one or more user manipulated input devices such as a mouse or a 3D pointing device. UIM receives user input as the user manipulates the input device to move size shape etc. a grid probe.

UIM inputs the identification of one or more grid volumes from Grid Volume to use for imaging and analysis. When a plurality of grid volumes are used the data value for each of the plurality of grid volumes represents a different physical parameter or attribute for the same geographic space. By way of example a plurality of grid volumes could include a geology volume a temperature volume and a water saturation volume.

UIM inputs information to create one or more probes. Such information may include for example probe type size shape and location. Such information may also include for example the type of display and imaging attributes such as color lighting shading and transparency or opacity . By adjusting opacity as a function of data value certain portions of the grid volume are more transparent thereby allowing a viewer to see through surfaces. As would be readily apparent to one skilled in the art data values with greater opacity less transparency will mask the imaging or display of data values with lower opacity more transparency . Conversely data values will less opacity and greater transparency will permit the imaging or display of data values with greater opacity and lower transparency.

UIM receives input from the user for sizing and shaping the probes. As described in more detail below in a preferred embodiment of the present invention the shape and or size of a probe may be changed by clicking onto manipulators or the probe display and making changes in the dimensions of the probe in one or more directions. A manipulator refers to a designated graphical representation on a surface of the probe which may be used to move reshape or re size the probe. Manipulators may also be used to identify boundaries or extents for creating certain types of probes. A manipulator is preferably displayed in a color that is different from the colors being used to display the features or physical parameters of the grid data. UIM receives input from the user to move the position or location of a probe within the grid volume. In a preferred embodiment a user manipulates a mouse to click onto a manipulator or the probe display and move or re size the probe.

UIM also receives input from the user regarding the content of the displayed image. For example the user can preferably select the content of the displayed image. The content of the displayed image could include only the probe i.e. its intersection with the grid volume. Additionally the probe could be displayed either with or without a bounding box that defines the outer geometry of the probe.

To carry out the foregoing functions UIM sends a request to VSM to load or attach the grid volumes identified by the user. UIM communicates via bi directional pathway with GPM that carries out the display and imaging.

GPM processes data for imaging probes with the color lighting shading transparency and other attributes selected by the user. To do so GPM uses the functions available through 3D graphics library and 3D graphics utilities described above. The user can select through UIM to display only the one or more probes that have been created. Alternatively the user can select to display one or more probes as well as the grid volume outside of the probes i.e. cells within the grid volume that do not intersect any of the probes that are being displayed. Probes that are being displayed may be referred to herein as active probes.

GPM processes the re shaping and move requests that are received by UIM from the user. GPM draws the re shaped probe in accordance with the user selected attributes color lighting shading transparency etc. . As the user inputs a change in shape for a probe the image with selected attributes is re drawn sufficiently fast to be perceived in real time by the user. Similarly GPM draws the probe in the new position or location in accordance with the user selected attributes color lighting shading transparency etc. . As the user moves the probe through the grid volume the image of the probe with selected attributes is re drawn sufficiently fast to be perceived in real time by the user.

To carry out the foregoing functions GPM communicates via bi directional pathway with UIM so that the information requested by the user is imaged or displayed with the selected attributes. GPM obtains the needed data from Grid Volume by sending a data request through the GridProbe Module and the VSM via bi directional pathways .

The GridProbe Module selects bounding box extents in the sampling domain based on input received from UIM through GPM regarding the type of probe and display selected. The GridProbe Module then maps converts the bounding box extents from the sampling domain to the index domain. The GridProbe Module then sends a request to VSM via bi directional pathway for grid data from Grid Volume that corresponds to the selected bounding box extents. The GridProbe Module receives grid data corresponding to the bounding box extents from VSM via bi directional pathway . The GridProbe Module then creates builds the selected probe and display using the grid data from VSM and transmits the selected probe and display to GPM for rendering an image of the selected probe and display.

The primary function of VSM is therefore to extract the appropriate grid data within the bounding box extents from Grid Volume at the request of GridProbe Module . VSM receives requests for grid data from GridProbe Module through bi directional pathway . VSM extracts the required sub grid within the probe bounding box extents from Grid Volume and transfers it to GridProbe Module . VSM also may receive instructions from UIM to load or attach other grid volumes identified by the user.

Referring now to a flow diagram illustrates one embodiment of method for implementing the present invention.

In step the grid volumes to be used in the index domain may be selected using a conventional graphical user interface and input devices. The grid data for the selected grid volumes may be loaded from disc into main memory. Preferably a default probe is created and drawn that is a subvolume of the selected grid volumes. The default probe may for example be a Quad Probe a Box Probe a Cut Probe a Slice Probe or a Filter Probe however is not limited to any particular size or shape.

In step the method determines whether to create a probe based on input received through a conventional graphical user interface. If the method detects that a probe should be created then the method continues to . Otherwise the method may return to step or step .

In step the method determines whether to move the probe based on input received through a conventional graphical user interface. If the method detects that the probe should be moved then the method continues to . Otherwise the method may return to step or step .

In step the method determines whether to re size the probe based on input received through a conventional graphical user interface. If the method detects that the probe should be re sized then the method continues to . Otherwise the method may return to step or step .

The functions determined by steps and may be performed individually or simultaneously. Depending on the input for example one probe can be moved while another probe is re sized. In addition for example one type of probe may be created while another type of prove is moved. While the functions determined by steps and are being carried out the image of the probe is being redrawn sufficiently fast to be perceived in real time. Thus at least one probe has to be created before the functions determined by steps and may be performed. After a probe is created any of the functions determined by steps and may be performed in any order.

Referring now to a continuation of the flow diagram in is illustrated for selecting a probe and display. The steps illustrated in are necessary to determine the preferred type of probe and display before creating the probe according to the methods illustrated in .

In step the method determines whether a Quad Probe is selected based on input received through a conventional graphical user interface. A Quad Probe defines a quad plane bounding box. A quad plane is the region R in the sampling domain where R is a plane such as for example a cross section or a map. An exemplary Quad Probe bounding box is illustrated in . If a Quad Probe was selected then the method continues to steps or which may be processed individually in any order or simultaneously. Otherwise the method may return to steps or .

In step the method determines whether a Box Probe is selected based on input received through a conventional graphical user interface. A Box Probe may be positioned in any geographic coordinate space world space however is preferably expressed as a square or rectangular bounding box with sampling coordinates that are standard x y z units. An exemplary Box Probe bounding box is illustrated in and . If a Box Probe was selected then the method continues to steps or which may be processed individually in any order or simultaneously. Otherwise the method may return to steps or .

In step the method determines whether a Cut Probe is selected based on input received through a conventional graphical user interface. A Cut Probe is similar to a Box Probe because it may be expressed as a square or rectangular outer bounding box and another square or rectangular inner bounding box that defines an area cut out of removed from a portion of the outer bounding box. The inner and outer bounding boxes may be expressed with coordinates that are standard x y z units. An exemplary Cut Probe with inner and outer bounding boxes is illustrated in . If a Cut Probe was selected then the method continues to steps or which may be processed individually in any order or simultaneously. Otherwise the method may return to steps or .

In step the method determines whether a Slice Probe is selected based on input received through a conventional graphical user interface. A Slice Probe is similar to a Box Probe and a Quad Probe because it may be expressed as a square or rectangular bounding box which includes manipulators on the edges of the bounding box and on opposite faces of the bounding box that form the extents of multiple quad plane bounding boxes between the opposing manipulators. An exemplary Slice Probe bounding box with a quad plane bounding box is illustrated in . If a Slice Probe was selected then the method continues to step . Otherwise the method may return to steps or .

In step the method determines whether a Filter Probe is selected based on input received through a conventional graphical user interface. A Filter Probe is similar to a Box Probe because it may be expressed as a square or rectangular bounding box which displays specific cells that contain properties that meet defined conditions. Such conditions for example may represent critical thresholds of key petrophysical properties that are consistent with hydrocarbon production. An exemplary Filter Probe bounding box is illustrated in and B . If a Filter Probe was selected then the method continues to steps or which may be processed individually in any order or simultaneously. Otherwise the method may return to steps or .

As demonstrated herein steps may be processed individually in any order or simultaneously. After a particular type of probe is selected one of the following displays may be selected for the probe.

In step the method determines whether a ShellDisplay is selected based on input received through a conventional graphical user interface. If a ShellDisplay was selected then the method continues to step . Otherwise the method may return to steps or .

In step the method determines whether a CellDisplay is selected based on input received through a conventional graphical user interface. If a CellDisplay was selected then the method continues to step . Otherwise the method may return to steps or .

In step the method determines whether a PlaneDisplay is selected based on input received through a conventional graphical user interface. If a PlaneDisplay was selected then the method continues to step . Otherwise the method may return to steps or .

In step the method determines whether a cell rendered FilterDisplay is selected based on input received through a conventional graphical user interface. If a cell rendered FilterDisplay was selected then the method continues to step . Otherwise the method may return to step .

In step the method determines whether a volume rendered FilterDisplay is selected based on input received through a conventional graphical user interface. If a volume rendered FilterDisplay was selected then the method continues to step . Otherwise the method may return to step .

The use and combination of the foregoing probes and displays enhance the visualization of desired features in a region of interest as demonstrated by the following methods describing each display.

Referring now to a continuation of the flow diagram in is illustrated for creating a probe with a ShellDisplay. As demonstrated by the flow diagram in the ShellDisplay may be used in connection with a Quad Probe a Box Probe or a Cut Probe.

In step a first bounding box for the probe is selected in the sampling domain according to the type of probe selected.

In step the first bounding box extents are converted mapped from the sampling domain to the index domain using the modules and techniques described in reference to .

In step the geometry attribute and split flag data for each cell within the extents of the first bounding box in the index domain are requested from the grid volume using the modules and techniques described in reference to .

In step the method determines whether a Cut Probe was selected. If a Cut Probe was selected then the method continues to step . Otherwise the method continues to step .

In step another bounding box is selected for the Cut Probe and the split flag for each cell in the another bounding box is set to inactive status.

In step the split flag data in the first bounding box is checked for each cell using techniques well known in the art.

In step the method determines if the split flag data for a cell in the first bounding box which is not inactive represents a left right near far up or down split. If the split flag data for the cell represents a left right near far up or down split then the method continues to step . Otherwise the method continues to step to determine whether there are any additional cells in the first bounding box.

In step 3 D graphics quads for the cell are selected using the modules and techniques described in reference to .

In step the method determines whether there are additional cells in the first bounding box using techniques well known in the art. If there are additional cells in the first bounding box then the method returns to step . Otherwise the method continues to step .

In step a ShellDisplay image for the selected probe is rendered using the modules and techniques described in reference to .

After step the method returns to step and waits for input or a request to move the probe re size the probe and or create another probe.

In an image illustrates exemplary Quad Probe ShellDisplays created according to the flow diagram in . The ShellDisplay may be used for example to interrogate a reservoir model with respect to the shape of a given reservoir and its internal arrangement of properties. The ShellDisplay resembles a silhouette in 3D but it also draws split faces for each cell. Therefore the inside of the probe is an empty shell .

In an image illustrates an exemplary Box Probe ShellDisplay created according to the flow diagram in .

In an image illustrates an exemplary Cut Probe ShellDisplay created according to the flow diagram in .

Referring now to a continuation of the flow diagram in is illustrated for creating a probe with a CellDisplay. As demonstrated by the flow diagram in the CellDisplay may be used in connection with a Quad Probe a Box Probe or a Cut Probe.

In step a first bounding box for the probe is selected in the sampling domain according to the type of probe selected.

In step the first bounding box extents are converted mapped from the sampling domain to the index domain using the modules and techniques described in reference to .

In step the geometry attribute and split flag data for each cell within the extents of the first bounding box in the index domain are requested from the grid volume using the modules and techniques described in reference to .

In step split flags are set as a global split flag for each face of each cell to be displayed in the first bounding box.

In step the method determines whether a Cut Probe was selected. If a Cut Probe was selected then the method continues to step . Otherwise the method continues to step .

In step another bounding box is selected for the Cut Probe and a split flag for each cell in the another bounding box is set to inactive status.

In step the split flag data in the first bounding box is checked for each cell using techniques well known in the art.

In step the method determines if the split flag data for a cell in the first bounding box which is not inactive represents a left right near far up or down split. If the split flag data for the cell represents a left right near far up or down split then the method continues to step . Otherwise the method continues to step to determine whether there are any additional cells in the first bounding box.

In step 3 D graphics quads for the cell are selected using the modules and techniques described in reference to .

In step the method determines whether there are additional cells in the first bounding box using techniques well known in the art. If there are additional cells in the first bounding box then the method returns to step . Otherwise the method continues to step .

In step a CellDisplay image for the selected probe is rendered using the modules and techniques described in reference to .

After step the method returns to step and waits for input or a request to move the probe re size the probe and or create another probe.

In an image illustrates an exemplary Box Probe CellDisplay an exemplary Cut Probe CellDisplay and an exemplary Quad Probe CellDisplay created according to the flow diagram in . The CellDisplay is used to visualize the inside of any given cell and its immediate relationship to neighboring cells. The CellDisplay is similar to a ShellDisplay but it draws the faces for each cell according to the split flags. For example if the split is left down far then the CellDisplay will draw the left down and far faces of the cells in the region defined by the probe. The CellDisplay uses bitwise operations applied to split flags for showing different combinations of the six faces. The CellDisplay can skip the static interval of I J and or K. The Box Probe and Cut Probe skip every 5 layers along I. The CellDisplay is also used for showing the intersection of a cell with a particular plane in the Quad Probe or Slice Probe.

Referring now to a continuation of the flow diagram in is illustrated for creating a probe with a PlaneDisplay. As demonstrated by the flow diagram in the PlaneDisplay may be used in connection with a Quad Probe a Box Probe a Cut Probe or a Slice Probe.

In step a first bounding box for the probe is selected in the sampling domain according to the type of probe selected.

In step the method determines whether a Quad Probe was selected. If a Quad Probe was selected then the method continues to step . Otherwise the method may return to steps or .

In step the method determines whether a Box Probe was selected. If a Box Probe was selected then the method continues to step . Otherwise the method may return to steps or .

In step the method determines whether a Cut Probe was selected. If a Cut Probe was selected then the method continues to step . Otherwise the method may return to steps or .

In step the method determines whether a Slice Probe was selected. If a Slice Probe was selected then the method continues to step . Otherwise the method may return to steps or .

In step a quad plane is generated for the Quad Probe using the modules and techniques described in reference to .

In step six quad planes are generated for the Box Probe. Each quad plane may be generated using the same techniques used to generate the quad plane in step .

In step twelve quad planes are generated for the Cut Probe. Each quad plane may be generated using the same techniques used to generate the quad plane in step .

In step quad planes are generated between the opposing manipulators on the Slice Probe. Each quad plane may be generated using the same techniques used to generate the quad plane in step .

In step the first bounding box extents are converted mapped from the sampling domain to the index domain using the modules and techniques described in reference to .

In step the method determines whether a Cut Probe was selected. If a Cut Probe was selected then the method continues to step . Otherwise the method continues to step .

In step another bounding box is selected for the Cut Probe and a split flag for each cell in the another bounding box is set to inactive status.

In step the geometry attribute and split flag data for each cell within an index range that intersects each quad plane are requested from the grid volume using the modules and techniques described in reference to .

In step an intersected quad plane is computed for each cell if the cell intersects the quad plane. To find an intersection between the quad plane and any cell one approach may be used that divides a cell into five 5 tetrahedrons. Then a look up table may be applied to map the intersected edges to triangles. Using this approach a cross section may be moved interactively inside a 2.3 million cell grid.

In step 3 D graphics quads for the cell are selected for each cell that intersects a quad plane using the modules and techniques described in reference to .

In step the method determines whether there are additional cells in the first bounding box using techniques well known in the art. If there are additional cells in the first bounding box then the method returns to step . Otherwise the method continues to step .

In step a PlaneDisplay image for the selected probe is rendered using the modules and techniques described in reference to .

After step the method returns to step and waits for input or a request to move the probe re size the probe and or create another probe.

In an image illustrates exemplary Quad Probe PlaneDisplays created according to the flow diagram in . The PlaneDisplay is designed to build layers and sections that cut across true reservoir layers similar to a time slice in a geophysical cube. The PlaneDisplay is most useful for evaluating the geological and petrophysical properties at particular depths. A PlaneDisplay for example constructed at a flat oil water contact point would permit the geometry and property distribution of the higher quality reservoir layers above and below the contact point to be examined. The PlaneDisplay renders an image similar to a slice that intersects a defined plane through a Box Probe a Quad Probe and a Slice Probe.

In an image illustrates an exemplary Box Probe PlaneDisplay created according to the flow diagram in .

In an image illustrates an exemplary Slice Probe PlaneDisplay created according to the flow diagram in .

Referring now to a continuation of the flow diagram in is illustrated for creating a probe with a cell rendered FilterDisplay. As demonstrated by the flow diagram in the cell rendered FilterDisplay may only be used in connection with a Filter Probe.

In step a bounding box for the Filter Probe is selected in the sampling domain according to the type of probe selected.

In step the bounding box extents are converted mapped from the sampling domain to the index domain using modules and techniques described in reference to .

In step the geometry attribute and split flag data for each cell within the extents of the bounding box in the index domain are requested from the grid volume using the modules and techniques described in reference to .

In step an attribute data range is selected from a color map editor using a conventional graphical user interface.

In step the split flag data in the bounding box is checked for each cell with an attribute in the attribute data range using techniques well known in the art.

In step the method determines if the split flag data for a cell in the bounding box with an attribute in the attribute data range represents a left right near far up or down split. If the split flag data for the cell represents a left right near far up or down split then the method continues to step . Otherwise the method continues to step to determine whether there are additional cells in the bounding box.

In step 3 D graphics quads for the cell are selected using the modules and techniques described in reference to .

In step the method determines whether there are additional cells in the bounding box using techniques well known in the art. If there are additional cells in the bounding box then the method returns to step . Otherwise the method continues to step .

In step a cell rendered FilterDisplay image for the Filter Probe is rendered using the modules and techniques described in reference to .

After step the method returns to step and waits for input or a request to move the probe re size the probe and or create another probe.

In an image illustrates an exemplary cell rendered Filter Probe FilterDisplay created according to the flow diagram in . In the FilterDisplay cells that are less than a defined threshold are filtered out while the rest are displayed with different colors.

Referring now to a continuation of the flow diagram in is illustrated for creating a probe with a volume rendered FilterDisplay. As demonstrated by the flow diagram in the volume rendered FilterDisplay may only be used in connection with a Filter Probe.

In step a bounding box for the Filter Probe is selected in the sampling domain according to the type of probe selected.

In step the bounding box extents are converted mapped from the sampling domain to the index domain using the modules and techniques described in reference to .

In step the geometry attribute and split flag data for each cell within the extents of the bounding box in the index domain are requested from the grid volume using the modules and techniques described in reference to .

In step an attribute data range is selected from the color map editor using a conventional graphical user interface.

In step a closest index axis and a view vector for the grid data from step are computed using techniques well known in the art.

In step the method loops through the defined sub grid volume from back to front along the closest index axis.

In step 3D graphics quads for each active cell in the bounding box with an attribute in the attribute data range are selected using the modules and techniques described in reference to .

In step the method determines whether there are additional active cells in the bounding box using techniques well known in the art. If there are additional active cells in the bounding box then the method returns to step . Otherwise the method continues to step .

In step a volume rendered FilterDisplay image for the Filter Probe is rendered using the modules and techniques described in reference to .

After step the method returns to step and waits for input or a request to move the probe re size the probe and or create another probe.

In an image illustrates an exemplary volume rendered Filter Probe FilterDisplay created according to the flow diagram in . For reservoir visualization and volume rendering a FilterDisplay may be used to roughly mimic the continuity of geological and petrophysical features and the shape of geobodies that result from connected cells with like properties. Using typical volume rendering for seismic data the alpha channel of the color table was used to specify a display range for the grid data. Domain geoscientists and engineers want to see and understand the attribute magnitude at each cell. Therefore instead of surface volume rendering cell based volume rendering was implemented. This method can generate closed isosurfaces. The connection threshold can be set to specify the threshold number of connected cells. If the connected cells within a body are less than the threshold those cells are filtered removed .

Referring now to a continuation of the flow diagram in is illustrated for moving a probe. Once a particular probe and display are created according to one of the flow diagrams illustrated in each probe may be moved in the following manner.

In step the new location for the probe is input by UIM . In a preferred embodiment any conventional input device may be used to direct the new location of the probe. The location of the probe may be moved by contacting a manipulator on the display with the input device and selecting through a graphical user interface or the input device to move the probe in any direction by dragging the manipulator or display along a trajectory to a new location. When a new location for the probe is reached the input device is used to release the manipulator or display.

In step GPM requests grid data for the new location of the probe from GridProbe Module . GPM processes the grid data extracted by VSM for the probe being moved and draws renders the probe at a new location in accordance with the attributes selected.

As the probe is moved for each new location of the probe the steps described herein and in or may be repeated at a rate sufficiently fast that the image of the probe may be perceived as changing with movement of the probe. In other words the image of the probe is being redrawn at a frame rate sufficiently fast to be perceived in real time. To meet the goal of real time performance only the outside layers of the probe may be displayed while the probe is moving. The points vertex for a cell may be drawn as cells for a large probe and the 3D graphics quads may be drawn as split faces for a small probe. When the probe stops moving the full shading details are displayed. For cases where grid data is requested from disc memory and is extremely slow the outlines of the bounding box may be drawn while moving the probe.

Referring now to an image illustrates manipulators for a Quad Probe and a Box Probe. The yellow manipulators are connected by yellow lines forming the Quad Probe bounding box . The red manipulators are connected by red lines forming the Box Probe bounding box . Multiple Quad Probes may be created producing an effect similar to a fence diagram a series of intersecting cross sections and maps as illustrated in .

Referring now to an image illustrates manipulators for a Cut Probe a Slice Probe and a Filter Probe. The purple manipulators are connected by purple lines forming the Cut Probe inner bounding box . The yellow manipulators are connected by yellow lines forming the Cut Probe outer bounding box . The red manipulators are connected by red lines forming the Slice Probe bounding box . The green manipulators positioned on opposite faces of the Slice Probe bounding box form multiple quad planes representing bounding boxes between the opposing manipulators. The blue manipulators are connected by blue lines forming the Filter Probe bounding box .

Referring now to a continuation of the flow diagram in is illustrated for re sizing a probe. Once a particular probe and display are created according to one of the flow diagrams illustrated in each probe may be re sized in the following manner.

In step the new size for the probe is input by UIM . In a preferred embodiment any conventional input device may be used to re size the probe. The size of the probe may be altered which may also alter the shape of the probe by contacting a manipulator or the display with the input device and selecting through a graphical user interface or the input device to re size the probe by dragging the manipulator or the display in any direction. When the input device contacts a manipulator or a display movement of the input device may be used to change the dimensions or properties of the surface on which the manipulator is located. When a desired size or shape for the probe is reached the input device is used to release the manipulator or display. The location of the manipulators is not limited to the bounding box geometry for the probe. It is to be understood however that the present invention is not limited to the use of manipulators for resizing probes and other suitable well known implementations may be used such as for example the sizing tabs described in U.S. Pat. No. 6 765 570.

In step the method determines whether more data is needed to draw the re sized probe. For example if the re sized probe is of a shape and size that fits inside the existing probe then no more data is needed and processing continues according to the probe and display selected when the method returns to step or . Otherwise if the re sized probe is of a shape and size that falls at least partially outside of the existing probe then the method continues to step .

In step GPM requests grid data needed for the re sized probe from GridProbe Module . GPM processes the grid data extracted by VSM for the probe being re sized and draws renders the probe with its new size and or shape in accordance with the attributes selected.

As the size and or shape of the probe changes the steps described herein and in or may be repeated at a rate sufficiently fast that the image of the probe may be perceived as changing with the changing size and or shape of the probe. The image of the probe is therefore being redrawn at a frame rate sufficiently fast to be perceived in real time.

Referring now to an image illustrates the use of control points to locate cells in a Quad Probe ShellDisplay that intersect line segments e.g. between the control points. For editing operations this particular application may include functionality to enter move and delete control points on any type of probe display. Certain graphics objects such as a point a line a plane or polygons may therefore be displayed to assist the application for a particular process. Then the application can query these cells to apply the particular process.

The present invention was applied to two large grids a first grid of 2.3 million cells 190 300 40 and a second grid of 20 million cells 300 400 168 on a 32 bit Windows operating system. The computer system comprised a bi Xeon 3.6 GHz with 3 GB of RAM and an NVIDIA Quadro FX 5600 graphics card. Table 1 summarizes the results of the application using a Box Probe ShellDisplay and a Quad Probe ShellDisplay.

While the present invention has been described in connection with presently preferred embodiments it will be understood by those skilled in the art that it is not intended to limit the invention to those embodiments. The present invention may also be applied to other types of geometrically irregular data such as for example medical data and engineering data. It is therefore contemplated that various alternative embodiments and modifications may be made to the disclosed embodiments without departing from the spirit and scope of the invention defined by the appended claims and equivalents thereof.

