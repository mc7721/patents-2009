---

title: Progress-driven progress information in a service-oriented architecture
abstract: A system may include reception of the first instruction, execution of the business process in a first software work process, reception, during execution of the business process, of an indication of a business object process associated with the business process, determination of progress information associated with the business process based on the indication of the business object process, and storage of the progress information within a memory. Aspects may further include reception, at a second work process, of a request from the client application for progress information, retrieval of the progress information from the shared memory and provision of the progress information to the client application.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08739166&OS=08739166&RS=08739166
owner: SAP AG
number: 08739166
owner_city: Walldorf
owner_country: DE
publication_date: 20091228
---
This application is related to U.S. patent application Ser. No. 12 647 732 filed on even date herewith and entitled Progress Information in a Service Oriented Architecture. 

Some embodiments relate to a service oriented architecture to provide software services. More specifically some embodiments relate to the provision of progress information to a service client during service fulfillment.

In one operational example a user may manipulate a user interface of client to input an instruction e.g. update inventory . Client in response may transmit a corresponding HTTP service request to service oriented architecture as illustrated. Service oriented architecture conducts any processing required by the request e.g. updating a list of inventory and after completing the processing provides a response to client .

Client does not receive any indication from service oriented architecture during the above mentioned processing. Accordingly after inputting the instruction and before receiving the response the user is left to wonder whether any processing is occurring as a result of the instruction whether service oriented architecture is non responsive or whether a network error has occurred between client and service oriented architecture . Service requests which require lengthy processing exacerbate this dilemma.

Due to the request response nature of HTTP the foregoing cannot be addressed simply by programming service oriented architecture to send some sort of progress indicator to client . In non HTTP systems the server system may be hardcoded to provide progress information on a case by case basis or to provide all generated feedback information to the client. The former approach is inefficient and resource intensive while the latter approach overwhelms the client with cryptic information which even if understood may provide little indication of the progress of the overall business process being executed.

Accordingly what is needed is a system to provide meaningful progress information to a client of a service oriented architecture.

Generally business process platform may provide services to client according to some embodiments. Such services may comprise Web services and client may therefore comprise a Web client. Examples of a Web client include but are not limited to a Web browser an execution engine e.g. JAVA Flash Silverlight to execute associated code in a Web browser and a dedicated standalone application.

Business process platform includes software work process and software work process . Each of software work processes and may independently execute tasks required of business process platform . Business process platform may support more than two simultaneous software work processes according to some embodiments.

Software work process includes Controller Object CO and business objects BOs . CO may be associated with a UI floorplan which is currently presented by client . CO therefore is familiar with business processes associated with the UI floorplan. Elements of software work process may execute such a business process by manipulating one or more of BOs each of which is unaware of the overall business process for which it is being manipulated.

Business process platform also includes shared memory and text tables each of which may be implemented in one of Random Access Memory persistent storage e.g. hard disks and or in any other suitable electronic memory. Shared memory may store business process progress information generated by work process as described below. In some embodiments shared memory stores text describing processes and subprocesses of one or more BOs as well as text describing processes and subprocesses of business processes which are associated with CO . The text descriptions may be associated with respective identifiers to allow lookup thereof by either of work processes and .

Text tables may store descriptions of business process and business subprocesses in several languages. As will be described in detail below work process may request a description of a business process or subprocess in a particular language from text tables . The description may be forwarded to client .

Each of software work processes and is in i.e. capable of communication with shared memory and software work process is in i.e. capable of communication with text tables but embodiments are not limited thereto. In some embodiments both shared memory and text tables are implemented in a same electronic memory which is accessible by any work process executing within platform .

Initially an instruction to execute a business process is received from a client application at S. The instruction may comprise a Web service call according to some embodiments. The instruction may be transmitted by the client application in response to user manipulation of a user interface presented by the client application.

Therefore prior to S the user navigates to user interface and completes the inputs fields thereof. The user then selects Hire Employee icon causing client to transmit an instruction to business process platform e.g. via HTTP to execute the business process needed to effect the hiring of a new employee. This instruction is received by business process platform at S.

