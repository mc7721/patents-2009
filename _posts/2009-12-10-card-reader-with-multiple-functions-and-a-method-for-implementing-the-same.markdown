---

title: Card reader with multiple functions and a method for implementing the same
abstract: The invention discloses a method for implementing a card reader with multiple functions and a card reader therewith. The method includes that a card reader determines whether a card is inserted in the slot of the card reader and whether the card reader is online; if no card is inserted in the slot, the card reader performs operation to generate a one-time password; if a card is inserted in the slot and the card reader is online, the card reader performs corresponding operation on the card according to the card operating requirement, while if a card is inserted in the slot and the card reader is offline, the card reader performs operation with the card to generate a Token; otherwise, to end the process. The card reader includes a power module, an input/output module, a determining module, an operating module, and a performing module. With good common performance, the card reader provided by the invention performs as smart card reader and verification whether a card is inserted in the card reader or not, which overcomes the shortcomings that the card reader in the prior art has simplex function.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08888000&OS=08888000&RS=08888000
owner: Feitian Technologies Co., Ltd.
number: 08888000
owner_city: Beijing
owner_country: CN
publication_date: 20091210
---
The invention relates to information security field and more particularly to a card reader with multiple functions and a method for implementing the same.

With the high speed development of digital information technology the digital information technology broken through the traditional limitation involves the electronic product of commerce trade and consuming fields. At present with the smart card is used more and more widely the smart card is applied in all aspects of human life.

In usage the smart card needs an interface device which is a card reader for supporting the operation of a card. For providing an economic safe and general interface for a card and a computer the card reader is adaptable to all kinds of computer interfaces. With powerful inbuilt software the card reader is compatible to the existed or will be produced smart cards operating systems or industry API Application Programming Interface standards. Now the card reader can be used in fields such as enterprise security PKI infrastructure online banking e business and the like. With the powerful secure and portable smart card consolidate and integrated security policy can be implemented in an organization via the card reader.

When a card reader according to the prior art is applied to a smart card the card reader must be linked to a computer first and then the smart card must be inserted in the card reader. The user can communicate with the smart card by the card reader. All of the application is based on the smart card and the card reader is a transparent channel only. So the function of the card reader is simplified and has narrow application field.

determining by the card reader whether a card is inserted in the slot of the card reader and whether the card reader is online 

performing by the card reader operation to generate a one time password if no card is inserted in the slot of the card reader 

performing corresponding operation on a card according to a card operating requirement sent from a computer if the card is inserted in the slot of the card reader and the card reader is online or

performing operation with a card to generate a Token if the card is inserted in the slot of the card reader and the card reader is offline.

performing operation by the card reader to generate a one time password if no card is inserted in the card reader otherwise

performing by the card reader corresponding operation on the card according to the card operating requirement sent from the computer if the card reader is online 

performing by the card reader operation with the card to generate a Token if the card reader is offline.

determining by the card reader whether a card is inserted in the slot of the card reader if the card reader is online 

performing by the card reader operation to generate a one time password if no card is inserted in the slot 

performing by the card reader corresponding operation on the card according to the card operating requirement sent from the computer if the card is inserted in the slot 

determining by the card reader whether a card is inserted in the slot of the card reader if the card reader is offline 

performing by the card reader operation to generate a one time password if no card is inserted in the slot and

performing by the card reader operation with the card to generate a Token if the card is inserted in the slot.

Preferably before performing by the card reader operation to generate a one time password the method further includes

determining by the card reader whether the user requires to obtain one time password if so performing the step of performing operation to generate a one time password otherwise ending the process and returning to the status of waiting for system call.

Preferably determining by the card reader whether the card reader is online is performed by checking the USB status of the card reader.

Preferably before performing by the card reader corresponding operation on the card according to the card operating requirement sent from a computer the method further includes

determining by the card reader whether an operating requirement is sent from the computer if so performing the step of performing corresponding operation on the card according to the requirement sent from the computer otherwise ending the process and returning to the status of waiting for system call.

Preferably before performing by the card reader operation with the card to generate a Token the method further includes

determining by the card reader whether the user requires verification if so performing by the card reader operating with the cad to generate a Token otherwise ending the process and returning to the status of waiting for system call.

an input output module adapted to receive information entered by the user and further to output a one time password or a Token generated by the card reader 

a determining module adapted to determine whether a card is inserted in the slot of the card reader and whether the card reader is online 

an operating module adapted to perform operation to generate a one time password if the determining module determines that no card is inserted in the card reader and perform operation with the card to generate a Token if the determining module determines that a card is inserted in the slot of the card reader and the card reader is offline and

a performing module adapted to perform corresponding operation on the card according to the card operating requirement sent from a computer if the determining module determines that a card is inserted in the slot of the card reader and the card reader is online.

