# Functional specification

## 1. Application structure
### 1.1 General
The application SSIComms consists of a business module, which makes use of an integrated SIP module and SSI module. The SIP module provides the different SIP communication utilities, the SSI module provides the DIDComm and wallet functionalities. Together, they constitute an application that satisfies use cases such as:
1. Identification before and during an internet communications session
2. The principle of verify the verifier
3. Exchange of payment tokens during internet communications sessions

As its SIP module, SSIComms uses SYLK Suite and as its SSI module AnimoMobile SDK, a javascript Aries mobile agent. The business module was built on purpose for this project The diagram below illustrates how all of this fits together.

![SSIComms_structure_diagram_ver2](https://user-images.githubusercontent.com/50589812/156152040-dea0e556-24a7-46b6-b836-3aa3f3156a0f.svg)
 
## 1.2. Business module
This module contains
- the business logic
- a SIP client capable of transporting DIDComm messages.
- the ability to display messages on screen
 
## 1.3. SIP module
This module is based on SYLK Suite and supports:
- SIP Signaling
- Voice Over IP
- Messaging
- SIP conferencing
- Gateway
- Web conferencing
 
## 1.4. SSI module

This module supports the following features:
- TypeScript native framework, built for cross-platform mobile development on iOS & Android
- A generic DID resolver interface that support the did:key, did:web and did:sov methods.
- Issuance of Indy credentials using both v1 and v2 of the Issue Credential protocol.
- Proving and verifying of Indy credentials using both v1 and v2 of the Present Proof protocol.
- Issuance of JSON-LD credentials using v2 of the Issue Credential protocol (RFC 0593 for JSON-LD credential exchange).
- Proving and verifying of JSON-LD credentials using DIF Presentation Exchange v1, and Present Proof protocol v2.
- Sign and verify JSON-LD credentials with the Ed25519Signature2018, BbsBlsSignature2020 and BbsBlsSignatureProof2020 signature suites.
- Fully AIP 1.0 and 2.0 compliant
- Mediation of DIDComm messages to hold messages while the mobile device is offline
- Allows to use mediator of choice (currently either AFJ or ACA-Py supported).
- Set of ready to use React Native modules needed for every mobile wallet
- Storage of key to unlock wallet in iOS & Android secure enclave, protected by biometrics or pin code.
- Set up of push notifications with automatic provisioning of mediator to receive push notifications when messages are received when wallet is closed.
- QR Scanner component for connection invitation handling.
- DIDComm deep linking setup so you can open DIDComm links in your wallet.
- Redux Store wrapper to integrate wallet functionality into a Redux store.
- Wallet import & export to local device for backups and recovery (may look into protocol for storing and backups at mediator in the future).

A detailed overview of which Aries features, agent types, protocols and AIP versions the mobile SDK will support see the Aries Mobile SDK - Aries Feature Overview document.
The special needs of SSIComms where it regards the SSI module are outlined in the use cases below.

# 2. Use cases

## 2.1. Scope and context
### 2.1.1. Scope
Two parties, Alice and Bob, want to execute a transaction, in this case setting up communication online. Both parties may have certain knowledge about the transaction, i.e. the participants and the purpose, and both may have certain conditions for the transaction that need to be met.
In order to determine what is needed for the specific transactions in the use cases to succeed, we analyze the phases of negotiation, execution and acceptance of the communication session. 

Within these phases, credentials may be needed, and parties may take on the role of holder, issuer and/or verifier of such credentials. 

The use cases are: 


Use Case 1: Alice calls Bob and Bob wonders whether she is really Alice.

|Step  | Phase | Description                      |
|:---------|:---------|:---------------------------------|
|1  |Negotiation  | Alice calls Bob|
|2  |Negotiation| Bob will only accept the call if he is convinced it's Alice calling|
|3  |Execution	 |Bob asks Alice for a credential|
|4  |Execution	 |Alice presents a credential|
|5  |Execution  |Bob examines the credential and approves|
|6  |Acceptance|Bob accepts the communication session|



Use Case 2: Alice calls Bob, Bob wonders whether Alice is Alice, and Alice wonders whether Bob is Bob

|Step  | Phase | Description                      |
|:---------|:---------|:---------------------------------|
|1  |Negotiation  | Alice calls Bob|
|2  |Negotiation| Bob will only accept the call if he is convinced it's Alice calling|
|3  |Negotiation| Alice will only proceed with the call if she is convinced she is calling Bob|
|4  |Execution	 |Bob asks Alice for a credential|
|4  |Execution	 |Alice presents a credential|
|5  |Execution  |Bob examines the credential and approves|
|6  |Execution  |Alice asks Bob for a credential|
|7  |Execution  |Bob presents a credential|
|8  |Execution  |Alice examines the credential and approves|
|9  |Acceptance|Alice accepts communication session|
|10 |Acceptance|Bob accepts the communication session|




Use Case 3: Use Case 3: Alice calls Bob, but calling Bob is not free
Follows the logic of Use Case 1 but adds a condition of payment.

### 2.1.2. Context

- Alice and Bob Alice and Bob both have an SSI enabled SIP client, with which they can set up an ongoing peer2peer internet communications session (a call, video call or message)
- Alice and Bob are both behind a firewall and have no other way of exchanging messages in realtime
- For the sake of simplicity, in all cases the proxy servers almost always present in real life situations are not shown here.

### 2.2. Use Case 1:  Alice calls Bob and Bob wonders whether she is really Alice.

The following diagram shows how we expect to make _identification during an internet communications session_ happen for Alice and Bob. Please note that DIDComm by itself, where a session is usually initiated by reading a QR-code, does not fit the circumstances. 

  
![SSI_SIP_flowdiagram_no_redirect drawio(2)](https://user-images.githubusercontent.com/50589812/156942818-caa14679-b1c8-44fe-91c4-2dc3a136ffaa.svg)
#### 5.1.1. Future work: Alice calls Bob, but Bob answers using the wrong app
In case of Bob not receiving the first invite on an SSI capable SIP client, he uses a 301 mesage to deflect the invite to another client, which does have this capability:

![SSI_SIP complex diagram drawio(2)](https://user-images.githubusercontent.com/50589812/157230190-de11afc5-746a-4ff8-9fce-76242d25b668.svg)


### 2.3. Use Case 2: Alice calls Bob, Bob wonders whether Alice is Alice, and Alice wonders whether Bob is Bob

![SSI_SIP_VTV_flowdiagram drawio(1)](https://user-images.githubusercontent.com/50589812/156942760-a1ba17fb-5170-4f7a-982b-e039a5e232ee.svg)

In this scenario, better known as _verify the verifier_, Alice and Bob take the role of holder and verifier respectively, and then the role of verifier and holder. The exchange of VC???s twice can of course be achieved by using existing DIDComm messages, but that has its drawbacks: not only does the holder have to respond to multiple on screen messages, which does not make for a great user experience, it also misses the opportunity to offload the decision making to the machine layer. Involving more human decision making creates additional risk of the agreed exchange going wrong.


### 2.4. Use Case 3: Alice calls Bob, but calling Bob is not free.
The third use case concerns the decentralized equivalent of premium rate numbers. Benefitting from their embedded digital wallets, Alice and Bob can identify and pay each other directly using a payment token. 
This use case falls under the category of nice to have, since in spite of its practical relevance, it is only indirectly connected to the subject of this project.


# 3. Security

### 3.1. SIP
#### 3.1.1. SIP messages
Concerns about the security of calls via the public Internet have been addressed by encryption of the SIP protocol for??secure transmission. The URI scheme SIPS is used to mandate that SIP communication be secured with??Transport Layer Security??(TLS). SIPS URIs take the form??sips:user@example.com.
End-to-end encryption??of SIP is only possible if there is a direct connection between communication endpoints. While a direct connection can be made via??Peer-to-peer SIP??or via a??VPN??between the endpoints, most SIP communication involves multiple hops, with the first hop being from a user agent to the user agent's??ITSP. For the multiple-hop case, SIPS will only secure the first hop; the remaining hops will normally not be secured with TLS and the SIP communication will be insecure. In contrast, the??HTTPS??protocol provides end-to-end security as it is done with a direct connection and does not involve the notion of hops.
#### 3.1.2. SIP text messages
SIP text messages are encrypted using the OpenPGP standard.

#### 3.1.3. RTP stream
The media streams (audio and video), which are separate connections from the SIPS signaling stream, may be encrypted using SRTP. The key exchange for SRTP is performed with??SDES??(RFC??4568), or with??ZRTP??(RFC??6189). When SDES is used, the keys will be transmitted via insecure SIP unless SIPS is used. One may also add a??MIKEY??(RFC??3830) exchange to SIP to determine session keys for use with SRTP.

### 3.2. DIDComm
#### 3.2.1. Out-of-band messages
Out-of-band messages are traditionally not encrypted, because DIDComm does not do so. However, in this case they are, because they are carried as SIP text mesages. See above to find out how SIP messages are encrypted.

#### 3.2.2. DIDComm messages
In DIDComm v1, the security is loosely based on standard JSON Web encryption. DIDComm v2 uses full JOSE standards (JWM, EDHC-1PU, etc) 