The instruction may include a session identifier e.g. cookie per the HTTP protocol. Business process platform assigns the instruction to work process and the session identifier is associated with the hire employee business process to be performed by work process .

Accordingly work process executes the business process at S. Execution of the business process may include but is not limited to instantiating populating and manipulating BOs within business process platform . Each of BOs may comprise a class defining data and methods associated with a business entity. For example S may include creation of an employee business object an employment business object a work agreement business object a compensation agreement business object etc. as well as definition of dependencies therebetween.

At S and during execution of the business process an indication of a business object process is received. The business object process is associated with the business process. In other words the business object process is a process or subprocess executed by one of BOs during execution of the business process.

According to some embodiments CO receives the indication at S. The indication may be generated by one of BOs and received directly therefrom or via a dedicated service as will be described below. One or more of BOs may therefore be coded so as to generate one or more indications during processing.

Table of includes indications e.g. Process ID that may be generated by one or more of BOs during execution of a business object process. Each process ID beginning with HCM C  is associated with a business object process that may be executed by a business object and known to the business object. Although only two process IDs beginning with HCM C  are shown table may include any number thereof.

After or during execution of a business object process a business object may generate a corresponding process ID for reception by CO at S. Similarly table of includes indications of business object subprocesses that might be generated by one or more of BOs during execution of a business object subprocess. illustrates only one business object process i.e. HCM C  and its corresponding subprocesses i.e. 5 through 85 but embodiments are not limited thereto. An indication of a subprocess may include a process ID of a corresponding business object process e.g. HCM C  and a subprocess ID. A business object may generate a process ID and subprocess ID for reception by CO at S after or during execution of a corresponding business object subprocess.

CO may therefore access table and or table at S to determine a business object process description and or subprocess description which corresponds to the received process ID subprocess ID. In some embodiments table and table are stored in memory .

As mentioned above a business object may be only aware of its own execution. A business object is most likely unaware of its role or its temporal position in the currently executing business process. Accordingly a business object is not suited to provide progress information regarding the overall business process being executed.

At S progress information associated with the business process is determined. The determination is based on the indication received at S. According to the present example CO is coded to determined whether a mapping exists between the received indication and previously stored business process progress information.

Tables and both show such previously stored business process progress information according to some embodiments. The business process progress information is stored in conjunction with a process ID beginning with HCM A  and in the case of sub processes i.e. in table also in conjunction with a subprocess ID.

The business processes and subprocesses HCM A  of tables and may correspond in any manner to the business object processes and subprocesses HCM C  of tables and . For example one business object process e.g. HCM C  may correspond to several business processes e.g. HCM A  through HCM A  . In some embodiments several business object subprocesses e.g. HCM C  through HCM C  may correspond to a smaller set of business subprocesses e.g. HCM A  through HCM A  .

CO may therefore be coded to determine business object process subprocess progress information e.g. HCM A  at S from tables and or based on the received business object process ID subprocess ID.

The determined progress information may include an indication of a degree of completion of the business process. This indication may comprise any information that indicates a degree of completion examples of which include a percentage a current step number and maximum step number and a graphic. Again this indication may be generated by CO rather than by BOs due to CO s knowledge of the overall business process.

Next at S it is determined whether the determined progress information should be used to update already stored progress information. It will be assumed that no other progress information is currently stored in memory and therefore flow proceeds to S.

The determined progress information is stored in a memory at S in association with the session identifier. According to some embodiments software work process stores the progress information in shared memory . Such storage enables retrieval of the progress information from shared memory based on the session identifier.

Flow proceeds to S to determine whether the business process is complete. Process therefore cycles through S to S as described above until it is determined that the business process is complete. After determining that the business process is complete work process may issue an instruction at S to release the area of shared memory which is reserved for storing progress information.

