---

title: Method and apparatus for rating URLs
abstract: A method of providing rating information in respect of Uniform Resource Identifiers to a client terminal. The method includes identifying a Uniform Resource Identifier at the client terminal, sending a first query to a rating server over an IP network, the query including as a query string a first component of the identified Uniform Resource Identifier or a derivative of that first component, and receiving the first query at the rating server and determining whether or not a rating exists for the query string. A response is sent by the server to the client terminal, the response including a determined rating, or an indication that no rating exists. The response is received at the client terminal and, if a rating included in the response so indicates or if the response otherwise so indicates, then a further query is sent to the rating server, the further query including as a query string said first component and a second component of the identified Uniform Resource Identifier, or a derivative of the first and second components. The steps of receiving the first query at the rating server, sending a response, and receiving the response at the client terminal, are repeated one or more times as required, adding for each iteration a further component to the query string.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09461966&OS=09461966&RS=09461966
owner: F-SECURE OYJ
number: 09461966
owner_city: Helsinki
owner_country: FI
publication_date: 20090508
---
The present invention relates to a method and apparatus for rating Uniform Resource Locators URLs . More particularly the invention relates to a method and apparatus for rating URLs in a client server based architecture according to which a multiplicity of clients request URL ratings from a common server or server set.

Whilst providing a great many benefits to individuals and organisations the Internet can be a source of both hidden and known dangers. On the one hand much of the content available on the Internet is of an undesirable nature whilst on the other web pages can be a source of malware including spyware trojans viruses etc. One mechanism for defending against these problems is to perform a rating on Uniform Resource Locators URLs entered into a web browser on a client terminal and to present the rating information to the user before downloading the associated web page and or filter access requests in dependence upon the rating results.

US2008 0163380 describes one such approach involving URL ratings. This involves providing a URL Rating Server which maintains a database of known URLs and their ratings. Client terminals request ratings from the Rating Server for example prior to downloading a web page. In order to reduce waiting times on the client side a URL cache is built up in the client terminal based both on previously accessed and trusted URLs and pre populated URL rating data obtained for example based on a user s profile.

Known approaches to providing URL ratings using a client server approach suffer from the disadvantages that the database of rated URLs must be extremely large and that it is extremely difficult to maintain a reliable database given the ever changing nature of the Internet. The massive growth in web 2.0 sites in particular causes a significant problem for conventional URL rating systems given that dubious and dangerous content can be introduced to the Internet and subsequently removed over extremely short time periods. In fact known approaches are to a large extent ineffective in view of the changing use patterns now seen with the Internet.

It is an object of the present invention to overcome or at least mitigate the above noted disadvantages of known YRL rating methods. This is achieved at least in part by seeking to identify rated URLs that match component parts of URLs that clients seek to rate. Such rated URLs may be provided to clients to transfer at least a part of the computational load required to rate a URL from a back end server to the clients.

According to a first aspect of the present invention there is provided a method of providing rating information in respect of Uniform Resource Identifiers to a client terminal the method comprising 

Embodiments of the present invention may in a large number of cases reduce the time taken to rate a URL. Rating of a full URL may be required in only a limited number of cases.

The queries sent to the rating server may contain derivatives of the respective query strings each derivative being obtained by applying a hashing function to the corresponding query string.

Said first component may comprises a registered domain name or registered IP address. Said second and any further component may comprise further sub components prefixed to said first component.

The method may involve at the rating server if it is determined that a rating exists for the query string and that a second or further component is required to refine the rating including in the response a format definition for a further query.

The method may involve upon receipt of a response at the client terminal caching in a local cache any determined rating together with the associated query string or derivative. At the rating server if it is determined that a rating exists for the query string and that a second or further component is required to refine the rating a format definition for a further query may be included in the response and additionally cached in the local cache the format definition.

The method may comprise between steps 1 and 2 querying said local cache to determine whether or not it contains an entry for a component of the Uniform Resource Identifier or a derivative of that component and 