Preferably the input output module includes a keyboard unit a touching unit a displaying unit and a sound generating unit.

a card inserting determining unit adapted to determine whether a card is inserted in the slot of the card reader and to inform the operating module to perform operating to generate a one time password if no card is inserted in the slot of the card reader and

an online status determining unit adapted to determine whether the card reader is online if the card inserting determining unit determines that the card is inserted in the slot to inform the performing module to perform corresponding operation on the card according to the card operating requirement sent from the computer if the card reader is online while to inform the operating module to perform operation with the card to generate a Token if the card reader is offline.

a card inserting determining unit adapted to determine whether a card is inserted in the slot of the card reader after the determination of the online status determining unit if no card is inserted in the slot of the card reader the card inserting determining unit being adapted to inform the operating module to perform operation to generate a one time password if a card is inserted in the slot of the card reader and the online status determining unit determines that the card reader is online the card inserting determining unit being adapted to inform the performing module to perform the corresponding operation on the card according to the card operating requirement sent from the computer while if a card is inserted in the slot of the card reader and the online status determining unit determines that the card reader is offline the card inserting determining unit being adapted to inform the operating module to perform operation with the card to generate a Token.

a user requirement determining unit adapted to if the determining module determines that no card is inserted in the slot determine whether requirement of obtaining a one time password from the user is received if so the user requirement determining unit inform the operating module to perform operation to generate a one time password otherwise to end the process and return the card reader to the status of waiting for the system call.

Preferably the determining module determines whether the card reader is online by checking the status of the USB of the card reader.

a card operating requirement determining unit adapted if the determining module determines that a card is inserted in the slot and the card reader is online to determine whether a card operating requirement is sent from the computer if so the card operating requirement determining unit being adapted to inform the performing module to perform corresponding operation on the card according to the card operating requirement sent from the computer otherwise to end the process and return the card reader goes back to the status of waiting for the system call.

a verification requirement determining unit adapted if the determining module determines that a card is inserted in the slot and the card reader is offline to determine whether a verification requirement from the user is received if so the verification requirement determining unit being adapted to inform the operating module to perform operation on the card to generate a Token otherwise to end the process and return the card reader to the status of waiting for the system call.

Objects technical solutions and advantages of the invention will be easily understood by reference to the following description of embodiments when read in conjunction with the accompanying drawings.

The embodiment of the invention provides a method of implementing a card reader with such multiple functions that the card reader determines whether a card is inserted in its slot and whether the card reader is online if there is no card in the slot of the card reader the card reader performs operation to generate a one time password if there is a card in its slot and the card reader is online the card reader performs corresponding operation on the card according to the requirement sent from the computer and if there is a card in its slot and the card reader is offline the card reader performs operation with the card to generate a Token.

In the embodiment a card reader has a keyboard and a LCD Liquid Crystal Display . Referring to the embodiment provides a method for implementing a card reader with multiple functions which includes 

Step the card reader determines whether a card is inserted in its slot if so go to Step otherwise go to Step 

Step the card reader determines whether a requirement of obtaining a one time password is received from a user if so go to Step otherwise the card reader end the process and goes back to the status of waiting for system call 

Thereby the user sends a requirement of obtaining a one time password to the card reader which can be implemented by pressing a specified key on the card reader to generate a one time password requirement.

Step the card reader performs OTP one time password operation to generate a one time password and displays the one time password on the LCD then the card reader ends the process and goes back to status of waiting for system call 

Thereby contrasted to the traditional static password the OTP is a dynamic password which is a changeable password. The change of the password is originated from the change of the factor in operation of generating a password. Generally the dynamic password generating algorithm adapts two factors one is the identification code of the user which is fixed such as the private key of user the other is a changeable factor such as time random number or counter value and the like. In the embodiment the method of OTP operation is same as the method of that in the prior art.

Step the card reader determines whether it is online if so go to Step otherwise the card reader is offline go to Step 

the card reader checks its USB Universal Serial Bus status machine and determines whether the USB is enumerated successfully if so that shows that the card reader is online otherwise the card reader is offline.

Step the card reader determines whether a card operation requirement sent from a computer is received if so go to Step otherwise the card reader ends the process and goes back to the status of waiting for the system call 

Step the card reader performs corresponding operation on the card according to the requirement sent from the computer then the card reader ends the process and goes back to system call status 

Step the card reader determines whether a requirement of verification is received from the user if so go to Step otherwise the card reader ends the process and goes back to the status of waiting for system call and

Step the card reader performs operation with the card to generate a Token and displays the Token on the LCD and

In the embodiment the process above can be executed repeatedly after that the process is ended. That the card reader goes back to the status of waiting for system call means that the card reader goes back to Step then the card reader executes the steps in the process described above.

