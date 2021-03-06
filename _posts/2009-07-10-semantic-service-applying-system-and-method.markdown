---

title: Semantic service applying system and method
abstract: The present invention relates to a semantic service applying system and a method, comprising: a semantic service pipeline manager which demands and receives a particular semantic service pipeline to and from a semantic service server, and stores the corresponding pipeline in a database to manage the stored pipeline; a semantic service pipeline provider which extracts corresponding semantic service pipelines and sends the extracted pipelines to the corresponding service server if the user requests at least one of a plurality of semantic service pipelines to be provided; and a database which stores information associated with a semantic service pipeline providing server as well as the semantic service pipelines, and thus various ontology-based semantic services can be applied to the web.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08402113&OS=08402113&RS=08402113
owner: Korea Institute of Science and Technology Information
number: 08402113
owner_city: Daejeon
owner_country: KR
publication_date: 20090710
---
The present invention relates to a semantic service application system and method and more particularly to a semantic service application system and method for selecting collecting and managing a semantic service pipeline in which semantic services distributed among a plurality of service servers are combined and for applying the semantic service pipeline to a web frame or a web page.

Web service is a method of providing service using a standard protocol on the web and is commonly used when web applications are constructed. A search Application Programming Interface API or an API executing a specific command widely adopts the web service method.

With the development of the Internet APIs adopting web service are increased and services using the API are further increased.

Accordingly the creation of new services through web service combinations is emerging as an important issue. This is because services created through the web service combinations have great costs versus effects as compared with services newly constructed.

A task of finding a proper combination based on web services where a web service combination is described in a syntactic way becomes static or the task has limitation to dependency on a manual task.

In order to overcome this there has recently been made an attempt to access a web service description such as OWL S in a semantic way using OWL through standardization organizations such as W3C.

There is however also a limit to the attempt. This is because the subject of the description itself is not semantic service but common web service.

In other words there is not proposed a method of intelligently attempting a web service combination because semantic service providing a search API or a reasoning API based on ontology is not taken into consideration.

Consequently there is an urgent need for technical support for creating new semantic service through a combination of ontology based semantic services that are expected to abruptly increase in the future but there is no method of supporting the urgent need using the prior art.

The present invention has been made in view of the above problems occurring in the prior art and an object of the present invention is to provide a semantic service application system and method for generating semantic service pipelines in which ontology based semantic services distributed among service servers are combined for selecting collecting and managing a specific semantic service pipeline from among the generated semantic service pipelines and for applying the specific semantic service pipeline to a web frame or a web page.

Another object of the present invention is to change a factor of a semantic service pipeline so that the semantic service pipeline is suitable for the subject to which the semantic service pipeline will be applied.

To achieve the above objects a semantic service application system of the present invention comprises a semantic service server for collecting pieces of ontology based semantic service information and ontology from a plurality of service servers registering the pieces of ontology based semantic service information and ontology generating semantic service pipelines based on a plurality of semantic services according to a condition inputted by a user and executing a specific semantic service pipeline 

a semantic service pipeline providing server for requesting the semantic service server to execute the specific semantic service pipeline receiving a result of the execution determining whether to select the specific semantic service pipeline receiving the specific semantic service pipeline by requesting the specific semantic service pipeline from the semantic service server if the specific semantic service pipeline is determined to be selected and storing the specific semantic service pipeline and

the service server for receiving a specific semantic service pipeline by requesting the specific semantic service pipeline from the semantic service pipeline providing server and incorporating the receive semantic service pipeline into its specific web frame or web page.

a semantic service pipeline management unit for receiving the specific semantic service pipeline by requesting the specific semantic service pipeline from the semantic service server storing the received semantic service pipeline in a database and managing the stored semantic service pipeline 

a semantic service pipeline providing unit for when the user requests one or more of a plurality of the semantic service pipelines to be provided extracting the relevant semantic service pipelines from the database and transmitting the relevant semantic service pipelines to a relevant service server and

the database for storing information associated with the semantic service pipeline providing server including the semantic service pipelines.

a semantic service pipeline selection unit for selecting the specific semantic service pipeline to be managed by the semantic service pipeline providing server from among the plurality of semantic service pipelines provided on the semantic service server.

