---

title: Host-based printer driver
abstract: A system includes a controller operable to receive a first data set comprising data in a first format type, the first-format-type data representing an image. The system further includes a circuit coupled to the controller, the circuit operable to produce a second data set in a second format type, the second data set based on the first-format-type data, the second data set representing the image.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08027053&OS=08027053&RS=08027053
owner: Marvell International Technology Ltd.
number: 08027053
owner_city: 
owner_country: BM
publication_date: 20090409
---
This application is a continuation of U.S. application Ser. No. 10 840 696 filed May 5 2004 which is hereby incorporated by reference.

Host based printer drivers are software applications that process print data i.e. data to be sent to a printer on a host device such as a personal computer. By processing the print data on the host device the printer driver allows the host device to cooperate with printers having minimal processing capability and thus a lower cost while yielding superior print quality.

However because such low capability printers cannot process object oriented graphics e.g. vector graphics and associated text fonts the printer driver typically converts object oriented images into raster bitmap data before the printer can print the images. Unfortunately such data conversion often places high demands on the processing resources of the host device and thus can detract from the performance of applications simultaneously running on the host device.

According to an embodiment of the invention a system includes a controller operable to receive a first data set comprising data in a first format type the first format type data representing an image. The system further includes a circuit coupled to the controller the circuit operable to produce a second data set in a second format type the second data set based on the first format type data the second data set representing the image.

Most modern personal computers PCs are equipped with video cards aka video adapters that have high level 2D and 3D graphics processing capabilities. Conventionally PCs employ such video card processing capability solely to process data to be rendered by a video display. According to an embodiment of the invention a host based printer driver leverages this video card capability to process print data.

In operation the application issues a print request with associated print data representing an image e.g. graphics or text to the driver through defined interfaces associated with the OS . The print data received by the driver can be in a variety of known application specific formats such as for example bitmapped graphics bitmapped text fonts vector graphics text fonts and or vector graphics. The driver converts any non raster print data to raster data so that the printer can print the associated image.

The driver translates the vector graphics based print data into a set of executable commands. The driver communicates these commands to the video card for execution. In one embodiment the driver is configured to employ a high level cross platform API such as OpenGL or DirectX in order to communicate with the video card . Of course the driver can be configured to utilize other custom APIs as well.

In executing the commands received from the driver the video card produces bitmapped images of points arcs lines text and other shapes corresponding to the vector graphics and thus to the associated image. The commands may further instruct the video card to fill as appropriate the rendered bitmapped shapes in a manner and with colors specified by the commands. For example at the direction of the driver the video card may render overlapping objects only a topmost object or blended objects in the case of semi transparent objects.

In a case where the print data includes both vector graphics and bitmap data the driver may pass the bitmap data along with the commands to the video card . The video card may cache this bitmap data in a memory not shown of the video card and later place the bitmap data in an appropriate location of the image rendered by the video card .

Once the video card has rendered into bitmap format the image or portion thereof associated with the print data the video card communicates the bitmapped image to the memory . The driver may then employ the CPU to perform any necessary post processing of the rendered image before providing the image to the printer via the interface for printing.

As discussed above video cards are conventionally used to process data for display on video monitors. Standard video monitors are capable of displaying far fewer pixels than can be displayed on a printed page. If a particular print data set represents an image that when in bitmap format requires a large number of pixels the video card may not be able to render the entire image.

As illustrated in an embodiment of the driver includes a divider and an assembler . The assembler is operable to divide into portions only portions shown a print data set received from the application . The driver translates each vector graphic portion into a corresponding instruction set and serially issues each instruction set to the video card for execution. Each instruction set once executed by the video card produces a corresponding bitmap portion that the video card subsequently provides to the assembler . The assembler is operable to assemble the bitmap portions into the complete bitmapped version of the image. The driver then provides the assembled bitmapped image to the printer .

In an alternative embodiment the driver may allocate a subset of the data portions to the video card for processing. The driver itself may then process the data portions not allocated to the video card to produce corresponding bitmap portions . The processing by the driver of data portions may or may not be simultaneous with processing by the video card of data portions .

The preceding discussion is presented to enable a person skilled in the art to make and use the invention. Various modifications to the disclosed embodiments will be readily apparent to those skilled in the art and the generic principles herein may be applied to other embodiments and applications without departing from the spirit and scope of the present invention. Thus the present invention is not intended to be limited to the embodiments shown but is to be accorded the widest scope consistent with the principles and features disclosed herein.