As an example of S according to some embodiments it will be assumed that a hire employee instruction was received at S. During execution of this business process the indications HCM C  and were received at S. Referring to table these indications correspond to the business object process Hiring an Employee and its subprocess Creating Identity and User .

At S CO determines based on the received indication its own internal coding and table the progress information Hiring an Employee and Updating Identity . A corresponding indication is stored in shared memory at S. The indication may include the corresponding process ID i.e. HCM A  and subprocess ID and may be associated with a session identifier associated with the executing business process.

Continuing the present example CO may receive a second indication upon returning to S. The second indication may include the indications HCM C  and . Again referring to tables and these indications correspond to the business object process Hiring an Employee and its subprocess Assigning Employee to Organizational Structure .

At S of the present example CO determines that the progress information Hiring an Employee and Updating Identity corresponds to the second indication. Since this progress information is identical to the previously stored business process progress information the progress information is not updated and flow proceeds to S and continues as described above.

It is assumed that the indication HCM C  is then received at S. At S CO determines the progress information Hiring an Employee and Updating Compensation Agreement as corresponding to the received indication. Since this progress information differs from the most recently stored progress information an indication of this progress information i.e. HCM A  is stored in shared memory at S in association with the session identifier. It may be preferable to overwrite previously stored progress information to avoid confusion as to which is most recent.

Process may be performed in parallel with process of . Generally as progress information is stored and updated in a shared memory according to process the progress information may be retrieved therefrom and provided to a client application according to process . In some embodiments the progress information is stored and updated by a first software work process e.g. work process and is retrieved and provided to the client application by a second software work process e.g. work process .

Initially at S a progress request and a session identifier are received from a client application. For example client may send a progress request and the session identifier to business process platform from the same client session used to send the instruction received at S. Client may send the progress request at a pre designated interval e.g. 1 second after sending the instruction.

Business process platform assigns the progress request to work process and at S work process retrieves the progress information from shared memory . Work process may use the received session identifier as a key to retrieve the progress information from shared memory at S. The retrieved progress information may include IDs such as those shown in tables and and or associated text descriptions. As described above the retrieved progress information may include an indication of a degree of completion of the business process.

A desired language is then determined at S. The desired language may be a current system language i.e. LANGU specified by configuration tables of platform . In some embodiments the desired language is specified within the received progress request.

Next at S text in the desired language is retrieved. The text corresponds to the retrieved business process progress information. According to some embodiments work process requests text from text tables using IDs e.g. HCM A  associated with the business process progress information and an indication of the desired language.

Retrieving the text in response to progress requests may consume fewer resources than systems in which work process stores the progress information in memory in the desired language. Such systems must retrieve text in the desired language each time progress information is stored.

The text is provided to the client application at S. Such provision may proceed according to the standard HTTP request response protocol. More specifically the text is sent via an HTTP response corresponding to the HTTP progress request received at S. An indication of a degree of completion of the business process may also be sent to the client application at S.

Flow returns from S to S to await another progress request. If another request and session identifier are received progress information is retrieved from shared memory at S as described above. Due to concurrent execution of process the now retrieved progress information may be different from the progress information retrieved in response to the last progress request.

Flow therefore continues through process as described above until text in the desired language and corresponding to the progress information is provided to the client application at S. Continuing with the present example is a view of user interface displayed by client after S according to some embodiments. User interface includes progress information window the contents of which have changed since the time represented in .

Specifically window includes the text Updating Compensation Agreement and the indication Step of and progress bar is more advanced than shown in . User interface thereby provides a visual indication of advancing progress according to some embodiments. Again any other information indicative of execution progress may be provided at S and that information may be presented by the client application in any suitable manner.

Business process platform may comprise a service oriented architecture to provide services to client and to other clients according to some embodiments. Business process platform includes dispatcher process to receive HTTP requests from client and to forward the requests to appropriate work processes. For example dispatcher process may receive an HTTP request associated with user interface floorplan functionality and may dispatch the request to ABAP dialog process . Based on the type of request ABAP dialog process calls an HTTP Handler UI .

