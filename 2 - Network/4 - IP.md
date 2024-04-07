# Network

A network is a interconnected systems of devices uniquely identified by a number called IP.

## IP (Internet Protocol)

An IP is the identification of a device that can uniquely know who you are over the internet. Nowadays we have two flavors of IP, IPV4 and IPV6.
In early days of the internet IPV4 was used to connect two different devices and exchange messages between then, but over the years this scenario has changed, and the number of these unique IP startet to end. There is IPV6 comes in.

## Anatomy of IPV4

IPV4 is as mentioned an unique identifier. Each device has one, it is composed by a group of 4 octets:

    x.x.x.x

It goes from range

    0.0.0.0 to 255.255.255.255

Each group is composed by 8 bits which is 1 byte size. Since IPV4 has 8 bits for each group 8 bits * 4 is equal to 32 bit (4 bytes).

## IPV6

As mentioned IPV4 is not comming to an end, which lead to development and usage of IPV6, it follows simillar composition of IPV4 but with some differences.
IPV6 is formed by 128 bit, and organized as follows:

    xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx

Different than IPV4, IPV6 also allow hexadecimal values, which allows a much high number of unique identifiers.

## Static and Dynamic IP

There are other common types of IP addresses.

A Dynamic IP for example, is a unique identifier that changes each time a device in a network re-stablish a connection. Picture this. You are playing with your video game, and your ISP gave you a Dynamic IP, just for the sake of that playing session. Once you shut down your video game, that IP became available again, and other device that connect to the network can use it. This kind of IP is commonly give automatically for clients devices.

A Static IP in other hand, is a unique identifier that never changes, it is manually configured and given by a server device that must always be reachabe with that address.
For example, imagine Google using an IP 12.232.2.21 for their server, to access their web site. Now what happens if Google was using a Dynamic IP. Every client that trying to access that IP would no longer be able to access their web site. Just because that IP is no longer used by them.

![](/images/5.png)