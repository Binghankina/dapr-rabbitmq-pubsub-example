# dapr-rabbitmq-pubsub-example
Publish and subscribe (pub/sub) enables microservices to communicate with each other using messages for event-driven architectures.
- The producer, or publisher, writes messages to an input channel and sends them to a topic, unaware which application will receive them.
- The consumer, or subscriber, subscribes to the topic and receives messages from an output channel, unaware which service produced these messages.
- An intermediary message broker copies each message from a publisher’s input channel to an output channel for all subscribers interested in that message. This pattern is especially useful when you need to decouple microservices from one another.

- ![pubsub-overview-pattern](https://docs.dapr.io/images/pubsub-overview-pattern.png)

## Prerequists
[tilt](https://docs.tilt.dev/install.html)

## Dapr pub/sub (HTTP requests client)

This example creates a publisher microservice and a subscriber microservice to demonstrate how Dapr enables a publish-subcribe pattern with rabbitmq. The publisher will generate messages of a specific topic, while subscribers will listen for messages of specific topics. 

This example includes one publisher:

- Python client message generator `pub` 

And one subscriber: 
 
- Python subscriber `sub`

## Deploy all apps with tilt

run

```bash
cd pub
tilt up 
```
stop tilt session, run 

```bash
cd sub
tilt up 
```

The terminal console output should look similar to this:

```text
== APP - order-processor-http == Subscriber received : 1
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:21] "POST /orders HTTP/1.1" 200 -
== APP - checkout-http == INFO:root:Published data: {"orderId": 2}
== APP - order-processor-http == Subscriber received : 2
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:22] "POST /orders HTTP/1.1" 200 -
== APP - checkout-http == INFO:root:Published data: {"orderId": 3}
== APP - order-processor-http == Subscriber received : 3
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:23] "POST /orders HTTP/1.1" 200 -
== APP - checkout-http == INFO:root:Published data: {"orderId": 4}
== APP - order-processor-http == Subscriber received : 4
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:24] "POST /orders HTTP/1.1" 200 -
== APP - checkout-http == INFO:root:Published data: {"orderId": 5}
== APP - order-processor-http == Subscriber received : 5
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:25] "POST /orders HTTP/1.1" 200 -
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:26] "POST /orders HTTP/1.1" 200 -
== APP - order-processor-http == Subscriber received : 6
== APP - checkout-http == INFO:root:Published data: {"orderId": 6}
== APP - checkout-http == INFO:root:Published data: {"orderId": 7}
== APP - order-processor-http == Subscriber received : 7
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:27] "POST /orders HTTP/1.1" 200 -
== APP - checkout-http == INFO:root:Published data: {"orderId": 8}
== APP - order-processor-http == Subscriber received : 8
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:28] "POST /orders HTTP/1.1" 200 -
== APP - checkout-http == INFO:root:Published data: {"orderId": 9}
== APP - order-processor-http == Subscriber received : 9
== APP - order-processor-http == 127.0.0.1 - - [04/Sep/2023 11:33:29] "POST /orders HTTP/1.1" 200 -
```

### Stop the apps and clean up

```bash
cd pub
tilt down
cd sub
tilt down 
```
