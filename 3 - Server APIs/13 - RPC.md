# RPC (Remote Procedure Call)

RPC is an old application protocol from 60s, that started gained visibility in modern distributed computing era.
This protocol allow client call a function located in a server and send raw binary as data instead other types such as text.
The server decode the raw binary and return the expected result as binary as well.
This communication procedure may look low level and hard to work, but it gives many benefits like:
- Faster data transmission, since client/server only transmit raw binary instead heavy data format.
- No parsing, since client and server only transmit binary, decreasing the time of encoding/deconding. Although RPC uses a mechanism called stubs, which is like a schema of how that raw binary data is about to be.
- Interoperability, RPC is language agnostic, so you can use clients and servers written in many different languages communicating in the same format.