# About domains and SIP adresses

_Consult diagram.pdf for the meaning of “SIP Client1” etc._
### Between SIP Client1 and SIP Client2
This project is about extending the SIP protocol, and therefore signalling between SIP Client1 and 2 must use the SIP protocol. We therefore must use a different domain for SIP Client1 and SIP Client2, so that using SIP becomes a necessity.

### Between SIP Wallet1 and SIP Wallet2.
In general in SSI, low correlation is a leading principle. This means that an agent (a wallet + business layer) will use a different public key and a different endpoint for each connection with a verifier. Thus, when a user is applying for a mortgage, the lender will not be able to learn whether that same customer also exchanged credentials with a hospital recently.

Translated to SSIComms, this means that the business layer needs several SIP adresses, for example 10 obtained at inception, from which it picks one at random when a new Identified Communications session is initiated. These adresses do not all need to be registered upon startup but one could be instructed to register when a new session is initiated.
Again, SIP Wallet1 must be in a different domain than SIP Wallet2, but can be in the same domain as SIP Client1. Two domains are therefore sufficient:

| Domain1 | Domain2 |
| ------- | ------- |
| SIP Client1 | SIP Client2 |		
| SIP Wallet1 |	SIP Wallet2 |