Local Client Proxy LCP Wrapper of ABAP dialog process forwards the request to an Enterprise Services Framework ESF . As is known in the art the ESF manipulates BOs to provide enterprise services. The ESF may also issue requests to an CO associated with the currently viewed UI floorplan. As described above the CO provides additional business knowledge and functionality behind the operation of the UI floorplan.

Progress information service as will be described in detail below receives information generated by one or more BOs of dialog process and provides the information to the CO. Progress information service may also receive progress information from the CO and store the progress information in shared memory. Progress information service may provide an application programming interface of static class methods to facilitate this operation according to some embodiments.

Upon receiving a request for progress information dispatcher process may dispatch the request to ABAP dialog process . In turn ABAP dialog process calls an HTTP Handler Progress . As will be described below the HTTP Handler Progress uses progress information service to retrieve the progress information from shared memory and returns the progress information to client .

Memory may include tables and . Memory may be accessible by both of processes and . Processes and may therefore provide receive and process information related to business processes business subprocesses business object processes and business object subprocesses via their respective IDs.

Client may comprise a Web client as described above. UI controller of client may comprise a software thread to control a user interface displayed by client . Requests related to user interface functionality are passed from UI controller to HTTP connector UI communication thread and on to platform . Similarly UI controller passes requests for progress information to HTTP connector progress communication thread .

System may execute processes and according to some embodiments. In a specific example an instruction to execute a business process associated with a UI floorplan is passed from UI controller to HTTP connector UI communication thread to dispatcher process and is received by dialog process at S.

The CO may then call an interface of progress information service to register therewith. Registration informs progress information service to provide the CO with any progress related information received from the BOs during execution of the business process. The following interface may be used 

Next the ESF BOs and CO of process operate to execute the business process at S. During such execution one or more BOs may generate progress related information and provide this information to progress information service via an interface such as 

Due to registration of the CO progress information service performs a callback to the CO upon receipt of the information from the one or more BOs. The callback may be implemented as follows 

After proceeding through S and S as described above to determine progress information based on the indicated business object process the CO calls another interface of progress information service to store the progress information in shared memory . The foregoing is an example of such an interface according to some embodiments 

For example progress information may comprise Updating 1 Purchase Orders . In this example the value of variable 1 cannot be determined at design time of the progress information. Instead the value is dynamically provided at runtime.

Turning to process the request to retrieve progress information received at S is formatted as follows according to some embodiments 

After receiving the request the HTTP Handler Progress of process may call interfaces of progress information service in order to retrieve the progress information. First HTTP Handler Progress calls 

At S the following HTTP compatible format may be used to provide the progress information to client application 

Once the CO determines that the business process is completed at S the CO may call the following interface at S to reset shared memory 

Some embodiments of the foregoing may therefore efficiently provide progress information to a client application in a service oriented architecture. Some embodiments may be enabled or disabled at the system server and or application level to provide flexibility and optimization.

Some embodiments may facilitate testing of business objects. In this regard a test platform may register with progress information service to receive indications of business object processes and business object sub processes which are generated by executing BOs. The test platform may then use corresponding descriptions stored in memory to monitor the execution of the business objects.

Each system described herein may be implemented by any number of devices in communication via any number of other public and or private networks. Two or more of devices of may be located remote from one another and may communicate with one another via any known manner of network s and or a dedicated connection. Moreover each device may comprise any number of hardware and or software elements suitable to provide the functions described herein as well as any other functions. Other topologies may be used in conjunction with other embodiments.

All systems and processes discussed herein may be embodied in program code stored on one or more computer readable media. Such media may include for example a floppy disk a CD ROM a DVD ROM a Zip disk magnetic tape and solid state RAM or ROM memories. Embodiments are therefore not limited to any specific combination of hardware and software.

The embodiments described herein are solely for the purpose of illustration. Those in the art will recognize other embodiments may be practiced with modifications and alterations limited only by the claims.

