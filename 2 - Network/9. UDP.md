# UDP (User Datagram Protocol)

UDP similar to TPC is a transmission protocol, which enables packet transmission while guarantee better speed delivery, it comes with cost of losing packets along the transmission.

This happens because different thand TCP, UDP doesn't check for signals of acknoledge of packet arrival. Only for this factor the transmission of packets is way faster than its sibling protocol, which turns this procotol less reliable.

## Why UDP over TCP?

There are applications that better suit UDP, for example data streaming.
Picture a scenario where you are watching a video, and sundely you notice that a frame just jump to another leaving a piece of video/sound empty. This also occurs when you are listening your favorite songs on your music apps.
So when you have a use case which you want a faster data transmission, but loss of data is not a big concern UDP can be a better choice for your app.

See more about [UDP](httphttps://datatracker.ietf.org/doc/rfc768/)
