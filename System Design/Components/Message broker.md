A message broker is an architectural pattern and type of software for message validation, transformation, and routing. It mediates communication among applications (i.e. services in Microservices architecture), minimizing the mutual awareness that applications/services should have of each other in order to be able to exchange messages, effectively implementing decoupling.

Message brokers offer two basic message distribution patterns or messaging styles:

### Distribution patterns

Message brokers offer two basic message distribution patterns or messaging styles:

**Point-to-point messaging (Request/Reply, RPC):** This is the distribution pattern utilized in message queues with a one-to-one relationship between the sender and receiver. Each message in the queue is sent to only one recipient and is consumed only once. Point-to-point messaging is called for when a message must be acted upon only one time. 
Examples of suitable use cases for this messaging style include payroll and financial transaction processing. In these systems, both senders and receivers need a guarantee that each payment will be sent once and once only.  

**Publish/subscribe messaging:** Often referred to as “pub/sub,” the producer of each message publishes it to a topic, and multiple message consumers subscribe to topics from which they want to receive messages. All messages published to a topic are distributed to all the applications subscribed to it. This is a broadcast-style distribution method, in which there is a one-to-many relationship between the message’s publisher and its consumers. 
Example: an airline were to disseminate updates about the landing times or delay status of its flights, multiple parties could make use of the information: ground crews performing aircraft maintenance and refueling, baggage handlers, flight attendants and pilots preparing for the plane’s next trip, and the operators of visual displays notifying the public. A pub/sub messaging style would be appropriate for use in this scenario.

**Priority queues:** Certain messages can have different priorities than others, a message with a higher priority will be handled sooner. 

**Saga:** Sage patterns are implemented using message brokers. Service A messages service B and than Service B messages Service C. If something fails, lets say Service C fails, it will send a rollback message to Service B which will in turn, send rollback message to Service A.

**Dead letter queue:** If a queue continuously fails to process a message, it can be sent to a special queue called the Dead letter queue and wait there. Developers can later investigate the cause of the error.
This way the message isn't being discarded and any issues can be resolved later.

**Retry Pattern:** If a receiver of a message is temporarily unavailable to process the message, the broker my retry (with a back-off) to resend the message, and after several retries may give up and send the message to the Dead letter queue.  
### Role in Microservices

Microservices must have a means of communicating with one another in order to operate in concert. Message brokers are one mechanism.

Message brokers enable asynchronous (event driven) communications between services so that the sending service need not wait for the receiving service’s reply. This improves fault tolerance and resiliency in the system. 

In addition, the use of message brokers makes it easier to scale systems since a pub/sub messaging pattern can readily support changing numbers of services (services don't need to know about each other, only send messages to a central broker). 

Message brokers can also keep track of consumers’ states and Remote Procedure Calls (RPC).

Source: https://www.ibm.com/think/topics/message-brokers

### Implementations

Some of the more popular message brokers are Kafka and [RabbitMQ](https://www.rabbitmq.com/). 
### Use cases

Message brokers have a lot of use cases inside the architecture
* User registration processing
- Email sending
- Background jobs such as Image resizing, video transcoding, PDF generation, etc..
- Notifications
- Logging
- Analytics
- Event broadcasting