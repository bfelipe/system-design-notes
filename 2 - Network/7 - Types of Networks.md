
# Types of Networks

Computers not always can communicate with each other, since they may have been located in different networks.
There are three different types of networks, LAN, MAN and WAN.

- LAN (Local Area Network): Is the most simple network structure, it connect devices together into the same area. It's common used in your house for example.

- MAN (Metropolitan Area Network): This type of network extend the capabilities of LANs, it can connect different LANs together, like two companies into the same network, or two universities. It can be even wider like connecting LAN of an entire city.

- WAN (Wide Area Network): It is the most complex type of network geographic speaking, you can picture the Internet as a WAN network, connecting networks of many states together of a country or even entire countries overseas.

There are other types of networks too like PAN, SAN, VPN and many others. But I think is it something you can search by yourself.

## A bit more about IPs: Private and Public IP

Now we know there are different types of network, lets come back to a known subject IP, and lets discuss about Public and Private IP.

LANs as we know can have a set of devices connected to it, each with its own IP addresses. These are Private IP addresses since they are not exposed over the internet and no one outside that network can communicate with that device.
So how can we keep devices in the LAN communicating with each other and also allowing devices outside the network communicate with them as well?

This is where Public IP comes in.

A Public IP is a unique identifier given by your ISP (Internet Service Provider). It will allow a device from a external network be able to connect and communicate with a device in your local network.

## Ports

Each server provide a range of ports that are unique available to services and apps to be exposed, and be able to be accessed over it.
For example, a web API service may be expose on port 80 allowing users to perform HTTP calls.
Or a web site exposed on port 4200 allow users to reach its web interface.
Ports are are compose by a 16 bit integer, variying from 0 to 65535.

It is important to state that each Port is designated to some functionalities and protocols such as TPC and UDP.
The most common Ports used by us engineers in our daily basis are:

- 20 - 21: FTP
- 22: SSH
- 25: SMTP
- 53: DNS
- 80: HTTP
- 443: HTTPS

See more about [Ports](https://www.cloudflare.com/learning/network-layer/what-is-a-computer-port/)

See more about [List of Ports by application](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.txt)