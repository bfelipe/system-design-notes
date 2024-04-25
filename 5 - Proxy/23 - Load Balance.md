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
In this algorithm many other algoritms are applied such as server health, response time, current server load.
