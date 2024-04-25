# Proxy

A Proxy is a special server that aims to protect one side of network as a representant of the client or the server actual application server.
We have two types of Proxy servers.

- Forward Proxy Server
- Reverse Proxy Server

## Forward Proxy Server

A Forward Proxy Server acts like a representant of the client during a request.
When a client perform a request to a server, the Forward Proxy Server mask the clients IP with its own. Then the request is sent to the target server. The target server then returns its message response, only knowing the proxy server as the origin of the request.
This Proxy server also can filter client access content, blocking or allowing client access to it over the network. Finally a Forward Proxy server can also cache certain content which client often requests, so it minimize the overall latency of the request.

## Reverse Proxy Server

A Reverse Proxy Server acts as a gateway for incoming client requests to the application server.
When a client makes a request, the message is received by the Reverse Proxy, which then forwards or routes it to the appropriate application server.
Reverse Proxy servers can also provide protection for the application servers from DDoS (Distributed Denial of Service) attacks by filtering and blocking malicious traffic before it reaches the backend servers. Finally, it can distribute requests using load-balancing algorithms to clustes of servers of the same application.

## Distributed Denial of Service

DDoS is a massive number of requests that aims to overload the servers until it goes down.
It is often performed by non-real users, but automated scripts that simulate a real user(bots).

## Reverse Proxy Server - The shield of backend systems

Reverse Proxy Servers can protect backend systems from DDoS attacks by analysing anomalies in incoming requests.

An anomaly is detected when requests from the same IP start to arrive in a huge number in a short period of time. A rate of limit is applied to this IP, aiming to decrease the frequency of its requests, otherwise it is added to a blacklist and blocked.

CDN servers employ Reverse Proxy to protect web pages, adding captcha challenges to filter real users before allowing them to access the page content.