In an embodiment of the invention the client terminal comprises a web browser and the method further comprises displaying in a web browser window a determined rating. The method may comprise the further steps of 

The Uniform Resource Identifier or a derivative of the Uniform Resource Identifier may be included in said first query sent to the rating server. In this case the method may comprise at said rating server determining whether or not a rating exists for the Uniform Resource Identifier or its derivative prior to determining whether or not a rating exists for the query string and if so then returning a response containing the rating to the client terminal.

According to a second aspect of the present invention there is provided a method of providing rating information in respect of Uniform Resource Identifiers to a client terminal. The method comprises receiving at the client terminal from a network server ratings in respect of Uniform Resource Identifiers and caching the received ratings at the client terminal within a client cache. The method further comprises for a Uniform Resource Identifier identified at the client terminal for which a rating is required 

The extended Uniform Resource Identifier may correspond to the identified Uniform Resource Identifier.

The method of the second aspect may comprise further extending the extended URI in dependence upon further results and repeating the query of the client cache or sending a query to the rating server.

According to a third aspect of the present invention there is provided a computer program for causing a computer to perform the steps of 

According to a fourth aspect of the present invention there is provided computer readable recording medium having stored thereon instructions for causing a computer to 

According to a fifth aspect of the present invention there is provided method of providing ratings in respect of Uniform Resource Identifiers to client terminals the method comprising 

There is illustrated in a typical client server architecture for providing a URL rating service. A multiplicity of client terminals which may be mobile phones PDAs laptops PCs etc are able to access the Internet via some appropriate access network s not shown in the Figure . Also coupled to the Internet is an ORSP FE URL rating server operated by a third party service provider e.g. a vendor of antivirus and security products and services. Each terminal is typically provided with a web browser that allows a user to download view and interact with web pages. A web browser is also provided with certain new functionality for optimising the rating process and enhancing the user experience. This functionality will now be described.

Every URL is made up of some combination of the following a scheme name or resource type a registered domain name or Internet Protocol IP address the port number the pathname of the file to be fetched or the program to be run the query string including query parameters and with html files an anchor for where the page should be displayed at. The combined syntax may be as follows 

As has been noted above even where a domain name or IP address is trusted as is the case for example with youtube.com or wikipedia.com content behind the domain name or IP address may not. It is also possible that the same web page may be pointed to by a large number of different URLs.

It is possible to reduce the number of rating queries that a client sends to the URL rating server by identifying those URL components behind which all URLs are trusted or not trusted and caching these at the client. When a user enters a URL into a browser appropriate components of the URL are compared against the cached components. If a match is found the cached rating can be presented to the user or filtering action taken without the need for the client to send a query to the rating server. Only if a match is not found need a query be sent.

It would be possible to build the cache at the client by causing the client to send a complete URL to the rating server in the event that a match is not found. This process is illustrated in where at steps 1 to 3 9 and 10 the client terminal determines whether a local URL rating cache contains an entry for a component of the URL. If not the client sends the URL to the rating server step 4 . The rating server could then split the URL into various components and compare those components against the contents of its database step 5 . The rating server would then return step 6 to the client one or more components together with their ratings. The results are received and cached by the client step 7 and the URL allowed or blocked accordingly step 8 . So for example if a user enters the URL 

Improved lookup speeds may be obtained by storing hashes of URL components and generating corresponding hashes from the received URL. The client cache also contains hashes. The client may in addition to the plaintext URL include in the query a hash of the URL components up to the point that it does not find a match in the local cache. The rating server then commences the search from that hash onwards. Only matches that are not previously known to the client are returned to it by the rating server.

In order to provide a very quick initial check the client may send a hash of the complete URL to the rating server together with the plaintext URL. The rating server performs a quick search for the hash and if the result is that the URL is trusted or not trusted this is returned immediately to the client. Only if a match for the hash is not found by the rating server is a search performed using the URL components.

