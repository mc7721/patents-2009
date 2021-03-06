---

title: Techniques for using database metric results
abstract: Techniques for using database metric results are provided. Structure Query Language (SQL) statements are parsed for multiple metric calculations. Each metric calculation is dynamically processed against a database to obtain combined results. The combined results are fed to remaining portions of the SQL statements as a source for or a driver to the remaining portions of the SQL statements.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08595217&OS=08595217&RS=08595217
owner: Teradata US, Inc.
number: 08595217
owner_city: Dayton
owner_country: US
publication_date: 20090109
---
A portion of the disclosure of this patent document contains material that is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyright rights whatsoever. The following notice applies to the example screen shots for a report tool as described below and in any drawings hereto Copyright 2008 Teradata Inc. All Rights Reserved.

Enterprises now track all aspects of their business electronically. Every transaction with a customer information about the customer inventory capital expenses etc. are captured indexed and stored in an enterprise s database. Very quickly the enterprise s database becomes enormous in size having a plethora of information. Accordingly enterprises are increasingly relying on their information for driving and managing all aspects of their business operations.

In fact enterprises often develop reports and real time statistics from their databases. Typically the interface for achieving these reports and statistics is a Structured Query Language SQL . Often analysts develop complex SQL statements that execute against the database for purposes of gaining different insight into the details of the business.

These SQL statements can include a variety of nested and complex rules and may rely on results from prior SQL queries. Unfortunately users are generally not permitted to use metric results as a source or driver to the complex rules embedded in SQL statements.

So users may have to iterate may have to develop many different sets of SQL statements to account for results that may be needed. This is time consuming and inefficient.

In various embodiments techniques for using database metric results are provided. More particularly a method for using database metric results is provided. Specifically Structured Query Language SQL statements are received and a first metric calculation and a second metric calculation are identified in the SQL statements. The first metric calculation and the second metric calculation are a source for a target rule within the SQL statements. Next the first metric calculation and the second metric calculation are processed against a database and results are used as the source that is fed to the target rule within the SQL statements and the target rule is processed with the results.

A database as used herein refers to a relational database. In an embodiment the database uses a Structured Query Language SQL interface.

A statement is a set of SQL operations that are capable of being processed by a database s Application Programming Interface API to perform database operations such as queries. The results associated with processing the statement s can be reports statistics other database tables etc.

A rule is a conditional comparison identified in a statement such as If X then Y or When X Do Y and the like. Rules can have labels and can be accessed by reference or via a name from statements and some rules can incorporate other rules such as When Rule X Do Rule Y etc. So rules can be accessed by reference nested simple complex etc. and the rules are embedded in statements.

It is within this initial context that the processing associated with the rule ordering service is now discussed in detail.

At the database metric service receives Structured Query Language SQL statements. The database metric service can acquire or receive the SQL statements in a variety of manners.

For example at the database metric service interacts with a user via a Graphical User Interface GUI to receive the SQL statements. In other cases a user submits the SQL statements via an application or via a command line operation that the database metric service intercepts and processes in the manners discussed herein and below.

At the database metric service identifies a first metric calculation and a second metric calculation in the SQL statements. Both the first metric calculation and the second metric calculation are used within the SQL statements as a source for a target rule that is also present in the SQL statements.

For example a user via the SQL statements may define multiple rules within a Direct Expense DE metric that targets Accounts from a database. A metric result is defined as the sum of those two rules at the account level. So the metric result for Account 10001 is the sum of the result of rule 1 for account 1001 and the result of rule 2 for account 1001.

Previously users were only capable of having a single previous rule within a metric as a source. Rules might have been capable of being chained but were limited to stay within the metric. Just a single rule was capable of being specified. Metric results were only used as a drive in the case of special Indirect Expense IE rules.

The database metric service allows users to create complex rule chains. So instead of a single previous rule now multiple previous rules from multiple metrics may be used as either the source or the driver. For example the user can specify as a source the sum of the results of an Other Revenue OR rule the results of an Allocated Capital AC rule and the results of an AB rule. In a same rule a driver can be specified as the sum or the results of a Direct Expense DE rule and the results of an OR rule.

In addition one or more metric results can be used as either the source of the driver to other portions of the SQL statements. This allows the user to specify for example the results for NIR and OR as a source for a given rule. The results are summed at an object modifier level and uses as the source. In another example OR and DE metric results are used as a driver.

So a source can be the sum of a set of metric results while the driver can be a set of previous rules and likewise a source can be a set of previous rules while a driver can be a sum of a set of metric results.

When multiple metric results are used to create a source or driver the results are summed. Results are stored with a positive sign for the expected result. For example DE IE and Risk Provision RP are stored with a positive number albeit these numbers reflect expense items. When multiple previous metrics are summed an appropriate sign is applied to the incoming value so that the summing metrics for income and expense metrics can be done properly. As an example if a rule used to combine metric results of OR AC and DE as a driver the calculation is Driver Amount OR AC DE for each object number modifier .

So while the DE result may be stored as a positive number the result is multiplied by a sign adjustment value.