In the embodiment when the card reader is online and a card is inserted in the slot of the card reader if the card reader receives a requirement of obtaining a one time password or a requirement of obtaining a Token the card reader can forbid any requirement or generate and display a one time password or generate a Token with the card and display the Token.

Referring to . the process of Step in which the card reader performs operation with the card to generate a Token includes 

Step the card reader determines the type of the working mode of card verification operation if the type of the working mode is the first mode MODEL go to Step if the type of the working mode is the second mode MODE go to Step if the type of the working mode is the third mode MODE go to Step 

In the embodiment the first mode MODE refers to the working mode that the card reader performs operation according to the data such as a challenge code and a account number and the like and PIN Personal Identification Number code entered by the user to generate a Token the second mode MODE refers to the working mode that the card reader performs operation according the PIN code entered by the user to generate a Token and the third mode MODE refers to the working mode that the card reader performs operation according to the challenge code and PIN code entered by the user to generate a Token.

Step the card reader receives the data such as the challenge code and account number and the like entered by the user and go to Step 

Step the card reader receives the PIN code entered by the user and performs operation with the PIN code then go to Step 

Step the card reader generates AC Application Cryptogram according to the received data and PIN code 

Step the card reader determines whether the working mode of card verification operation is MODE and needs TDS Transaction Data Signing if so go to Step otherwise go to Step 

In the embodiment the verification operation includes but not limited to CAP Chip Authentication Program operation and DPA Dynamic Passcode Authentication . Thereby the CAP which is a method for verifying the identity of a cardholder is an online process. By taking advantages of the verification function of the EMV chip payment card the CAP provides identification verification for remote cardholder and evidence to prove the details of the transaction agreed by the cardholder.

In the embodiment a card reader has a keyboard and a sound generating means. Referring to the embodiment provides a method for implementing another kind of card reader which includes 

Step the card reader determines whether it is online if so go to Step otherwise the card reader is offline go to Step 

the card reader checks its USB Universal Serial Bus status machine and determines whether the USB is enumerated successfully if so that shows that the card reader is online otherwise the card reader is offline.

Step the card reader determines whether a card is inserted in its slot if so go to Step otherwise go to Step 

Step the card reader determines whether a card operation requirement sent from a computer is received if so go to Step otherwise the card reader ends the process and goes back to the status of waiting for the system call 

Step the card reader performs corresponding operation on the card according to the requirement sent from the computer then the card reader ends the process and goes back to system call status 

Step the card reader determines whether a requirement of obtaining a one time password from a user is received if so go to Step otherwise the card reader ends the process and goes back to the status of waiting for system call 

Thereby the user sends a requirement of obtaining a one time password which can be implemented by pressing a specified key on the card reader to generate a one time password requirement.

Step the card reader performs OTP one time password operation to generate a one time password and reads the one time password by sound then the card reader ends the process and goes back to system call status 

Thereby contrasted to the traditional static password the OTP is a dynamic password which is a changeable password. The change of the password is originated from the change of the factor used for the operation of generating a password. Generally the dynamic password generating algorithm adapts two factors one is the identification code of the user which is fixed such as the private key of user the other is a changeable factor such as time random number or counter value and the like. In the embodiment the method of OTP operation is same as the method in the prior art.

Step the card reader determines whether a card is inserted in its slot if so go to Step otherwise go to Step 

Step the card reader determines whether the a requirement of verification is received from the user if so go to Step otherwise the card reader ends the process and goes back to the status of waiting for system call 

Step the card reader performs operation with the card to generate a Token and reads the Token by sound and

In the embodiment the process above can be executed repeatedly after that the process is ended in Step . The step that the card reader goes back to the status of waiting for system call means that the card reader goes back Step then the card reader executes process described above again.

In the embodiment the process of Step that the card reader performs operation with the card to generate a Token is same as the process of that in the embodiment 1. No more further detail is described here.

In the embodiment when the card reader is online and a card is inserted in the slot of the card reader if the card reader receives a requirement of obtaining a one time password or a requirement of obtaining a Token the card reader can forbid to generate a one time password or a Token or generate a one time password and read the one time password by sound or generate a Token with the card and read the Token by sound.

In the embodiment the verification operation includes but not limited to CAP Chip Authentication Program operation and DPA Dynamic Passcode Authentication . Thereby the CAP which is a method for verifying the identity of a cardholder is an online process. By taking advantages of the verification function of the EMV chip payment card the CAP provides identification verification for remote cardholder and evidence to prove the details of the transaction agreed by the cardholder.

Referring to the embodiment of the invention provides a card reader with multiple functions which includes

a power supply module adapted to supply power to the card reader in the embodiment the power for the card reader can be supplied by cells or by the USB interface 

