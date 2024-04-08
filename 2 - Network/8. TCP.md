## TCP (Transmission Control Protocol)

When data is transmited over the network we use a common protocol called TCP. TCP allows us to split our data into pieces(packets) and send to our destination. Once it arrives the protocol will manage to rearrange its proper order due its headers to our receiver, so he can read it. Using TCP also ensure that all packets are delivery without any missing parts.

# How it actually works?

When a client and a server stablish connection, they execute an operation called handshake.
This ensure both sides can start transmiting data.
The client send a packet and the server then have to acknoledge the receive of that package to the client. In case this doesn't occur, the client retransmit that packet ensuring any packets are missing, expecting the server return an acknoledge signal this time.
