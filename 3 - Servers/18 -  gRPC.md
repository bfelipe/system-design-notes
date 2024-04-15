# gRPC (gRPC Remote Procedure Call)

gRPC is a framework for RPC paradigm. Which allows client and server call for for a function exposed by another server, and exchange data over binary.
These messages are common defined by a schema called Protocol Buffers.

## Protocol Buffers or just Protobuff

Protobuff is a IDL (Interface Definition Language), or simply speaking is a technology to define a schema for RPC services.
Once you define a protobuff, the server will encode and decode the data exchanged with the client based on this schema from/to a binary format.
It allows also that client doesn't send any arbritary data to the server that is not defined in the protobuff.
Working with this kind of technology allows low latency over the network since we exchange messages in a binary data.
So imagine you have a 200kb json size wich you used to perform requests over a Rest API. Using protobuff is basically compacting this payload to a 64kb size or less, remember, we are not talking about json here, we are talking about pure binary.

Protobuff is agnostic, so once you define a schema for your data, you can use this schema on both client and servers without any additional changes.
gRPC is also a framework for RPC protocol. Which means that clients can use it to perform calls to servers implemented using this technology.

## Protobuff schema example

A Protobuff schema can look like this once defined for a simple server:

        syntax = "proto3";

        package pb;

        import "google/protobuf/timestamp.proto";

        enum ApplicationType {
            WORKER=0;
            API=1;
            CRON=2;
        }

        message Team {
            string name = 1;
            repeated string members = 2;
        }

        message Application {
            string name = 1;
            int32 id = 2;
            bool is_backend = 3;
            ApplicationType type = 4;
            Team team = 5;
            optional google.protobuf.Timestamp created_at = 6;
        }

        message ApplicationName {
            string name = 1;
        }

        service AppService {
            rpc NewAPI(ApplicationName) returns (Application);
        }

        option go_package = "simple-app/pb";

Once you compile this schema Protocol buffer will generate the code for your desire programming language. Which simplify the development workflow.
As you can see, we have data models called Team, Application, Application Name, and also and Enum called ApplicationType. Then we define our rpc service called AppService that expose NewAPI function which an RPC client can call sending ApplicationName model data as input. Once that service process the request it returns an Application model response.
You can notice similar structure of how models are designed here and GraphQL, but they work pretty different from each other.
gRPC allow client and servers to process many different types of requests, unary, streaming, bidirectional streaming, and some other rpc life cycles.

You can learn more about gRPC and Protocol Buffers in the follow links:

- [gRPC](https://grpc.io/)
- [gRPC concepts](https://grpc.io/docs/what-is-grpc/core-concepts/#rpc-life-cycle)
- [Introduction to gRPC](https://grpc.io/docs/what-is-grpc/introduction/)
- [gRPC status code](https://grpc.github.io/grpc/core/md_doc_statuscodes.html?ref=apisyouwonthate.com)
- [Protocol Buffers](https://protobuf.dev/)
- [Protocol Buffers Overview](https://protobuf.dev/overview/)
