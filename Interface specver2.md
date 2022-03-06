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

#### 2.3. Complete the SIP-SSI session for session initiators
This function 
- creates an out-of-band-message
- encrypts it
- sends it as a SIP text message, using the active SIP connection
- completes setting up the DIDComm connection
- answers a proof request with a proof presentation

#### 2.4. Complete the SIP-SSI session for session responders
This function 
- decrypts incoming out-of-band-messages 
- answers incoming out-of-band-messages with a connection-request and completes setting up the DIDComm connection
- sends a proof request for default credentials and verifies and displays the credentials that it receives
- Unblocks the media stream in case of a satisfactory credential exchange.

#### 2.5. Future work: request credentials
Request the default credentials from the other party. To be used by Alice when during the session, she decides she needs more assurance from Bob.

#### 2.6. Future work: present credentials
Present the default credentials to the other party. In response to 2.5.





