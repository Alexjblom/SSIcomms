## Interface Specification
 
 


The SSIComms project will deliver an SSIComms mobile app that demonstrates the capabilities of the library behind it.

The library is foreseen to offer the following functions:

### 1. Configuration

#### 1.1. Session type
- Only accept only SIP-SSI invites and refuse all others
- Accept SIP-SSI as well as regular SIP invites
- Only accept regular SIP invites.

#### 1.2. Credentials
- Set default credentials to offer
- Set default credentials to accept

### 2. Session
#### 2.1. Send an invite to a SIP-SSI session
This function sends out an invite for a SIP session which will be used for regular communications AND to set up a DIDComm connection. 

#### 2.2. Respond with a 200 OK to a SIP-SSI invite
This function acknowledges the existence of SSI-capabilities

#### 2.3. Send an out-of-band message over SIP connection
This function creates an out-of-band-message, encrypts it and sends it as a SIP text message, using an active SIP connection

#### 2.4. Present credentials
Present the default credentials to the other party.

#### 2.5. Request credentials
Request the default credentials from the other party.

#### 2.6. Block the media stream
Block the media stream, for instance until Bob decides that the credentials he received from Alice satisfy his expectations.

#### 2.7. Unblock the media stream
Unblock the media stream, for instance because Bob decides that the credentials he received from Alice satisfy his expectations.