Thus as described herein above and below the database metric service permits complex rule chaining by expanding current source and driver options and allowing users the following additional capability when selecting source and driver amounts 

According to an embodiment at the database metric service parses the SQL statements to identify a first rule that defines the first metric calculation and to identify a second rule that defines the second metric calculation.

In another case and as discussed above at the database metric service identifies the first metric calculation as a metric for IE DE AC or RP.

Continuing with the embodiment at and at the database metric service also identifies the second metric calculation as a different metric from that which is associated with the first metric calculation. That is the first and second metric calculations are different from one another.

In still another situation at the database metric service recognizes two different rules that define the first metric calculation within the SQL statements. That is when evaluating the first metric calculation multiple or even chained and complex rules are evaluated for the first metric calculation. This can also be the case with the second metric calculation.

At the database metric service processes the first metric calculation and the second metric calculation against a database. Results associated with processing the first and second metric calculations are then used as a source to another target rule identified within the SQL statements. The target rule is also processed with the SQL statements.

According to an embodiment at the database metric service sums the first metric calculation and the second metric calculation to obtain the results. The results are provided as the source to the target rule when processing the remaining portions of the SQL statements.

So multiple metrics are capable of being used within SQL statements and the results associated therewith can be used as the source to other portions of the same SQL statements. Previously this was not capable.

The database results service provides another and in some cases enhanced perspective to the database metric service represented by the method of the discussed in detail above.

At the database results service dynamically parses SQL statements to obtain a first metric calculation and a second metric calculation.

According to an embodiment at the database results service recognizes the first metric calculation as a first rule that is to be evaluated when the first metric calculation is processed. The first metric calculation can also be multiple first rules or an entire complex chain of first rules.

Continuing with the embodiment at and at the database results service recognizes the second metric calculation as a second rule that is to be evaluated when the second metric calculation is processed. Again the second rule can include multiple second rules or an entire chain of complex second rules.

At the database results service processes the first metric calculation and the second metric calculation against a database. First results acquired from processing the first metric calculation are then summed with second results acquired from processing the second metric calculation. The sum provides combined results.

In an embodiment at the database results service produces the combined results as a source to other portions of the SQL statements.

In another case at the database results service produces the combined results as a driver to other portions of the SQL statements.

According to an embodiment at the database results service processes a first rule chain which represents a set of rules when calculating the first metric calculation.

Continuing with the embodiment at and at the database results service processes a second rule chain which represents another set of rules when calculating the second metric calculation.

At the database results service uses the combined results as input to other portions of the SQL statements when processing the other portions against the database.

The database metric results system includes a SQL preprocessor and a database . Each of these and their interactions with one another will now be discussed in detail.

The SQL preprocessor is implemented in a computer readable storage medium and executed by a processor of a network. Example aspects of the SQL preprocessor were presented in detail above with reference to the methods and of the respectively. Moreover an example implementation of the SQL preprocessor is presented below after the discussion of the .

The SQL preprocessor iterates SQL statements to automatically and dynamically identify and process multiple metric calculations against the database . This produces combined results that feed other portions of the SQL statements when those other portions of the SQL statements are processed.

According to an embodiment the SQL preprocessor iterates the SQL statements to process multiple sets of rules for each of the metric calculations. So each metric calculation can include multiple sets of chained and complex rules that are evaluated when resolving each metric calculation.

In another case the SQL preprocessor feeds the combined results as a source input to a rule that represents the other portions of the SQL statements.

In yet another situation the SQL preprocessor feeds the combined results as a driver to the remaining portions of the SQL statements.

In an embodiment the SQL preprocessor interacts with a user via a graphical user interface GUI to interactively acquire the SQL statements.

The database is implemented in a computer readable storage medium and is accessible to the SQL preprocessor . Example aspects of the database were presented above with reference to the methods and of the respectively.

According to an embodiment the database is a data warehouse that includes a collection of databases logically organized and accessible as a single unit.

It is understood that other embodiments may be used to achieve the teachings presented herein and above and that the example source code presented below is but one implementation capable with the teachings presented. The source code that follows is presented as one example implementation of the teachings presented herein.

The above description is illustrative and not restrictive. Many other embodiments will be apparent to those of skill in the art upon reviewing the above description. The scope of embodiments should therefore be determined with reference to the appended claims along with the full scope of equivalents to which such claims are entitled.

The Abstract is provided to comply with 37 C.F.R. 1.72 b and will allow the reader to quickly ascertain the nature and gist of the technical disclosure. It is submitted with the understanding that it will not be used to interpret or limit the scope or meaning of the claims.

In the foregoing description of the embodiments various features are grouped together in a single embodiment for the purpose of streamlining the disclosure. This method of disclosure is not to be interpreted as reflecting that the claimed embodiments have more features than are expressly recited in each claim. Rather as the following claims reflect inventive subject matter lies in less than all features of a single disclosed embodiment. Thus the following claims are hereby incorporated into the Description of the Embodiments with each claim standing on its own as a separate exemplary embodiment.

