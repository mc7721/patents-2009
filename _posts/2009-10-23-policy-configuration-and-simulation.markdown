---

title: Policy configuration and simulation
abstract: Techniques for policy configuration and simulation are presented. A graphical user interface (GUI) permits a user to visualize network resources and their relationships to one another. The user can select a resource and receive another view within the GUI to see policies for that resource and relationships between the policies. The user can also select a particular policy and alter its configuration. The altered configuration can then be simulated within the network and the results presented back to the user within the GUI.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08285822&OS=08285822&RS=08285822
owner: Novell, Inc.
number: 08285822
owner_city: Provo
owner_country: US
publication_date: 20091023
---
Enterprises now organize and store information across a wide variety of physical facilities. Employees no longer work at single locations for a single enterprise. Moreover employees have devices and network capabilities to remotely log into an enterprise s network from virtually anywhere across the globe using a plethora of different devices.

All this increased accessibility and mobility require more administration and security than what has been available in the past. To make administration easier directory services are often deployed by enterprises. These directory services logically represent enterprise assets such as users machines files etc. Tools and Application Programming Interfaces API s provide the ability for administrators to assign asset attributes that define security and other actions that are permissible on those assets. Such abilities allow for automated support and maintenance which reduce support staff and corresponding expenses of the enterprises.

Some visualization tools permit graphical viewing a network tree that shows the hierarchical nature of an enterprise s assets. These tools have limited capabilities and often separate tools or API s not fully integrated with the visualization tools are needed for modifying the attributes of the enterprise assets. That is a series of tools are needed for efficient maintenance.

In addition when administrators want to test new actions or attributes for enterprise assets such testing usually occurs in a mirrored testing environment where the tools are duplicated and separately maintained. In many cases separate machines are used in the testing environments. These circumstances add to an enterprise s support staff equipment and maintenance for supporting dual versions of the directory API s and tools .

In various embodiments techniques for policy configuration and simulation are presented. More specifically and in an embodiment a method for policy configuration and simulation is provided. More specifically a graphical user interface GUI is presented to a user for policy configuration and simulation of a network. The network resources are represented within the GUI as interconnected nodes each connection between two particular nodes defining a relationship between those two particular nodes. Finally the user is permitted to selectively activate the nodes to configure policies for particular relationships and to simulate the configured policies against the selectively activated nodes.

As used herein a network resource refers a user a processing device a machine having one or more processors and memory such as a client server peripheral device etc. an automated service that processes as instructions on a processing device groups of users etc. Network resources are authenticated via an identity for access to secure network services.

A secure network is one that requires authentication to access and that may or may not use encryption for communication to and within the secure network.

A node is a logical representation of a network resource within a graphical user interface GUI . Nodes are connected via relationships. A relationship is logically represented as a line within the GUI or other visual depiction as discussed herein and below. A relationship is a type of connection and attributes associated with that connection between two nodes. It is noted that nodes are also network resources and can represent pieces of data or information. The nodes are configured by clicking on them or selecting them in the manners discussed herein and below.

A node is activated within the GUI by selection device of a user such as a mouse a digital pen wand or a finger when the display presenting the GUI is touch screen enabled. Activation is more than a selection. For example when the selection device is a mouse a double click of the mouse on the node activates the node. Conversely a node can be selected by bringing that node into focus or highlighting it with the selection device. For example when the selection device is a mouse a single click of the mouse on the node selects the node or brings it into focus but does not activate the node within the GUI. It is noted that sometimes users can custom configure their selection devices such that a single mouse click can produce activation and a mere mouse over without a click can select or bring a node into focus. The point is there are two types of user actions to take action on a node one is to activate the node and another is to simply select and bring that node into focus within the GUI.