request the specific semantic service pipeline from among the plurality of semantic service pipelines provided on the semantic service server to be executed and determine whether to select the specific semantic service pipeline based on the result of the execution received from the semantic service server.

request a change of a factor and an execution of the specific semantic service pipeline from among the plurality of semantic service pipelines provided on the semantic service server and determine whether to select the specific semantic service pipeline based on the result of the execution received from the semantic service server.

According to another aspect of the present invention provides a semantic service pipeline providing server coupled to a semantic service server and a plurality of service servers over a communication network and configured to provide semantic service pipelines the semantic service pipeline providing server comprising 

a semantic service pipeline management unit for receiving a specific semantic service pipeline by requesting the specific semantic service pipeline from the semantic service server storing the received semantic service pipeline in a database and managing the stored semantic service pipeline 

a semantic service pipeline providing unit for when a user requests one or more of a plurality of the semantic service pipelines to be provided extracting the relevant semantic service pipelines from the database and transmitting the relevant semantic service pipelines to a relevant service server and

the database for storing information associated with the semantic service pipeline providing server including the semantic service pipelines.

further comprise a semantic service pipeline selection unit for selecting the specific semantic service pipeline to be managed by the semantic service pipeline providing server from among the plurality of semantic service pipelines provided on the semantic service server.

request the specific semantic service pipeline from among the plurality of semantic service pipelines provided on the semantic service server to be executed and determine whether to select the specific semantic service pipeline based on a result of the execution received from the semantic service server.

request a change of a factor and an execution of the specific semantic service pipeline from among the plurality of semantic service pipelines provided on the semantic service server and determine whether to select the specific semantic service pipeline based on the result of the execution received from the semantic service server.

Yet another aspect of the present invention provides a semantic service application method of a semantic service application system including a semantic service server a semantic service pipeline providing server and service servers providing semantic services the semantic service application method comprising the steps of 

a the semantic service server collecting pieces of ontology based semantic services and ontology distributed among a plurality of the service servers registering the pieces of ontology based semantic services and ontology and generating semantic pipelines by combining one or more of the semantic services according to a specific condition 

b the semantic service pipeline providing server requesting a specific semantic service pipeline from among a plurality of semantic service pipelines provided on the semantic service server to be executed and checking a result of the execution 

c the semantic service pipeline providing server receiving the executed semantic service pipeline by requesting the executed semantic service pipeline and storing the received semantic service pipeline and

d the service server receiving a specific semantic service pipeline by requesting the specific semantic service pipeline from the semantic service pipeline providing server and applying the received semantic service pipeline to its web frame or web page.

the semantic service application method further comprise the step of selecting the specific semantic service pipeline to be managed by the semantic service pipeline providing server based on the result of the execution of the specific semantic service pipeline.

the semantic service application method further comprise the steps of the semantic service pipeline providing server checking the result of the execution and requesting a change of a factor and an execution of the specific semantic service pipeline 

the semantic service server incorporating the factor requested to be changed by the semantic service pipeline providing server into the specific semantic service pipeline executing the specific semantic service pipeline and transmitting a result of the execution to the semantic service pipeline providing server and

the semantic service pipeline providing server selecting the specific semantic service pipeline to be managed by the semantic service pipeline providing server based on the result of the execution of the specific semantic service pipeline.

As described above the semantic service application system and method of the present invention generate semantic service pipelines in which ontology based semantic services distributed among service servers are combined select collect and manage a specific semantic service pipeline from among the generated semantic service pipelines and apply the specific semantic service pipeline to a web frame or a web page. Accordingly an effect that a variety of ontology based semantic services can be applied to the web can be expected.

Furthermore the present invention has effects that a factor of a semantic service pipeline can be changed so that the semantic service pipeline is suitable for the subject to which the semantic service pipeline will be applied and the semantic service pipeline can be actually applied to service embodiments.

Preferred embodiments of the present invention are described in detail with reference to the accompanying drawings.

Semantic service disclosed in the present invention is defined as service in which ontology information is used as an input factor parameter and an output factor and the ontology information is utilized for providing service.

