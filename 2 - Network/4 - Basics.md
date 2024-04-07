## Basics

# Network

A newtwork is a interconnected systems of devices uniquely identified by a number called IP.

# IP (Internet Protocol)

An IP is the identification of a device that can uniquely know who you are over the internet. Nowadays we have two flavors of IP, IPV4 and IPV6.
In early days of the internet IPV4 was used to connect two different devices and exchange messages between then, but over the years this scenario has changed, and the number of these unique IP startet to end. There is IPV6 comes in.

# Anatomy of IPV4

IPV4 is as mentioned an unique identifier. Each device has one, it is composed by a group of 4 octets:

    x.x.x.x

It goes from range

    0.0.0.0 to 255.255.255.255

Each group is composed by 8 bits which is 1 byte size. Since IPV4 has 8 bits for each group 8 bits * 4 is equal to 32 bit (4 bytes).

# IPV6

As mentioned IPV4 is not comming to an end, which lead to development and usage of IPV6, it follows simillar composition of IPV4 but with some differences.
IPV6 is formed by 128 bit, and organized as follows:

    xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx

Different than IPV4, IPV6 also allow hexadecimal values, which allows a much high number of unique identifiers.

# Transmission

When two devices (owned by people) want to exchange messages, they just exchange packages over the network using their IP addressess as point of references of origin and destination.

# Data Packets

Data Packats are a format how our data will be wrappet to be sent over the network.
Once you decided to send an information to someones computer you gonna organize it into the follow structure: Header, Payload, trailer/footers(which is a group of metadata that marks the end of the packet).
See more about [Cloudflare Packet](https://www.cloudflare.com/learning/network-layer/what-is-a-packet/)

# Headers

Headers are a list of metadata that contain information about the senders and other metadata about the content which is being sent over the network.

# Payload

Payload is the actual data, payloads may not always be sent in the same packet due its size, which leads us to use other mechanims such as a trailer/footer to know our stream of data is completely sent.