A policy is one or more conditional statements that when evaluated to true perform one or more actions associated with those conditional statements. For example a policy may be if user X is using machine Y then access to resource Z is to be set to read only Here X Y and Z are unique identities for network resources X user Y machine and Z resource such as a database . Again this example was presented for purposes of illustration only. Any customized or enterprise defined conditions assigned to actions can be embodied within a computer readable storage medium and enforced as a policy evaluation on a processing device that is configured to evaluate that policy.

A configuration refers to the specific values or conditions that are used to define or set a particular policy. So a specific set of values that define the conditions and actions for a particular policy is a configuration for that specific policy.

Connections may also represent policies condition path to reach a particular resource in a server s policy tab within a GUI as presented herein and below . These same connections also represent the configuration drivers or calls for configuration to access the resources so the driver needs the resource configuration to address the resource to control the resource being address policies are used which consume the configuration data when the policy is executed an appropriate resource is chosen in some cases the resources are directly connected with the resource where thee is no choice the flow would either pass if the condition leads to true or blocks if the condition leads to false in the server configuration tab for the GUI as presented herein and below .

An identity is authenticated via various techniques e.g. challenge and response interaction cookies assertions etc. that use various identifying information e.g. identifiers with passwords biometric data hardware specific data digital certificates digital signatures etc. . A true identity is one that is unique to a principal across any context that the principal may engage in over a network e.g. Internet Intranet etc. . However each principal may have and manage a variety of identities where each of these identities may only be unique within a given context given service interaction given processing environment given virtual processing environment etc. .

According to an embodiment the techniques presented herein are implemented in proxy server products directory based products storage access based products and or operating system products distributed by Novell Inc. of Provo Utah.

Of course the embodiments of the invention can also be implemented in a variety of products and or devices. Any particular architectural layout or implementation presented herein is provided for purposes of illustration and comprehension only and is not intended to limit various aspects of the invention.

It is within this initial context that various embodiments of the invention are now presented with reference to the .

In some cases the processing device one or more processors is specifically configured to execute the instructions representing the configuration and simulation service. The GUI is presented to the user for purposes of adding deleting and or configuring the network resources nodes as well as for purposes of configuring the policies relationships and connections .

At the configuration and simulation service presents a graphical user interface GUI tool to a user. The GUI tool may be referred to herein as a Modeler or a Modeler Editor. The GUI is presented to the user for purposes of permitting the user to perform custom policy configuration and simulation of those policies on network resources of a network.

At the configuration and simulation service represents network resources as interconnected nodes within the GUI. Each connection between any two particular nodes defines a relationship between those two particular nodes. The relationships are the policies defining the connection and or attributes associated with the connection. Network resources nodes and Relationships connections can also have either image such as an icon color text and or label to uniquely identify them.

According to an embodiment at the configuration and simulation service provides each type of network resource with a unique color for those nodes associated with that type of network resource. So the user can visually and readily ascertain from the GUI different types of network resources such as users groups of users data resources machines peripherals etc.

Continuing with the embodiment of and at the configuration and simulation service provides each node with a unique label within the GUI for the user to ascertain a particular network resource. In some cases the label provides a textual indication as to an identity for the particular network resource. So not only are different types of nodes color coded by each node includes a unique label so that the user can readily ascertain not only the type of network resource represented by a node within the GUI but also ascertain an identity for each network resource via a text label provided with the node.

In an embodiment at the configuration and simulation service identifies at least one node as a Lightweight Directory Access Protocol LDAP server for the network. So one type of network resource is a LDAP server used from directory management by an enterprise.

At the configuration and simulation service permits the user to interact with the nodes depicted in the GUI. This allows the user to selectively activate the nodes representing network resources for purposes of configuring policies for particular relationships connections between nodes network resources . This also permits the user to simulate via the configuration and simulation service the configured policies against the selectively activated nodes.

According to an embodiment at the configuration and simulation service provides an expanded view within the GUI that presents sub network resources other nodes in the expanded vie of the GUI and these sub network resources relationships with one another within the GUI when the user selects a particular network resource. In other words when a node is activated the sub nodes representing policies for that node are shown along with the connection relationships that the policies related to.