Here the ontology information of the input factor is essential and the ontology information of the output factor is optional. Furthermore a search API includes the ontology information in the input factor but does not utilize the output factor or the ontology information.

Meanwhile not the ontology but a common API may also be used as the input factor and the output factor according to the necessity of an operator.

For example ontology based semantic services use semantic information in the input factor and output results. In case of semantic service that finds experts for specific research subjects a Uniform Resource Identifier URI that is an ontology standard identification system is used as the input factor and identifiers are provided as the output results using the URI.

Here ontology is a specification that is explicitly standardized in order to provide a concept for any interest field and the ontology includes an ontology schema and ontology instances.

The ontology instance means a real value or an entity that is matched with ontology classes and the ontology classes mean a concept from among elements forming the ontology schema.

First is a diagram showing the construction of a semantic service application system according to the present invention.

As shown the semantic service application system includes a semantic service server service servers and a semantic service pipeline providing server .

More particularly the semantic service server collects pieces of ontology based semantic service information and ontology from the plurality of service servers registers the pieces of ontology based semantic service information and ontology generates semantic service pipelines based on a plurality of semantic services according to a condition inputted by a user and executes a specific semantic service pipeline.

Here the plurality of service servers means the subjects from which the semantic services will be collected and generally means all servers such as a server that provides a various portal services a server that provides specific education data and a server that provides search service.

Furthermore the plurality of service servers may be identical with or different from reference numeral .

The semantic service pipeline providing server requests the semantic service server to execute a specific semantic service pipeline receives a result of the execution and determines whether to select the specific semantic service pipeline based on a result of the execution. If the specific semantic service pipeline is determined to be selected the semantic service pipeline providing server requests the relevant semantic service pipeline from the semantic service server and receives and stores the relevant semantic service pipeline.

The service server requests a specific semantic service pipeline from the semantic service pipeline providing server receives the specific semantic service pipeline and incorporates the received semantic service pipeline into its specific web frame or web page.

For example the service server applies a semantic service pipeline of a script language form received from the semantic service pipeline providing server to a web frame or web page and when the relevant web frame or web page is selected by a user calls and executes the Application Programming Interface API of the semantic service pipeline.

As shown the semantic service server includes a semantic service management unit a semantic broker and a semantic service license unit .

More particularly the semantic service management unit registers deletes and edits ontology based semantic service information and ontology and supports information search performed by the semantic broker .

Here the semantic service information includes a semantic service name an input item an output item a property a visualization type reference ontology and a service specification.

Furthermore the semantic service management unit further collects an ontology reference Application Programming Interface API and stores the collected ontology reference API in an additional repository.

If an ontology reference API does not exist the semantic service management unit stores relevant instance information itself.

The semantic broker searches for semantic services through the semantic service management unit combines the retrieved semantic services and provides a result as any one of a combined semantic service or a semantic workflow.

When a user inputs a condition including an input factor according to preset items the semantic service license unit requests a result by transmitting the relevant condition to the semantic broker and receives and outputs the relevant result.

More particularly when the semantic service license unit transmits the condition to the semantic broker the semantic broker generates a semantic service pipeline matched with the condition and transmits the generated semantic service pipeline to the semantic service license unit .

Furthermore the semantic service license unit requests the semantic broker to execute a specific semantic service pipeline of a plurality of semantic service pipelines and receives a result of the execution.

The result of the execution of the semantic service pipeline is any one of a graph form a group form a grid form a network form a list form a map form a browsing form a tag cloud form and a tree form.

An example where the semantic service management unit the semantic broker and the semantic service license unit disclosed in are implemented on one server has been described but they may be separately configured according to an intention of an operator.

As shown the semantic service pipeline providing server includes a semantic service pipeline selection unit a semantic service pipeline management unit a semantic service pipeline providing unit and a database .

More particularly the semantic service pipeline selection unit selects a specific semantic service pipeline to be managed by the semantic service pipeline providing server from among a plurality of semantic service pipelines provided on the semantic service server .

