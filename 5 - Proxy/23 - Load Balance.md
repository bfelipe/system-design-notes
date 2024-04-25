# Load Balance

A Load Balance is a technique of even request distribution implemented in a Reverse Proxy server. Load balancers allows servers to not get overloaded with requests, ensuring best use of computing resources by the server infrastructure.

As mentioned Load Balance is a technique, this technique is defined its own algorithm to achieve this even distribution of requests accross multiple servers.
They are:

- Rouding Robin
- Weighted Round Robing
- Least number of connections
- User Location
- Layer 4 Load Balancing
- Layer 7 Load Balancing

## Rouding Robing

A Rouding Robing implements the following algorithm. In a cluster of servers S(5) where S is a server. Each incoming request R(5) where R is a request, the request is forward to each server in a sequencial manner.

    R(1) -> S(1)
    R(2) -> S(2)
    R(3) -> S(3)
    R(4) -> S(4)
    R(5) -> S(5)

For each new request, the distribution is applyed again starting by S(1).

## Weighted Round Robing (WRR)

A Weighted Round Robing implements the following algorithm. In a cluster of servers S(3) where S is a server. Each incoming request R(4) where R is a request, the request is forward to server based on the server computational power.

Lets say S(1) is weighted with a computation power of 50% more compared to the others.
S(2) and S(3) is weighted with a computational power of 25% compared to the others.
So a even distribution based on this example would be the follow:

    R(1) -> S(1)
    R(2) -> S(1)
    R(3) -> S(2)
    R(4) -> S(3)

## Least number of connections

The Least number of connections implements the follow algorithm. In a cluster of servers S(3) where S is a server. Each incoming request R(6) where R is a request, the request is forward to server based on the least active connection in that group of servers in that specific moment.

    R(1) -> S(1)
    R(2) -> S(2)

Let say R(1) is done at this moment

    R(3) -> S(1)
    R(4) -> S(3)
    R(5) -> S(1)
    R(6) -> S(2)

## User Location

The User Location implements an algorithm based on IP of the client request and the geolocation of the server.
When an incoming request reach the Load Balancer, it checks the request IP address and then forward to the closest server of that IP address.
This will reduce latency and decrease response time affecting client experience.

## Layer 4 Load Balancing

Layer 4 Load Balancing rely on the Layer 4 of the OSI (Open Systems Interconnection) model. This layer works with protocols such as TCP and UDP. When an incoming request reaches the Load Balancer it examines the IP and port specified in the request (these IP and port are the IP and port of the target server). Then the LB uses the port to checks in its routing table and select the proper server to forward the request.

## Layer 7 Load Balancing

Layer 7 Load Balancing rely on the layer 7 of the OSI model. This layer is the application layer which deals with applications protocols such as HTTP.
When a incoming request reaches the Load Balancer, it analyses many aspects of the request message such as url, query params, headers and/or payload to make decisions before forward the request.
In this algorithm many other algoritms are applied such as server health, response time, current server load. These allows the load balancer to forward the request to the most appropriate server based on Availability Design Requirement.

## Consistent Hashing

There is another technique that allows us to achieve Load Balancing which is hashing.
Hashin is an algorithm that based on an input I and a range of numbers N we can find which position of that range of number our input can be allocated/directed.

So imagine we have a request R which always has in its headers the client IP, or RequestID or any other unique identifier that leads to that request user. Now we have a range of servers S(3).

Hashing will calculate the modulus of that IP or RequestID from request R, with the number of servers. The result will be a number from 0-2 which is the index of our list of servers S. Each new request R with that IP or RequestID will be forward to that server S.

Hashing in a Load Balancing is a good technique when dealing with static content access, caching or database where the data of that user will be stored.

The problem is when one of the servers goes down. Future requests R with those attributes will now have another server S index. Which means we gonna access a server S that no longer contains the data which that user once sent to the server, or requested.

This is where Consistent Hashing comes in.
Consistent Hashing works using the same hash algorithm to find the index of our server S.
But this time, our servers S are arranged in a circular array data structure, with a N number of slots, each for a server S.
In a case where one server goes down, our hashing algorithm will calculate the server S index using a probe technique, which allow us to find the next server available in our circular array of servers. This next available server S will be connected to the same cache or database or content store that the previous server (now unavailable) were connected.

Consistent Hashing ensure not just Availability Design Requirement, but also consistency to data access.
