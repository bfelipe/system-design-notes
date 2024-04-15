# GraphQL

Due Rest paradigm limitations, another paradigm was created to solve over-fetching and under-fetching, it is called GraphQL.
GraphQL allow clients to perform Query(Request) to a server, asking only the necessary data it desires. The server then process that Query(Request), based on a schema defined on the server, and return its response.
Different than Rest which perform requests over HTTP methods, GraphQL perform two type of requests called Queries, and Mutations.

## Query

In GraphQL a Query is a request performed in a resource over a POST HTTP method, sendind a payload schema like this:

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

## How it works?

In the server we define a schema of type Query, which is attached to a model. It may look like this:

    type Query {
        me: User
    }
    
    type User {
        id: ID
        name: String
    }

Pay attention to Query, there is a keyworkd called "me", this is the name of the function that will trigger the request and return the model User as a response.
But remember, in GraphQL we don't need to return every single data of that model. So if you look in our previous request example, our query called "me" function, passing only the "name" attribute of the User model. I could also asked ID, or any other attribute that our User model provide if that was necessary.

## Multation

Mutation is similar to our common POST, PUT and PATCH HTTP methods, Mutation allows client to send data based a schema, that whill be persisted or modifed in the server side.
It's important to say, that both Query and Mutation on GraphQL operates over POST HTTP method to perform both operations.

See more about [GraphQL](https://graphql.org/learn/)
