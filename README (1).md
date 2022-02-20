SSIComms project summary
========================

## Who's talking
One of the things people enjoy the most about the internet, is that it enables them to talk to others remotely almost without limit. 

Unfortunately, remotely often means that parties are not sure who they are communicating with. Think of the epidemic of robocalls and prank calls the telecoms industry has been battling for years, or you yourself simply trying to videoconference with your bank: the absence of an identity layer can be a huge problem. 

Adding SSI to internet communications resulting in seamless identified communications is the solution to this problem. It enables people engaging in any form of internet communication to exchange presentation requests and proofs, and communicate at the same time. 



## Mixing two protocols
Dedicated to identified communications, Dutch startup and initiator of the SSIComms project **Bloqzone** (bloqzone.com) has built several solutions to this problem in the past using more standard local identity solutions such as DIGID and IDIN. Unfortunately, these sofar tended to result in a somewhat awkward customer experience since the enduser has to switch between multiple applications during one session.
A more thorough approach is therefore needed where not only one application is able to handle both communications sessions and identity sessions, but also where both communications and SSI protocols are interwoven.



## The SSIComms project
The project SSIComms adds SSI to internet communications by adding SSI wallets to the renowned SYLK Suite, an award winning ensemble of communications solutions. In terms of protocols, SSIComms connects the open standard SIP on the internet communications side to the open standard DIDComm messaging on the SSI side. This enables users to respond to presentation requests for credentials entirely voluntarily and according to SSI principles during communications sessions. 

SSIComms differs from existing applications in that it focuses on peer2peer internet communications sessions, where DIDComms by itself does not suffice to add an identity layer.

The solution is designed to function within an SSI ecosystem and conform to all its principles by extending the SIP protocol to accommodate identified communications and by linking governance-as-code to the implementation to ensure the rules (as much as possible) are enforced in the source code. 

The use cases include identification before and during session, the principle of verify the verifier, and exchange of payment tokens during sessions.

The resulting source code will be available open source and offer developers the opportunity to integrate their own wallets with the enhanced Sylk Suite react native client.