In another case at the configuration and simulation service represents each sub network resource as a particular one of the policies.

Continuing with the embodiment of and at the configuration and simulation service depicts the sub network resources as a hierarchy of the policies within the GUI.

Example visual aspects of the GUI when the user selects the nodes and configures the policies are shown below with reference to the .

The network modeling service represents another and in some cases enhanced perspective of the configuration and simulation service presented in detail above with respect to the method for the .

At network modeling service acquires an activation of the selected network resource from a user within a GUI. The GUI depicts the activated selected network resource along with other network resources of a network which depicts the possibilities after applying the policies similar to a partial simulation.

According to an embodiment at the network modeling service receives a selection within the GUI from the user. The selection identifies the network resource which is depicted as a node within the GUI. Also the network modeling service alters a presentation of the GUI to show a path of connections from the selected network resource to other network resources connected in the path with the selected network resource. A visual depiction of this scenario is presented below with reference to the .

Continuing with the embodiment of and at the network modeling service identifies the selection from the selected network resource as a single click made on the node within the GUI by the user.

In another cases at the network modeling service identifies the activation of the selected network resource via a double click made on a node representing the selected network resource within the GUI. This is a node activation that alters the presentation as discussed above.

At the network modeling service presents a new presentation showing policies and policy relationships for the activated selected network resource.

At the network modeling service obtains from a user an activation of a select policy within the GUI. The policies presented within the new presentation have interconnections to one another and are related to the activated selected network resource.

At the network modeling service shows a configuration dialogue to the user to alter configuration settings for the activated select policy.

At the network modeling service makes changes to the configuration settings in response to values supplied by the user in the configuration dialogue. Here the user has made changes to the selected policy changes by way of changes in values for the original policy such as conditions and or actions.

At the network modeling service simulates the changes to the activated and selected policy via the values within the network in response to direction within the GUI that is supplied by the user. So the user supplies the values for the changes that the network modeling service uses to then simulate the changed policy configuration within the network.

According to an embodiment at the network modeling service presents results from simulating the changes within the GUI for the user to see.

In one case at the network modeling service identifies some relationships in red. The red color indicating that errors occurred when simulating the changes within the network.

In another cases at the network modeling service identifies some relationships in green indicating success occurred when simulating the changes within the network.

It is noted that the simulation results may include the embodiments of both and within the GUI simultaneously. Thus some relationships are in red and other relations are shown in green. The red showing failures and the green showing success.

In an embodiment the policy configuration and simulation system implements among other things the methods and of the respectively.

The policy configuration and simulation system includes a configurator and a simulator . Each of these and their interactions with one another are now discussed in turn.

The configurator is implemented in a computer readable storage medium and executes on the one or more processors of a network. Example processing associated with the configurator was discussed in detail above with reference to the method of the .

The configurator interacts with one or more screens of a GUI accessed by a user and the configurator is configured to accept value changes from configuration settings of policies. The policies are graphically presented in the GUI. Moreover the configurator is also configured to provide the value changes to the simulator .

In an embodiment the configurator is also configured to be activated from a dialogue box after a user selects a particular policy from a particular network resource. The particular policy is selected by the user from modification or alteration with respect to its configuration settings.

In yet another situation the configurator is configured to enforce security against the value changes to ensure that the user has proper access rights to make the value changes provided by the user.

Similarly the configurator is configured to provide a listing of acceptable values from the user to select when providing the value changes.

The simulator is implemented in a computer readable storage medium and executes on the one or more processors of the network. Example processing associated with the simulator was discussed in detail above with reference to the method of the .

The simulator is configured to process the value changes and present results of those value changes to the user within the GUI.

According to an embodiment the simulator is configured to alter presentations within the GUI to depict the results for the user.

Continuing with the previous embodiment the simulator is also configured to uniquely provide visual cues where results fail and succeed within the presentations.

