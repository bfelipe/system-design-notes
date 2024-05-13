# Queues

Sometimes we encounter scenarios where our servers has to face a high volume of data to be processed. We could simply scale up or scale out our service to keep up with the demand. These are valid solutions, but it also present your set of challenges and increase cost.

So what else can we do to prevent server overload and still be able to process users requests?

In scenarios where we don't need to process data in real time and return the result of that operation to the user, we can employ an asynchronous technique using Message Queues.

A Message Queue act as a middleware between a producer(the server which event originate) and a consumer(the server which will handle the event data).

Picture a book store. This business may have an ecommerce which their customers buy books. Their customer send a request to the server containing the products and payment method. This server may trigger an event to another service which is responsible to process inventory, and another service which process payments.

![](/images/13.png)

There are different models we can employ queues into our system design, we are going to explore a bit about them now.

## Push Model

In a Push model architecture, once our producer send the message to the queue, it will automatically send that message to the consumer server. The downside of it is that if the message queue receives a high volume of messages in a short period of time, the queue can overload the consumer.

![](/images/14.png)

## Pull Model

In this model, consumers will check in the message queue if messages are available, in case of positive, the consumer will pull the messages and process it.
In this architecture model our consumer won't face the issue of server overload, since it will have the control of checking the message queue. Although, we can't always ensure the queue has messages available, which can add latency to the consumer due to its check operation.

![](/images/15.png)

## Acknowledge signal

When working with Push/Pull model architecture consumers must to signal back to the queue message an Acknowledge signal, this signal enfers that the message was successfully processed and it may now be removed from the message queue buffer.

## Dead Letter Queue (DLQ)

A DLQ is an additional queue in a messaging architecture designed to receive messages that, for some reason, couldn't be successfully processed by the consumer. Some message queue systems allow engineers to configure policies for the main queue, such as a time-to-live (TTL) for the message. If a message expires without being processed, it is automatically redirected to the DLQ, ensuring the message is not lost.

Also consumers can implement additional settings to retry process the message if a failure occur. If after some attempts the message is not successfully processed, the message is moved to the DLQ, and removed from the main queue.

DLQs allow engineers and administrators to analyze possible issues in both producers and consumers, ensuring they are communicating through the same contract. Also DLQs allow manual reprocessing of messages with the correct payload, ensuring messages are always processed no matter what.

## Publish and Subscribe Model (Pub/Sub)

In a Pub/Sub model, messages are sent to a topic which acts like and address, this topic then will fanout its content to all its subscribers.
Going back to our previous example of the book store. We mentioned about having a inventory service and payment service, if that example implements a pub/sub architecture, you can imagine that each service has its own queue subscribed to a topic.
Additional consumers can be added to the topic without affecting the architecture, also, additional producers can also be included.

![](/images/16.png)
