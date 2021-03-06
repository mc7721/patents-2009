---

title: Minimizing problems in accessing referred content
abstract: According to an aspect of the present invention, information indicating the list of referrer documents referring to a referred document, is maintained. Thus, when the document identifier (name and directory location of the document) changes, the list of referrer documents that need to be changed can be easily identified. In an embodiment, the administrators of the referrer document are notified (e.g., by an automatic email) of the change of the document identifier of the referred document. According to another aspect of the present invention, a first mapping of the Uniform Resource Locator (URL) of each web accessible page/document to a virtual link is maintained in a web server. The content server maintains a second mapping of the virtual link to the document identifier. Thus, when the document identifier changes, only the second map in the content server needs to be updated for continued access of the content.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07970744&OS=07970744&RS=07970744
owner: Oracle International Corporation
number: 07970744
owner_city: Redwood Shores
owner_country: US
publication_date: 20090122
---
The present application is a divisional of and claims priority from co pending U.S. application Ser. No. 10 908 218 entitled Minimizing Problems in Accessing Referred Content filed on May 3 2005 and is incorporated in its entirety herewith.

The present invention relates to content management in digital processing systems and more specifically to a method and apparatus for minimizing problems in accessing referred content.

There are often scenarios in which content referred content from one source is referred to in the content of another source. For example when a user accesses a web page the web page may be defined to contain content of several files and the web page delivered to the user contains the contents of all such files. The files thus accessed and containing the referred content are termed to as referred documents and the web page is termed as the referrer document.

While the referred content in the above example is provided as integral to the referrer document for example due to the definition of the web page there are other scenarios in which the referred content is delivered external to the referrer document. As an illustration many web pages often contain hyperlinks with an associated Uniform Resource Locator URL and a user selects the hyperlink to access the content of the referred document corresponding to the URL.

Users are known to experience problems in accessing referred content typically because of changes to the document identifier of the referred documents or deletion of the referred documents themselves. A document identifier refers to a name string often including directory structure where the document is located which is used to uniquely identify the document interfacing with the system software e.g. operating system executing on a system from which the document is accessible.

In such situations user accessing content are displayed messages such as file not found or a portion of the display containing blank. It is generally desirable that such access problems be avoided.

In the drawings like reference numbers generally indicate identical functionally similar and or structurally similar elements. The drawing in which an element first appears is indicated by the leftmost digit s in the corresponding reference number.

According to an aspect of the present invention data indicating the referrer documents corresponding to each referred document is maintained. Thus when there is a change of the document identifier either moved to a new location deleted or renamed of a referred document the corresponding referrer documents which may require changes are easily identified. In one embodiment described below the administrator corresponding to each of such identified referrer documents is notified of the change to the document identifier of the referred document.

According to another aspect of the present invention a server web server processing requests for web pages identified by corresponding Uniform Resource Locators URLs maintains a map of the URL to a logical link. A content server providing the document corresponding to the URL maintains a mapping from the logical link to the document identifier.

Thus when a web server receives a request for a web page identified by a URL the web server maps the URL to a corresponding logical link and sends the logical link to a content server. The content server maps the logical link to the corresponding document identifier and causes the corresponding content to be provided to the user system requesting the web page.

If the document identifier of the referred document changes the content server updates the map mapping the logical link to the corresponding document identifier. Thereafter the content corresponding to the URL received by a web server continues to be provided to user systems sending the URL.

Several aspects of the invention are described below with reference to examples for illustration. It should be understood that numerous specific details relationships and methods are set forth to provide a full understanding of the invention. One skilled in the relevant art however will readily recognize that the invention can be practiced without one or more of the specific details or with other methods etc. In other instances well known structures or operations are not shown in detail to avoid obscuring the features of the present invention.

Internet generally refers to a conglomeration of network connecting various systems here client system and web server and is implemented using protocols such as Internet Protocol IP . Intranet is also implemented using protocols such as IP and is generally owned or operated by an organization providing the content services. Intranet provides connectivity between web server and content server .

Content server may store or otherwise provide access to content of various web pages. Client system A may execute software such as browsers enabling a user to specify specific web pages of interest. The Uniform Resource Locator URL corresponding to the specified web pages are forwarded to web server via Internet .

Web server receives the URLs and any associated parameters and causes the content corresponding to the URL to be served to client system . If the content is present on content server web server interfaces with content server to serve the content. Often times web server itself stores the content. Various aspects of the present invention minimize problems while providing access to the content as described below.

In step content server maintain information indicating the list of referrer documents which refer to each referred document. illustrates an example table containing such information. Column and respectively contain the document identifiers of the referred and referrer documents. As depicted there in rows and a document with name doc and contained in a directory a b c is referred by documents doc and doc in directory a b c . Column indicates whether the referred document identifier is valid i.e. not delete from content server .

