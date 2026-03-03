Backpressure happens when a system receives more requests/data/input then it can handle in real-time.
A common case in Software is when a service consumer can't keep up with the rate of incoming data from a producer.

Backpressure is common throughout system that access the network and even those that do no

### Causes for Backpressure

Network requests - A system with a network facing API doesn't have enough resources to handle incoming traffic, some messages may be dropped.

File processing - A huge file can be read all at once into memory and slow down the system and even crashing it.

UI rendering - Having to render more elements on the screen that the system can handle, framerate may suffer greatly, memory can be exhausted and the system may crash.

### Strategies to handle Backpressure

#### Rate Limiting 

In event driven systems, we can use rate limiting to limit or reduce the amount of incoming messages to the system. 

#### Buffering

If we can't slow the rate of incoming requests then maybe we can store them in a linear buffer where they will stay until the system can process them. A blocking queue is such a candidate.
If you're using a queue make sure to bound it otherwise an unbounded queue may lead to memory exhaustion.

#### Load Balancing

A load balancer will distribute the load across multiple consumers instead of allowing one consumer to get overwhelmed.
This is a common approach in Microservices Architecture.

#### Asynchronous Processing

Instead of allowing all your consumer to handle the data synchronously, use async processing and background workers to handle the data because being consumed by the endpoint.

[[Message broker|Message Queues]] such as Kafka and RabbitMQ are good for this.

#### Drop the messages

Sometimes it's just better to drop the data if you're sure a loss of data will not impact the system or the end user.