Whilst this approach may work in principle in practice it opens a security threat as it is necessary for the client to send the complete URL in plain text in order to allow the URL rating server to parse the URL. In some instances a URL may contain sensitive data such as a user s bank username and password. Whilst some approaches to URL rating require that the client cipher the sent URL e.g. by applying a hashing function over the URL and sending only the result this is not possible with the approach described in the preceding paragraph as the URL rating server will be unable to parse the URL components where the URL is previously unknown to the rating server. If ciphering is used then the rating server must store a rating for each and every rated URL.

A solution to this problem is to break up the URL query into a number of sub queries. This approach is illustrated in where a user first enters a URL step into the address line of the browser or clicks on a web link . In the case of the example considered above and again assuming that the client using the client cache is unable to rate the URL the client determines step that it must send to the rating server a query containing the domain level marks clerk.com . The client applies a rule set in this step in order to take account of hierarchical top level domain name structures such a .co.uk . Rather than send the domain name part in plain text the client sends only a hash of the component step . Upon receipt of the query an ORSP Front End FE at the rating server compares step the received hash against a database of hashes corresponding to rated URLs. In this example the hash of marks clerk.com is present in the database together with a trusted rating. The rating server responds to the client step with the rating. The client presents the rating to the user and downloads the requested web page step . In addition the hash of the domain name part is stored together with the rating in the client cache step . The user can now freely surf all URLs behind the marks clerk.com domain without any further queries having to be sent to the URL rating server.

Consider now the case where the user enters a URL of a community web 2.0 website into the browser. The following sequence illustrates such a situation 

Considering the components of the client in more detail the browser plugin represents a thin component whose role is to identify and extract URLs from the browser pass queries to the ORSP client receive rating responses from the ORSP client and update the browser display according to received ratings including downloading blocking web pages . The ORSP client is responsible for parsing URLs hashing components querying the local cache and querying the rating server. The ORSP client may be a service provided on the Windows platform and communicates with the browser plugin via an appropriate Application Programming Interface API . The local client cache is stored by the ORSP client in the memory cache .

It will be appreciated that anyone snooping traffic between the client terminal and the rating server will only see hashed URL components and not the components themselves. In the event that the rating server possesses a rating for a received hash the rating server will be able to identify the corresponding URL component. In that case it is unlikely that disclosure of the URL component is of concern to the user. Sensitive URL component are very unlikely to be know to the rating server.

It will also be appreciated by the person of skill in the art that various modifications may be made to the above described embodiment without departing from the scope of the present invention. For example an initial sub query sent from the client to the rating server may additionally include a hash of the complete URL. The rating server may then perform an initial quick search for that hash returning a result immediately to the client if a rating for that URL exists. Only if a rating is not found does the server proceed to perform a look up based on the domain level.

The ORSP client may be implemented as a standalone application on the client terminal on the client terminal. Alternatively the ORSP may be implemented as a browser plugin applet etc.

The URL rating server may maintain a set of rating categories indicative of the trust associated with a rated URL. For example the following six categories may be used 

The colour associated with each category defines a colour that is displayed in a traffic light trust indicator added to the browser buttons by the ORSP client.

A rating provided to the client by the URL rating server may include a time to live TTL value. This indicates to the client a duration for which the rating can be trusted and is stored in the client cache. When a URL entered into the browser matches or includes a component that matches a hash for which the TTL has expired the client will repeat the query procedure with the rating server updating the cache entry according to the result. The client may also periodically initiate updates of expired cache entries.

Critical cache updates may be pushed to the client by the rating server. This may apply for example to newly discovered malicious domain names. Alternatively such critical updates may be provided en bloc the next time that a client makes an ordinary query to the rating server.

It will be further appreciated that the rating procedure described here may be applied to rate URLs associated with application services other than a web browser. For example the procedure may be applied to rate URLs and web data contained within emails. In this case a thin plugin type component may be implemented in an email client such as Microsoft Outlook with the component communicating with the ORSP client. The ORSP client may be shared by multiple applications and services.

