## Web Application Architecture

We live in a world connected through a wide network called internet.
Is through that system that we can access different other systems and applications.
This notes try to explain in a simple view of how a web application is architectured.
How different system components are interlinked and how our final user is able to access the data our system provide.

# Servers

First things first, every application we can access through the web is host in a server.
A server is just someones else computer, dedicated to run our code.
Servers can have a wide range of responsabilities, run our code, store a database, host history of our application called logs, or even run other applications in paralell your app.

# Server scalability

Let say we have our app running in a server, and our client is happy accessing their data, but for some reason the server start to slow down, or even crash due unkown reasons. Seems like we have a bootleneck, which can be related to limitations from our machine. This can be due lack or Memory RAM or CPU.

There are two common ways to solve this sort server scalability problem.

- Vertical Scale
- Horizontal Scale

# Vertical Scale

Imagine your app is not very complex and the number of users are not massive like youtube for example.
It means you can easily run your app in a single server, but as mentioned before the server starts to slow down or even crash. Upgrading your machine with more Memory RAM or CPU with multiple cores could solve your users problems. This approach is called Vertical Scale. Since you scale up a single machine.
For simple applications this is the way to go, but there is a tradeoff, Vertical Scale can't be upgraded forever. As we know, machines can't hold unlimited Memory RAM or CPUs. That is where Horizontal Scale shines.

![](/images/2.png)

# Horizontal Scale

In a scenario where your app is accessed by a massive number of users or even accross the globe, hosting your app into multiple servers allows you to not just keep providing the functionality of your app for your users, but also ensuring that if a single server crash you still can redirect your user request to other instances that are up and running.
This approach also allows you to a very specific technique called canary, which allow you to provide a certain functionality for a % number of users withot affecting all of them at the same time.
When we are dealing with scalability that we an not sure how massive our servers will be hit by requests or how often, we can rely on a technique called Horizontal Scale, which instead of upgrading a single machine with more Memory RAM or CPU, we can just add or remove servers instances by demand.
Since we have many servers running our app we have to ensure that our users requests are evenly directed to them, this is acomplished by a Load Balance.

![](/images/3.png)

# Clients

Clients are how our users interact with our system, it can be a web site, mobile app, or desktop app.
In a default web scenario clients uses an interface application called a browser. It will request a very specific server which will load all HTML, CSS, JavaScript. These code components will then be rendered as a web page which will be used as interface for our back-end system.

# Logs

Our apps run on servers as we code them to behave. But sometimes things goes wrong, and we can't just guess what happened.
This is why is important to have logs. Logs are history behavior of your app. They use to be files written in a specific directory in your server. But nowadays it is not very versatile anymore.
Logs can describe as much information you need, what happened when a given input hit a function during a task in your app, or when a connection were lost with a database.
Nowadays there are Server Logs which are connected to your app servers, and they are constantly reciving your appplication logs as requests and storing them in a dedicated application which late can be used to filter whatever you need based from any of your app servers into a single point.

# Metrics

Sometimes logs won't show everything we need to understand what happened to our app to crash our server or why it start to slow down.
That is where Metrics came in. Metrics are a special type of data that is fetched from our app server, it collects information such as Memory consumption, CPU usage and network consumption.
There are also special servers with dedicated applications that nowadays are used to store this sort of data, and are constantly receiving our app servers requests with this information.

# Alerts

As engineers, we may have all data we need to observe our apps running, and also understanding issues that may occur. But sometimes it is even better to know when a problem occur ahead of time.
Combining Logs and Metrics we can always configure alerts to notify our engineers when specific problems or when a certain % of occurrences of issues start to happen, so our workforce can act as quick as possible before our users start to complain, or even worst, decide to stop using our app.

![](/images/4.png)