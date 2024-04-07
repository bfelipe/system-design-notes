# Layers

Network are componse by many layers, each with its own responsabilities.
For System Design, there are only three that are important for us.

- Network Layer
- Transport Layer
- Application Layer

## Network Layer

This layer is responsible to actual interlink over different networks, without it, we could never transmit data from a source to a target over the internet.

## Transport Layer

This layer is where different protocols of transport such as TCP, UDP and others works. They are the barebones to ensure our data is organized into proper structures for our applications to read and write on them.

## Application Layer

Application Layers rely on specific protocols, which allows us to take the structures from Transport Layer and Decode into a more friendly protocol, such as HTTP. This will allow us to actually use in our application, read headers, read the data stores as payload in the packet received, and write responses.

As you can see, Network can be very complex, and we only talked about three of many layers they are built on to make this complex system called internet work.

See more about [Layers](https://developers.cloudflare.com/fundamentals/reference/network-layers/)
