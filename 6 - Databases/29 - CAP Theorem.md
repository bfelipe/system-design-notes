# CAP Theorem

The CAP Theorem is a concept applied into distributed databases. It aims to guarantee system functioning even when a network partition occurs, where primary and replica nodes can't communicate with each other.
This concept rely on two of three properties: Consitency, Availability, Partition Tolerance. Where Partition Tolerance is always present.

See more about [CAP Theorem](https://martin.kleppmann.com/2015/05/11/please-stop-calling-databases-cp-or-ap.html)

![](/images/11.png)

## Partition Tolerance

When we talk about distributed databases using primary/replica, a partition occurs when nodes stop communicatin due a network interruption. This can happen due network issues, hardware issues or delays.

In the concept or CAP Theorem, Partition Tolerance is prioritized when a partition occur. This mean the system continue to operate, even if nodes can't communicate anymore.

## Availability

Availability is prioritized when a partition occur between primary and replicas, clients still be able to access data, even if that data is outdated. This is applicable for non-critical systems, where maintaining system interactions is more relevant.

## Consistency

Consistency is prioritized when a partition occur between primary and replicas, clients will only be able to read and write from the primary node, ensuring data consistency for critical operations.

## The CAP Theorem extension

The CAP Theorem provide guidance to design systems where a network partition occur, where you consider Availability or Consistency. But there is an extension to this theorem when network partition is absent. It is called PACELC.

PACELC stands for Partition Avilability Consistency Else Latency Capability.

In this extension, you can choose one of two properties: Consistency or Latency. Where users can have the most updated data or data with minimum delays.

![](/images/12.png)
