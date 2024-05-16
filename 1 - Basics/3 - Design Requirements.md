# Design Requirements

When talking about System Design there are three things we have the bare in mind.

- Moving Data
- Store Data
- Transforming Data

## Moving Data

Moving data is the most common opperation we gonna perform in our system, the question is, which is the most effective way to do so?
Which protocol can we use to improve this sort of operation. And how much and often we gonna do that?

## Store Data

Storing thata is a bit tricky, because its not just about keeping a big chuck of information in a random database.
Choosing a proper data structure may help you to store it effectively and also assist you to access portions of it through algorithms in an effective way as well.
Ex. A data stored in an simple array or a data stored in a Binary Search Tree or a data stored in a Graph?
Choosing a proper database also must be in consideration, since each one has its pos and cons in terms of how access your data.

## Transforming Data

Transforming data is another operation we often do. Think like which is the most effectice way to process the percentage of certain occurrences in the data we have, or the most effective way to aggregate or filter from different datasets to extract insights for a report.

## The good, the Bad and the Ugly

As engineers we all have to make design decisions, and having a proper understanding of which is good or not may affect the future of our application.
Data structure and algorithms as mentioned before can give you insight of how to structere and manipulate your data in an effective way in your application. But when dealing with architecture design, an ugly decision for the sake of quick delivery can cost highly to the company in the future when talking about a distributed system.
Imagine you start your app with an algorithm that appears not to be as efficient as you thought, it can easily be fix without too overburden. But imagine choosing a database or platform to host your app, the fact you may have to migrate your data and your entire infrastrcuture may take a long time, and the cost for that is high, even worst when you also have to rewrite part of your code that is tightly attached to that decision.

## Factors of System Design

Bare in mind when you design a distributed and data intensive/demading system.
There are factors you should consider that will certainly help you on your decisions along the way. They will sure help you during your design decisions.

- Reliability
    - Availability
    - Reliability, Fault Tolerance, Redundancy

- Scalability
    - Throughput
    - Latency


Note: There is another factor called Maintainability, which focus on how easy is to engineers are to keep things running, understand the overal system and keep maintaining in the long run. We not going to discus this factor here, since this is much more clear during your experience building things thand describing each of them.

## Availability

Availability stands for how often our system stays up based in a range of time.
For a critical system this is important, once your system is down, the number of users and money you lose can be extremely high.
You can predict availability downtime by considering patch time, or not, like hardware issues or other factors like natural disasters.
To calculate your availability you can use the follow mathematical equation:

    availability = up time / (up time + down time)

    ex scenario:

        up time = 22 hours
        down time = 2 hours due update + unexpected issues

    availability = 22 / (22 + 2)
    availability = 0.916666667
    availability = 91.6%

In other words your service will be available 91.6% the entire day.

But let's imagine if you consider an example for an entire year? How many days your service will be unavailable?

    ex scenario:

        year = 365
        days unavailable = (% number / 100) * total days
        days unavailable = (9 / 100) * 365
        days unavailable = 32.85

In other words, if an entire year your service sum 9% of unavailability, it means it went off for 32.8 days. That is terrible.

For a standart point of view this is bad. Engineers now have to think how they can increase they availability so their users are not negatively impacted.
There are other equations that can be used to calculate availability of your systems, but I will leave it for you to search them.
The ideal scenario is to have an availability close to 99%.
When dealing with availability of great scale systems, we have must to think in two factors SLA (service level agreement) its like an agreement to our clients that our system will be available to a certain up time, and SLO (service level objective), which will be te goal our team will commit to ensure our service will reach that level of availability.

## Reliability, Fault Tolerance, Redundancy

Reliability comes in when we have a app running in a server and we expect it behaves as intended as we coded, without leading to failures or presenting errors, in other words, it do what it means to do.
But what happens when millions of users start to hit our server? That is the rate that our server crash? This is when Fault Tolerance came into play. As discussed before, there are techniques to scale our servers to ensure that our system keep up and running without crashing or goes totally down. Having multiple instances of servers even when they are not currently being used, we can call it Redundancy. It serves as a backup or extra resources in cases where our system enter into a critical state of provide the functionality our users expect.

A clear example of how these three factors work together is when we think about a DDOs (distributed denial of service) attack. Multiple users start to hit our servers, by scalling them up we ensure our system do not goes down to the actual users trying to use our app. Having redundancy or extra instances of our servers even without them being used ensure that in a critical state, we can keep serving healthy users with our services.

## Throughput

Throughput is a factor considering in System Design when considering how much data or operations we can perform in a given time.
There are different ways to measure that, and logs can easily come into play to visualize this insight.
Examples:

- requests/second
- bytes/second
- queries/second

Depending of the scenario Vertical Scale or Horizontal Scale can improve considerably your measure. Take in considerarion what you are trying to visualize.
Requests can give you insight how how many operations a user are doing in your app, bytes, how many data are you moving through the network, queries, how much read/write you are executing in your database which can lead to some bottle necks, and this can help you also start to think how you can improve in that area which affect user experience requests, which lead to our next factor Latency.

## Latency

Latency is a measure of how much time the entire operation it takes to a client perform a request and get its response.
Imagine a user, sending a request, this request takes about 800ms, the server then perform another request to authenticate the user, which can takes about 300ms because the authentication is done in another server, then the server query data into a data base which can take about 100ms, then the server do a set of requests to another server by each item in that query which in total can take 20ms, and finaly it returns the data to our user with another 900ms.

As you can see, there are tons of operations that takes time, which in sum could easily 2.12 seconds.

This example is just for a single user, now imagine this being processed by thousands of users in a single server?
What can we do to improve that number?
There are many techniques to do that:

- change to a different protocol such grpc/protobuff which half the size in bytes of its payload transmited in the network
- look for improvements of the database query
- caching data
- scale the authentication server

This and many other considerations can be done to improve that 2.12 seconds to a few milliseconds, without having to scale our server, which could certain save tons of money.