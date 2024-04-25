# CDN (Content Delivery Network)

There is a special type of server that is strictly designed to deliver static content, such as HTML, CSS, JavaScript, Videos, Images. They are called CDN servers.

CDN servers as mentioned allows us to distribute static content in a large scale. They are often known as edge server or cache servers.
Imagine you have a web site that resides in the Origin server which is located in your city and country, let say somewhere in Ireland.

Now what is going to happen if someone from America, or Argentina or China try to access your web page?
The time to load all these files may take very long. The idea of CDN servers is that they have copies of these files and are globaly distributed, so people close to these special servers may get better performance in terms of loading the site.
Also in scenarios where a CDN server goes down, we can easily redirect the user to the most close CDN server from them, which ensure the Redundancy Design Requirement.

![](/images/8.png)

## Push CDN

A Push CDN is a technique where the static content once uploaded to the origin server, it automatically spread it to the CDN servers.
This can also be configurable in such way that only certain CDN servers receive this new content.
Por example. Imagine Netflix provide a new movie in their origin server. But not all countries will have access to this movie. Netflix can configure to push this movie only to certain CDN servers.

## Pull CDN

A Pull CDN operates the inverse of Push CDN, where a user request a certain data from the CDN server, the cache hit is done, and if there is a miss, our CDN server will request that missing content from the origin server.
This allow our CDN server to only provide content that actually is relevant for that geographical area.