Continuing with reference to in step content server detects a change in the referred document identifier for example when the referred document is moved to a different location or deleted. Such changes are often implemented in the drivers or other components of the system software and the detection task may be implemented associated with the drivers system software. Such implementations will be apparent to one skilled in the relevant arts by reading the disclosure provided herein.

In step content server updates the information to reflect the change. For example if the referred document is deleted the corresponding row in valid column is set to N not valid as depicted in row . On the other hand if the referred document is moved the corresponding row in referred column is modified to reflect the new document identifier after the move .

In step content server notifies e.g. by email the modification to the administrator of each referrer document associated with the referred document. The administrator can then take appropriate action such as changing the document identifier in the corresponding referrer documents. The flowchart ends in step .

Due to the notification to administrator the problems in accessing content may be reduced since the administrator can take appropriate actions. One problem with the approach of above is that the administrator intervention is relied upon for corrections needed for continued access to the referred content. The below noted approach overcomes some of such problems as described below.

In step a first map mapping each resource locator to a virtual link and a second map mapping the virtual link to the document identifier of the document is maintained. Web server may maintain the first map and content server may maintain the second map as respectively shown with respect to . These tables can be contained within a database.

As shown columns and in respectively contain URL and the virtual link identifier and columns and in respectively contain the virtual link to the document identifier. Thus a URL of http www.mywebsite.com d1 is shown mapped to link by row of and row of is shown mapping link to a b c doc. The other mappings are similarly described. It should be appreciated that the two maps can be combined into a single map. In addition web server and content server can be integrated as a single physical unit.

Continuing with combined reference to A B and C in step content server detects a change in the document identifier of the referred document. The detection can be performed similar to in step described above. In step content server updates the second mapping to reflect the changes. Assuming doc has been moved to a new directory a b d and with a new name ndoc depicts the corresponding second map. In particular row is shown changed to indicate the changed document identifier. The flowchart ends in step .

Due to the updating of the second map from the logical link to the document identifier user accesses can continue without substantial disruption even when the document identifier changes as further described below with reference to .

In step web server receives a resource locator URL from client system . The URL may be received when a user at the client system selects a hyperlink encoding the URL in a referring document. The manner in which the web page content of the referred document corresponding to the URL is retrieved is described below.

In step web server determines the virtual link corresponding to the resource locator according to the mapping of . In step web server sends the virtual link to content server . The interface between web server and content server can be implemented using any compatible approach as will be apparent to one skilled in the relevant arts.

In step content server maps the virtual link to the document identifier using the mapping of FIG. B C. Since the mapping is updated to reflect any changes in the document identifier the file document corresponding to the URL of step is readily accessed. In step content server sends the content of the accessed document either to web server or client system directly depending on the specific approach used in the environment . The flowchart ends in step .

Thus using the approaches described above either alone or in combination one may minimize problems in accessing referred content. The approaches may be implemented in various embodiments. The description is continued with respect to embodiments in which the aspects of the invention are operative when appropriate software instructions are executed.

CPU may execute instructions stored in RAM to provide several features of the present invention. CPU may contain multiple processing units with each processing unit potentially being designed for a specific task. Alternatively CPU may contain only a single general purpose processing unit. RAM may receive instructions from secondary memory using communication path .

Graphics controller generates display signals e.g. in RGB format to display unit based on data instructions received from CPU . Display unit contains a display screen to display the images defined by the display signals. Input interface may correspond to a key board and or mouse. Network interface provides connectivity to a network e.g. using Internet Protocol . In the case of web server network interface provides network connectivity to both Intranet and Internet and in the case of content server network interface provides network connectivity to Intranet .

Secondary memory may contain hard drive flash memory and removable storage drive . Secondary memory may store the data and software instructions which enable digital processing system to provide several features in accordance with the present invention. Some or all of the data and instructions may be provided on removable storage unit and the data and instructions may be read and provided by removable storage drive to CPU . Floppy drive magnetic tape drive CD ROM drive DVD Drive Flash memory removable memory chip PCMCIA Card EPROM are examples of such removable storage drive .

Removable storage unit may be implemented using medium and storage format compatible with removable storage drive such that removable storage drive can read the data and instructions. Thus removable storage unit includes a computer readable storage medium having stored therein computer software and or data.

In this document the term computer program product is used to generally refer to removable storage unit or hard disk installed in hard drive . These computer program products are means for providing software to digital processing system . CPU may retrieve the software instructions and execute the instructions to provide various features of the present invention described above.

While various embodiments of the present invention have been described above it should be understood that they have been presented by way of example only and not limitation. Thus the breadth and scope of the present invention should not be limited by any of the above described exemplary embodiments but should be defined only in accordance with the following claims and their equivalents. Also the various aspects features components and or embodiments of the present invention described above may be embodied singly or in any combination in a data storage system such as a database system.

