## Design Requirements

When talking about System Design there are three things we have the bare in mind.

- Moving Data
- Store Data
- Transforming Data

# Moving Data

Moving data is the most common opperation we gonna perform in our system, the question is, which is the most effective way to do so?
Which protocol can we use to improve this sort of operation. And how much and often we gonna do that?

# Store Data

Storing thata is a bit tricky, because its not just about keeping a big chuck of information in a random database.
Choosing a proper data structure may help you to store it effectively and also assist you to access portions of it through algorithms in an effective way as well.
Ex. A data stored in an simple array or a data stored in a Binary Search Tree or a data stored in a Graph?
Choosing a proper database also must be in consideration, since each one has its pos and cons in terms of how access your data.

# Transforming Data

Transforming data is another operation we often do. Think like which is the most effectice way to process the percentage of certain occurrences in the data we have, or the most effective way to aggregate or filter from different datasets to extract insights for a report.

# The good, the Bad and the Ugly

As engineers we all have to make design decisions, and having a proper understanding of which is good or not may affect the future of our application.
Data structure and algorithms as mentioned before can give you insight of how to structere and manipulate your data in an effective way in your application. But when dealing with architecture design, an ugly decision for the sake of quick delivery can cost highly to the company in the future when talking about a distributed system.
Imagine you start your app with an algorithm that appears not to be as efficient as you thought, it can easily be fix without too overburden. But imagine choosing a database or platform to host your app, the fact you may have to migrate your data and your entire infrastrcuture may take a long time, and the cost for that is high, even worst when you also have to rewrite part of your code that is tightly attached to that decision.

# Factors of System Design

Bare in mind when you design a distributed and data intensive/demading system.
There are factors you should consider that will certainly help you on your decisions along the way. Seem them as laws, and you sure gonna succced in your decisions.

- Reliability
- Scalability
- Maintainability



- Availability
- Reliability, Fault Tolerance and Redundancy
- Throughput
- Latency