The modeler based policy configurator and simulator techniques presented herein and above are particular well suited for a Lightweight Directory Access Protocol LDAP proxy. This LDAP proxy implementation is shown via the screen shots of the . The show a variety of information such as 1 gives a GUI for a user to configure and simulate complex policies 2 adds removes graph nodes and relationships between nodes connections between nodes 3 gives the user a complete picture of the whole directory configuration for a network in the form of graph nodes and graph connections relationships within a single modular based graphical editor where the relationship and flow of controls are represented by connections 4 lets users configure any section part or portion of the configuration or subsection or relationships just by clicking on the graph node which pops up respective configuration dialog 5 permits the modeler to arrange graph nodes and connections into appropriate stages therefore the user is not confused with what is to come first or last 6 allows zooming out of a graph node when activated double clicked to show all its subsection nodes so the user can also configure the subsections by activating double clicking on the subsection nodes 7 permits the user to activate double click on a respective policy and configure these activated policies via pop up configuration dialogues.

In addition the user can simulate and test policies and configuration in one of two manners. Firstly by providing sample data and starting a simulation operation to get results in the modeler GUI as presented above to show failures and successes. Secondly by connecting live to an LDAP proxy server and passing the configuration for the policies in order to get the results back that are then represented in the modeler GUI as described above .

The below description describes the process of how the policy configurations are modeled and represented into the graph nodes and relationships.

The shows 1 that the user can click on the Listener Group Server and invoke the configuration dialog and start editing the configuration 2 that the user can know the relationships just by clicking on any node with highlighting of all the connection lines relationships that are related with the current node 3 that the changes done in the modeler GUI and are reflected in the configuration represented in eXtensible Markup Language XML .

Policies are set for the LDAP Proxy Server by double clicking on the LDAP PROXY Graph Node. The Graph Node changes its appearance User Interface UI composite with the below shown in the where each node has its child nodes which usually represent the sub sections individual policies . Each policy can be configured by clicking on the icons sub nodes e.g. A B C D. are individual policies which would open a configuration dialog. Once done with the policies the user can double click on the graph node again which brings the GUI back to the original state.

Simulation policies are now discussed. The user can start simulating the policies by sampling a request object with appropriate informational values or configuration setting values. The simulator engine consumes the request object and parses against the policies and the result and routing is depicted on the Modeler Graphical Editor GUI as shown below in the . The green lines indicate the pass and routing as well.

In case of Policy failure or Error the Modeler Editor GUI will look as shown in the . The red lines and cross mark indicates the failure.

The techniques presented herein provide a variety of novell things such as 1 representing a whole network configuration in a single editor modeler or GUI as discussed above with reference to the 2 extending the graph node when double clicked it changes to a well formed UI container to show all its child nodes e.g. policies refer to the .

The techniques presented herein permit policy configuration and simulation within a single GUI or Modeler Editor as shown in the .

Additionally the techniques can be used for any configuration modeling monitoring and or simulation environment and not just directory based environments or LDAP based environments. The techniques and interfaces allow for custom configuration and simulation on any sort of user defined policy.

The above description is illustrative and not restrictive. Many other embodiments will be apparent to those of skill in the art upon reviewing the above description. The scope of embodiments should therefore be determined with reference to the appended claims along with the full scope of equivalents to which such claims are entitled.

The Abstract is provided to comply with 37 C.F.R. 1.72 b and will allow the reader to quickly ascertain the nature and gist of the technical disclosure. It is submitted with the understanding that it will not be used to interpret or limit the scope or meaning of the claims.

In the foregoing description of the embodiments various features are grouped together in a single embodiment for the purpose of streamlining the disclosure. This method of disclosure is not to be interpreted as reflecting that the claimed embodiments have more features than are expressly recited in each claim. Rather as the following claims reflect inventive subject matter lies in less than all features of a single disclosed embodiment. Thus the following claims are hereby incorporated into the Description of the Embodiments with each claim standing on its own as a separate exemplary embodiment.

