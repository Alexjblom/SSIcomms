Interface specification
=======================

## Communications and business layer
SYLK Suite consists of a mobile client and SYLK Server, to which it connects through the SYLK Server API. Mirroring this setup, the communications and business layer of SSIComms will consist of a mobile client that makes use of an enriched SSIComms version of the Sylk Server’s API. This allows for all of the functions of the communications layer and the business layer to be called from the mobile application.

This setup allows anyone to build ones own SSIComms mobile application by simply having a mobile application that addresses the SSIComms version of the Sylk Server’s API. This will result in the integration of some or all of SSIComms functionalities, in order to have the capabilities of the communications layer and the business layer at its disposal.

The current documentation for the SYLK server API can be found at https://github.com/AGProjects/sylkrtc.js/blob/master/API.md More SSIComms specific endpoints will be added during the project.






## Aries Mobile SDK/wallet layer
The Aries Mobile SDK is created by creating an instance of the Agent class.


import { Agent } from '@aries-framework/core'


import { agentDependencies } from '@aries-framework/react-native'



const agent = new Agent(
  
  {
   
     //Agent config to be defined 
  
  },
  
  agentDependencies

)


After creating an agent, it exposes a set of modules that together compose the public API. 


Besides the standard use of existing modules, SSIComms  will focus on the specific modules to facilitate the transport of out-of-band-messages over SIP and the handling of payments and payment requests.
