Envisioned interoperability
===========================

Interoperability is a core aspect of SSI, and SSIComms strives to live up to that by offering different options for interoperability and collaboration with other eSSIF solutions as well as solutions outside of eSSIF-lab.

### 1. Interoperability with AnimoMobile SDK and Sylk Suite
SSIComms has chosen eSSIF-LAB participant AnimoMobileSDK to cooperate with right from the start of the project. The cooperation involves embedding Animo's solution into the SSIComms app and making the two work together. The participation of SYLK Suite is a good example of cooperation with a project outside of eSSIF-lab.
 
### 2. Using SSIComms
In general, there are a number of ways to make use of the SSIComms libraries:

##### 2.1 Substitute the wallet 
This means leaving the SIP module and the business module intact, and integrating a different react native wallet which leaves the transport of its out-of-band message to the business module.
Candidates to explore are Evernym and Trinsic.

##### 2.2 Substitute our SYLK Suite based SSIComms communications client and server with a different solution.
There are currently no internet communications projects within eSSIF-Lab, and we are keeping our eyes out for existing react native internet communications applications.

### 3. Interoperability relevant to our use cases

##### 3.1 The SSI Mandate service from Visma
Mandates are particularly relevant in the case of internet communications, where often requests for informaton are exchanged between entities in the medical and insurance ecosystem and clients and their mandatees. We are exploring the use of Visma's SSI Mandate service in cooperation with Visma. 

###### 3.1.1.Implementation
Currently, we have foreseen a very basic process to load the app with credentials. Working with Visma, we will look at expanding this process to accomodate their solution.

##### 3.2. Trinsic Trust registry. 
Through this component, holders can avoid coercion by verifying the verifier; verifiers can discern offline which issuers they trust; issuers can communicate to holders which governance framework they are associated with. This is relevant to our use cases 1 and 2 and our use runs parallel to Animo's implementation effort.

###### 3.2.1. Implementation
We will look at expanding our API for this.

##### 3.3. iGrant.io: data-agreement. 
On our wishlist since the verify the verifier protocol creates a special set of circumstances where a specialized data agreement is suggested by the use case. Together with iGrant.io, we therefore want to investigate whether the two parties agreeing to a mutual exchange of credentials offers room for legal/machine readable formalization.

###### 3.3.1. Implementation
We will look at expanding our API for this.

 
### 4. Contributions to standards

##### 4.1 The SIP protocol
The transport of DIDComm related messages using the SIP protocol creates the need for a standardized message format. We will investigate whether this can and should be added to the standardized Session Initiation Protocol (SIP). To be more specific, we are considering a new SSIComms header for the SSIComms messages as a way of standardising the SIP encapsulation of DIDcomm messages.


##### 4.1 DIDComm messaging 
DIDComm messaging currently has no special provisions for a Verify the Verfier exchange between a holder and a verifier. It is usually handled by repeating a holder verifier exchange while switching roles. However, if one strives to minimize the number of on screen messages for the user, and thus the possibility for disruptive human interference, this situation might be improved upon by adding to the library of DIDComm messages. 