Furthermore the semantic service pipeline selection unit requests the execution of a specific semantic service pipeline from among a plurality of semantic service pipelines provided on the semantic service server and determines whether to select the specific semantic service pipeline based on a result of the execution received from the semantic service server .

In addition the semantic service pipeline selection unit requests a change of factors and the execution of a specific semantic service pipeline from among a plurality of semantic service pipelines provided on the semantic service server and determines whether to select the specific semantic service pipeline based on a result of the execution received from the semantic service server .

The semantic service pipeline management unit requests a specific semantic service pipeline from the semantic service server receives the specific semantic service pipeline stores the specific semantic service pipeline in the database and manages the specific semantic service pipeline.

When a user requests the semantic service pipeline providing unit to provide one or more of a plurality of semantic service pipelines the semantic service pipeline providing unit extracts relevant semantic service pipelines from the database and transmits the extracted semantic service pipelines to the relevant service server .

The database stores information associated with the semantic service pipeline providing server including the semantic service pipelines.

First the semantic service server collects pieces of ontology based semantic services and ontology distributed among the plurality of service servers registers the pieces of ontology based semantic services and ontology and generates semantic pipelines by combining one or more semantic services according to a specific condition S .

Next the semantic service pipeline providing server requests the execution of a specific semantic service pipeline from among a plurality of semantic service pipelines provided on the semantic service server and checks a result of the execution S .

The semantic service pipeline providing server determines whether to select the specific semantic service pipeline to be managed by the semantic service pipeline providing server based on the result of the execution of the specific semantic service pipeline S .

If the specific semantic service pipeline is determined to be selected the semantic service pipeline providing server performs step S.

The semantic service pipeline providing server requests and stores the executed semantic service pipeline S S .

The service server requests the specific semantic service pipeline from the semantic service pipeline providing server receives the specific semantic service pipeline and applies the received semantic service pipeline to its web frame or web page S S .

For example the service server applies a semantic service pipeline of a script language form received from the semantic service pipeline providing server to a web frame or web page so that the Application Programming Interface API of the applied semantic service pipeline is selected when a user selected the relevant web frame or web page.

First the semantic service server collects pieces of ontology based semantic services and ontology distributed among the plurality of service servers registers the pieces of ontology based semantic services and ontology and generates semantic pipelines by combining one or more semantic services according to a specific condition S .

Next the semantic service pipeline providing server requests the execution of a specific semantic service pipeline from among a plurality of semantic service pipelines provided on the semantic service server and checks a result of the execution S .

The semantic service pipeline providing server checks a result of the execution. If the semantic service pipeline needs to be changed the semantic service pipeline providing server requests factor of the semantic service pipeline to be changed and the semantic service pipeline to be executed S S .

This is performed when the result of the execution received from the semantic service server is determined not to meet a selected criterion or a specific factor needs to be changed.

Next the semantic service server incorporates the factor requested to be changed by the semantic service pipeline providing server into the relevant semantic service pipeline executes the relevant semantic service pipeline and transmits a result of the execution to the semantic service pipeline providing server S S .

The semantic service pipeline providing server selects a specific semantic service pipeline to be managed by the semantic service pipeline providing server based on the result of the execution of the semantic service pipeline S .

If the specific semantic service pipeline is selected the semantic service pipeline providing server performs step S.

Meanwhile if the result of the execution received from the semantic service server does not meet a selected criterion or another specific factor needs to be changed the semantic service pipeline providing server performs step S.

The semantic service pipeline providing server requests the executed semantic service pipeline receives the requested semantic service pipeline and stores the received semantic service pipeline S S .

The service server requests a specific semantic service pipeline from the semantic service pipeline providing server receives the specific semantic service pipeline and applies the received semantic service pipeline to its web frame or web page S S .

As described above those having ordinary skill in the art to which the present invention pertains will appreciate that the present invention may be implemented in other detailed forms without changing the technical spirit or indispensable characteristics. Accordingly it should be understood that the above embodiments are only illustrative from all aspects and are not to be restrictive. The scope of the present invention is defined by the following claims rather than the detailed description and the meanings and scope of the claims and all changes or modified forms induced from their equivalents should be interpreted to fall within the scope of the present invention.

