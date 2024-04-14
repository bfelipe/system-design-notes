# GraphQL

Due Rest paradigm limitations, another paradigm was created to solve over-fetching and under-fetching, it is called GraphQL.
GraphQL allow clients to perform Query(Request) to a server, asking only the necessary data it desires. The server then will process that Query(Request), based on a schema defined on the server side, and return the proper response.
Different than Rest which perform requests over HTTP methods, GraphQL perform two type of actions Queries, and Mutations.

## Query

In GraphQL a Query is a request performed in a resource over a POST HTTP method, sendind a schema like this:

    {
        me {
            name
        }
    }

Our server then will return a response similar to this:

    {
        "me": {
            "name": "Luke Skywalker"
        }
    }

## Multation

Mutation similar to our common POST, PUT and PATCH HTTP methods, Mutation allows client to send data over a schema, that whill be persisted or modifed in the server side.
It's important to say, that both Query and Mutation on GraphQL operates over POST HTTP method to perform both operations.

See more about [GraphQL](https://graphql.org/learn/)
