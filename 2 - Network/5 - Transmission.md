# Transmission

When two devices (owned by people) want to exchange messages, they just exchange packages over the network using their IP addressess as point of references of origin and destination.

## Data Packets

Data Packats are a format how our data will be wrappet to be sent over the network.
Once you decided to send an information to someones computer you gonna organize it into the follow structure: Header, Payload, trailer/footers(which is a group of metadata that marks the end of the packet).
See more about [Packet](https://www.cloudflare.com/learning/network-layer/what-is-a-packet/)

## Headers

Headers are a list of metadata that contain information about the senders and other metadata about the content which is being sent over the network.

## Payload

Payload is the actual data, payloads may not always be sent in the same packet due its size, which leads us to use other mechanims such as a trailer/footer to know our stream of data is completely sent.

## Packet Structure (TPC Packet Structure)

| IP Header      | TPC Header | Payload|
|--------------|:-----:|-----------:|
| xxx | xxx |        xxxxxx |

See more about [TCP Packet](https://www.ietf.org/rfc/rfc9293.html)