an input output module adapted to receive the data information entered by a user further adapted to output a one time password or a Token generated by the card reader in the embodiment the input output module can receive the information entered by a user by keyboard and display the one time password or the Token generated by the card reader by display or read the one time password or the Token by a sound generating means 

a determining module adapted to determine whether a card is inserted in slot of the card reader to determine whether the card reader is online and to determine whether a requirement of verification from a user is received 

an operating module adapted to perform OTP operation to generate a one time password if the determining module determines that no card is inserted in the slot of the card reader to perform operation with the card to generate a Token if the determining module determines that a card is inserted in the slot of the card reader and the card reader is offline and a requirement of verification is received from the user and

a performing module is adapted to perform corresponding operation on the card according to the card operation requirement sent from a computer if the determining module determines that a card is inserted in the slot of the reader and the card reader is online 

In the embodiment the determining module can determine whether a card is inserted in the slot of the card reader and then determine whether the card reader is online that is the determining module includes

a card inserting determining unit adapted to determine whether a card is inserted in the slot of the card reader and

an online status determining unit adapted to determine whether the card reader is online if the card inserting determining unit determines that the card is inserted in the slot to inform the performing module to perform corresponding operation on the card according to the card operating requirement sent from the computer if the card reader is online to inform the operating module to perform operation with the card to generate a Token if the card reader is offline.

In addition referring to the determining module can determine whether the card reader is online and then determine whether a card is inserted in the slot of the card reader that is the determining module includes

a card inserting determining unit adapted to determine whether a card is inserted in the slot of the card reader after the determination of the online status determining unit if no card is inserted in the slot of the card reader the card inserting determining unit being adapted to inform the operating module to perform operation to generate a one time password if a card is inserted in the slot of the card reader and the online status determining unit determines that the card reader is online the card inserting determining unit being adapted to inform the performing module to perform the corresponding information on the card according to the card operating requirement sent from the computer and if a card is inserted in the slot of the card reader and the online status determining unit determines that the card reader is offline the card inserting determining unit being adapted to inform the operating module to perform operation with the card to generate a Token.

In the embodiment whatever the sequence of the determining steps by the determining module is the determining module can determine whether the card reader is online by checking the USB status of the card reader.

In the embodiment whatever the sequence of determining steps by the determining module is the determining module further includes

a user requirement determining unit adapted to if the determining module determines that no card is inserted in the slot determine whether requirement of obtaining a one time password from the user is received if so the user requirement determining unit informing the operating module to perform operation to generate a one time password otherwise the card reader ends the process and goes back to the status of waiting for the system call.

In the embodiment whatever the sequence of determining steps by the determining module is the determining module further includes

a card operating requirement determining unit which is adapted to if the determining module determines that a card is inserted in the slot and the card reader is online determine whether a card operating requirement is sent from the computer if so the card operating requirement determining unit is adapted to inform the performing module to perform corresponding operation on the card according to the card operating requirement sent from the computer otherwise the card reader ends the process and goes back to the status of waiting for the system call.

In the embodiment whatever the sequence of the determining steps by the determining module the determining module further includes

a verification requirement determining unit adapted to if the determining module determines that a card is inserted in the slot and the card reader is offline determine whether a verification requirement from the user is received if so the verification requirement determining unit being adapted to inform the operating module to perform operation with the card to generate a Token otherwise the card reader ends the process and goes back to the status of waiting for the system call.

The determining module can includes a user requirement determining unit a card operating requirement determining unit or a verification requirement determining unit or a combination from any of the three units.

In the embodiment the verification operation includes but not limited to CAP Chip Authentication Program operation and DPA Dynamic Passcode Authentication . Thereby the CAP which is a method for verifying the identity of a cardholder is an online process which takes advantages of the verification function of the EMV chip payment card provides identification verification for remote cardholder and provides evidence to prove the details of the transaction agreed by the cardholder.

In the embodiment the process that the operating module performs operation with the card to generate a Token is same as the process of that in the embodiment 1. No more further detail is described here.

From the technology described above the invention provides a card reader with multiple functions and a method for implementing the same which overcomes the shortcomings that the card reader in the prior art has simplex function. And the card reader provided by the invention has good common performance. Besides the function of reading the card the card reader is further adapted to perform verification when the card is inserted in the slot of the card reader for example generating a Token and further adapted in identification authentication field such as online bank and transaction online and the like. Furthermore the card reader is adapted to generate a one time password or a challenge code without a card in the field of identification verification in the internet game or operation system.

The presently disclosed embodiments should be considered in all respects to be illustrative and not restrictive. The scope of the invention is indicated by the appended claims rather than the foregoing description and all variations which come within the meaning and range of equivalents thereof are intended to be embraced therein.

