A message broker is an architectural pattern and a type of software for message validation, transformation, and routing. It mediates communication among applications (i.e. services in Microservices architecture), minimizing the mutual awareness that applications/services should have of each other in order to be able to exchange messages, effectively implementing decoupling.

Message brokers offer two basic message distribution patterns or messaging styles:

### Distribution patterns

Message brokers offer two basic message distribution patterns or messaging styles:

**Point-to-point messaging:** This is the distribution pattern utilized in message queues with a one-to-one relationship between the message’s sender and receiver. Each message in the queue is sent to only one recipient and is consumed only once. Point-to-point messaging is called for when a message must be acted upon only one time. Examples of suitable use cases for this messaging style include payroll and financial transaction processing. In these systems, both senders and receivers need a guarantee that each payment will be sent once and once only.  

**Publish/subscribe messaging:** In this message distribution pattern, often referred to as “pub/sub,” the producer of each message publishes it to a topic, and multiple message consumers subscribe to topics from which they want to receive messages. All messages published to a topic are distributed to all the applications subscribed to it. This is a broadcast-style distribution method, in which there is a one-to-many relationship between the message’s publisher and its consumers. If, for example, an airline were to disseminate updates about the landing times or delay status of its flights, multiple parties could make use of the information: ground crews performing aircraft maintenance and refueling, baggage handlers, flight attendants and pilots preparing for the plane’s next trip, and the operators of visual displays notifying the public. A pub/sub messaging style would be appropriate for use in this scenario.

### Role in Microservices

Microservices must have a means of communicating with one another in order to operate in concert. Message brokers are one mechanism they use to create this shared communications backbone.

Message brokers enable asynchronous communications between services so that the sending service need not wait for the receiving service’s reply. This improves fault tolerance and resiliency in the systems in which they’re employed. In addition, the use of message brokers makes it easier to scale systems since a pub/sub messaging pattern can readily support changing numbers of services. Message brokers also keep track of consumers’ states.

Source: https://www.ibm.com/think/topics/message-brokers

### Implementations

Some of the more popular message brokers are Kafka and RabbitMQ. 