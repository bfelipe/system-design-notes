# API (Application Programming Interface)

APIs can be seen as a combination of protocols and specifications for clients to perform opperations with servers functionality.
It provide rules to clients of how this communication must to be performed, data structures(payloads), and how to exchange this data with through the network.
In other words, APIs are just insterfaces which clients can use to communicate with server logic.

## API Paradigms

There are a few API paradigms, which allows servers to be exposed in such way that clients can communicate with servers.
The most common API Paradigms in modern web are:

- Rest
- GraphQL
- gRPC
- SOAP (Simple Object Access Protocol) - we are not going to talk about this one.

## Server Paradigms

Server paradigms are models which engineers can choose to build the server, each paradigm has pos and cons. Based on system requirements such as: scalability, reliability, performance, etc.

Some examples of server Paradigms:

- Monolithic: all logic and access of server functionality if packet into a single binary, it may be easy to develop as a small server, but can become difficult to scale as the application evolve.
- Microservice: servers are developd and distribuited based on business domain, it may be easy to develop and scale since each server contain it own set of rules, but can difficult to debug since requests may be distributed across other servers downstream, and some models must be sincronized if they share common payload.
- Serverless: the simplest paradigm for server development, serverless doesn't need to worry about infrastructure and scalability, since the cloud provide is responsible to scale up and scale down on demain, but it can become difficult to manage so many services, since its database can grows exponentially, force you to stay forever with your cloud provider due its resources for this specific technology and affect latency due also to could start.
- Event Driven: applications that requires high volume of data processing may benefit from this paradim, since each server can process as much events as it can with the resources it is provided, commonly Even Driven servers are used for background processing which eventually data will reach its finaly destination.
- Distributed Systems: this approach distribute computational tasks over a cluster of servers. In modern days of systems we use something called docker and kubernetes, platforms that allows us to scale horizontaly based on the demain our system requires. There must be knowledge of how this distribution of tasks must be done through load balance and other things to ensure each server can process evenly the same ammount of tasks using the resources provided to it. Commonly this approach works alonside with Microservice paradim.