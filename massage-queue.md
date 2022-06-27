# Message Queues
[✔back to main](./README.md)

- What does it mean that web sockets are bidirectional? Why is this useful?

web sockets are bidirectional means it handles both client-side and server-side.
Whereas HTTP relies on a client request to receive a response from the server for every exchange, WebSockets allow for full-duplex bidirectional communication. This enables the server to send real-time updates asynchronously, without requiring the client to submit a request each time.

- Does `socket.io` use `HTTP`? Why?

`no`, Socket.IO is always dependent on a `http server`


- What happens when a client `emits` an `event`?

the event gets passed to the server through websockets. Its a tcp connection from the browser to the server. The connection is full duplex meaning the server can send real time data to the client and vise versa.

- What happens when a server emits an event? 

when the server listen to the connection event. When that event is invoked, socket.io pass a socket object to our function. We then listen to all of our sockets for a chat. As defined on the client side, take the data emited from the chat and emit it back to all of our sockets.

- What happens if a client `“misses”` an event?

it `stored` in queue until the client get opportunity to listen the event.

- How can we mitigate this? we will push a missed event to the Buffers until it is consumed(used).


### `Terms`

- `Socket`

a socket is an endpoint of a communication between two programs running on a network. Sockets are used to create a connection between a client program and a server program

- `Web Socket`

The WebSocket object provides the API for creating and managing a WebSocket connection to a server, as well as for sending and receiving data on the connection.

- `Socket.io`
Socket.IO is a library that enables real-time, bidirectional and event-based communication between the browser and the server.

- `Client`

The Clients interface provides access to Client objects.

- `Server`

framework can be used to develop web servers using the ‘http’ module.

- `OSI Model`

The OSI model is an architectural model that represents networking communications.

- `TCP Model`

TCP (Transmission Control Protocol) is a protocol for sending information between computers.

- `TCP`

TCP (Transmission Control Protocol) is a protocol for sending information between computers.

- `UDP`

UDP (User Datagram Protocol) is a long standing protocol used together with IP for sending data when transmission speed and efficiency matter more than security and reliability.

- `Packets`

a packet is a small segment of a larger message. Data sent over computer networks*, such as the Internet, is divided into - `packets`.


### Socket.io Chat example

Sockets have traditionally been the solution around which most real-time chat systems are architected, providing a bi-directional communication channel between a client and a server
The server can push messages to clients

Whenever you write a chat message, the idea is that the server will get it and push it to all other connected clients
Setup steps here

- `Rooms` and `Namespaces`

`Room` is an arbitrary channel that sockets can join and leave, it can be used to broadcast events to a subset of clients
Rooms are a server-only concept (client does not have access to the list of rooms it has joined)
Can join to subscribe the socket to a given channel `socket.join()`

Each socket in Socket.io is identified by a random unique identifier (Socket#id), each socket automatically joins a room identified by its own id

Upon disconnection, sockets leave all the channels they were part of automatically.

#### references

[chat example on socket.io](https://socket.io/get-started/chat/)

[rooms](https://socket.io/docs/v4/rooms)

[nameSpaces](https://socket.io/docs/v4/namespaces/)

[cheatSheet](https://socket.io/docs/v4/emit-cheatsheet/)