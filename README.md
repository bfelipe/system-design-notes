# System Design Notes

A simple and comprehensive guide about system design, bringing compiled information about principles and insights.

## Introduction

Over the past decade I had the opportunity to work with many talented people, who was willing to share their knowledge and who mentored me for a very long time.
I always had my personal goals and desire to learn, but sharing what I have learnt just became a passion which I start to nurture a few years ago.
I truly hope these notes can guide future generation of engineers when making architectural decisions and expanding their knowledge about different solution alternatives when considering its trade-offs when applying them on system design.

## Content

In this repository you going to find many notes, grouped by context.
The follow structure resume all texts in each chapter:

 - Basics
	- Computer Architecture
		- Hard Disk
		- Memory
		- CPU
		- Cache
	- Web Application Architecture
		- Servers
		- Server Scalability
		- Vertical Scale
		- Horizontal Scale
		- Clients
		- Logs
		- Metrics
		- Alerts
	- Design Requirements
		- Moving Data
		- Store Data
		- Transforming Data
		- The good, the Bad and the Ugly
		- Factors of System Design
		- Availability
		- Reliability, Fault Tolerance, Redundancy
		- Throughput
		- Latency
 - Network
	- IP
		- Network
		- IP
		- Anatomy of IPV4
		- IVP6
		- Static and Dynamic IP
	- Transmission
		- Data Packets
		- Headers
		- Payload
		- Packet Structure
	- Layers
		- Network Layer
		- Transport Layer
		- Application Layer
	- Types of Network
		- Types of Network
		- A bit more about IPs: Private and Public IP
		- Ports
	- TCP
		- TPC (Transmission Control Protocol)
		- How it actually works?
	- UDP
		- UDP (User Datagram Protocol)
		- Why UDP over TCP?
	- DNS
		- DNS (Domain Name System)
		- Name Registrars
	- URL
		- URL (Uniform Resource Locator)
		- Protocol
		- Domain
		- Subdomain
		- Primary Domain
		- TDL
		- Path
 - Servers
	- HTTP
		- HTTP (Hypertext Transfer Protocol)
		- HTTP structure
		- Client/Server model
		- HTTP Message - client
		- Start Line
		- Request Method
		- Headers
		- Body
		- HTTP Message - server
		- Start Line
		- Status Code and Status Message
		- TLS (Transport Layer Security)
	- RPC
		- RPC (Remote Procedure Call)
	- WebSocket
		- Pooling
		- Bidirectional communication
	- API
		- API (Application Programming Interface)
		- API Paradigms
		- Server Paradigms
	- Rest
		- Rest (Representation State Transfer)
		- Data exchange
		- Limitations
	- GraphQL
		- Query
		- How it works?
		- Multation
	- gRPC
		- gRPC (gRPC Remote Procedure Call)
		- Protocol Buffers or just Protobuff
		- Protobuff schema example
	- API Design
		- Resource naming
		- Subresource, Path Param, Query Param, & Pagination
 - Cache
	- Caching
		- Caching
		- The downside of caching
		- The computer cache
		- L1 Level
		- L2 Level
		- L3 Level
		- How cache is controlled and managed by CPU?
		- The web browser/client case
		- Cache Ratio
		- The server case
		- Write around
		- Write through
		- Write back
		- Eviction cache policies
		- First in First out (FIFO)
		- Least Recently Used (LRU)
		- Least Frequently Used (LFU)
	- CDN
		- CDN (Content Delivery Network)
		- Push CDN
		- Pull CDN
 - Proxy
	- Proxy
		- Forward Proxy Server
		- Reverse Proxy Server
		- Distributed Denial of Service
		- Reverse Proxy Server - The shield of backend systems
	- Load Balance
		- Rounding Robing
		- Weighted Round Robing (WRR)
		- Least number of connections
		- User Location
		- Layer 4 Load Balancing
		- Layer 7 Load Balancing
		- Consistent Hashing
 - Databases
	- SQL
		- Tables
		- Why Relational databases?
		- Atomicity
		- Consistency
		- Isolation
		- Durability
		- Trade-offs
	- NoSQL
		- NoSQL (Not Only SQL)
		- Key/Value store
		- Document store
		- Wide Column store
		- Graph store
		- Why NoSQL?
		- Eventual consistency
	- Object Store
		- Object Store
		- The file system approach
		- The object store approach
	- Data Replication & Sharding
		- Replication
		- Synchronous Replication
		- Asynchronous Replication
		- Multi-Master Replication
		- Sharding
	- Cap Theorem
		- Partition Tolerance
		- Availability
		- Consistency
		- The CAP Threorem extension
 - Big Data
	- Queues
		- Queues
		- Push Model
		- Pull Model
		- Acknoeledge signal
		- Dead Letter Queue (DLQ)
		- Publish and Subscribe Model (Pub/Sub)
	- ETL
		- ETL (Extract, Transform, Load)
		- Cronjobs
	- Batch
	- Stream
		- Stream processing

## References

The follow are some of the references I've used to write these notes and some references are insightful material to expand from what I have here, its important to say that some texts also come with links which can be used to dive deep into the subjects. I may add extra links over time.

- Books
    - Design Data-Intensive Applications by Martin Kleppmann
    - Designing Distributed Systems by Brendan Burns
    - Software Architecture: The hard parts by Neal Ford, Mark Richards, Pramod Sadalage
- Sites
    - neetcode.io: [System Design for beginners course](https://neetcode.io/courses/system-design-for-beginners)
    - geek for geeks: [System Design Tutorial](https://www.geeksforgeeks.org/system-design-tutorial)

## Author

- Bruno Felipe

## License

Shield: [![CC BY-NC 4.0][cc-by-nc-shield]][cc-by-nc]

This work is licensed under a
[Creative Commons Attribution-NonCommercial 4.0 International License][cc-by-nc].

[![CC BY-NC 4.0][cc-by-nc-image]][cc-by-nc]

[cc-by-nc]: https://creativecommons.org/licenses/by-nc/4.0/
[cc-by-nc-image]: https://licensebuttons.net/l/by-nc/4.0/88x31.png
[cc-by-nc-shield]: https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg