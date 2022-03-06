# 1. Introduction

One of the things people enjoy the most about the internet, is that it enables them to talk to others remotely almost without limit.
Unfortunately, remotely often means that parties are not sure who they are communicating with. Think of the epidemic of robocalls and prank calls the telecoms industry has been battling for years, or you yourself simply trying to videoconference with your bank: the absence of an identity layer can be a huge problem.

Adding SSI to internet communications resulting in seamless identified communications is the solution to this problem. It enables people engaging in any form of internet communication to exchange presentation requests and proofs, and communicate at the same time.


# 2. Protocol use by SSIComms
SSIComms makes use of two protocols: DIDComm, central to SSI, and SIP, equally central to internet comunications.


### 2.1 DIDComm

DIDComm is the messaging protocol that provides utility for DID-based relationships, the foundation of Self Sovereign Identity. DIDComm is a protocol layer capable of supporting specialized application protocols for specific workflows. 
One such application  protocol is the “Present proof protocol”, a way to exchange credentials.

#### 2.1.1. The out-of-band message
Establishing a DID-based connection starts by Alice sending an out-of-band message to Bob. Besides key material and an identifier, the message contains the endpoint where Alice wishes to receive Bob’s DIDComm messages. Alice is free to use any means of communications to send her out-of-band message.


### 2.2. SIP
The Session Initiation Protocol (SIP) is a signaling protocol used for initiating, maintaining, and terminating real-time sessions that include voice, video and messaging applications. SIP is used for signaling and controlling multimedia communication sessions in applications of Internet telephony for voice and video calls, in private IP telephone systems, in instant messaging over Internet Protocol (IP) networks as well as mobile phone calling over LTE (VoLTE).


### 2.3. DIDComm & SIP within SSIComms
An SSIComms session between Alice and Bob involves 4 major steps:
1. First, Alice and Bob start a SIP session, for instance by Aice calling Bob using the SIP protocol.
2. Then, after Bob answers, he and Alice establish a DID-based connection by Alice sending an out-of band-message. As a means of transport, Alice chooses the active SIP session between her and Bob, and sends Bob the message as an encrypted SIP message. 
3. With the DIDComm connection in place, they can now use DIDComm to exchange credentials. 
4. The credentials proven to be satisfactory, Bob and Alice continue their SIP session and exchange voice, video or text messages.


## 3. The SSIComms project
The project SSIComms adds SSI to internet communications by bringing together an a SIP module and an SSI module in one application. In terms of protocols, SSIComms connects the open standard SIP on the internet communications side to the open standard DIDComm messaging on the SSI side. This enables users to respond to presentation requests for credentials entirely voluntarily and according to SSI principles during communications sessions.

SSIComms differs from existing applications in that it focuses on internet communications sessions with both participants behind a firewall. Under these circumstances, DIDComms by itself does not suffice to add an identity layer.

SSIComms is designed to function within an SSI ecosystem and conform to all its principles by extending the SIP protocol to accommodate identified communications.
The use cases include identification before and during session, the principle of verify the verifier, and as a nice to have, exchange of payment tokens during sessions.

The resulting source code will be available open source and offer developers the opportunity to integrate their own solutions with the SSIComms framework.
