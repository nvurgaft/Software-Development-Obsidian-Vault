A **stateless protocol** is a communication protocol in which the receiver must not retain session state from previous requests. The sender transfers relevant session state to the receiver in such a way that every request can be understood in isolation, that is without reference to session state from previous requests retained by the receiver.

In contrast, a **stateful protocol** is a communication protocol in which the receiver may retain session state from previous requests.

In computer networks, examples of stateless protocols include the Internet Protocol (IP), which is the foundation for the Internet, and the Hypertext Transfer Protocol, which is the foundation of the World Wide Web. Examples of stateful protocols include the [Transmission Control Protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) (TCP) and the [File Transfer Protocol](https://en.wikipedia.org/wiki/File_Transfer_Protocol "File Transfer Protocol") (FTP)

Stateless protocols improve the properties of visibility, reliability, and scalability. 

1. Visibility is improved because a monitoring system does not have to look beyond a single request in order to determine its full nature. 
2. Reliability is improved because it eases the task of recovering from partial failures. 
3. Scalability is improved because not having to store session state between requests allows the server to easily scale horizontally.
4. Stateless API's are easier to develop and maintain.
5. Independent requests are easier to cache because they don't depend on the server state, 

The disadvantage of stateless protocols is that they may decrease network performance by increasing the repetitive data sent in a series of requests, since that data cannot be left on the server and reused.

An HTTP server can understand and process each HTTP request in isolation.

Sources: https://en.wikipedia.org/wiki/Stateless_protocol

Despite the stateless nature of some protocols, many server and database implementations necessitate the need to track user state in the form of user [[Session|Sessions]].