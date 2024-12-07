# **Multithreaded WebSocket Server**

## **Overview**

This project implements a **multithreaded Java server** with **WebSocket support**. It is designed to handle WebSocket connections from clients, efficiently process requests, and send responses. The server includes functionality for **bit manipulation** and **header management** for outgoing WebSocket responses, ensuring proper communication with WebSocket clients.

## **Features**

- **Multithreading**: The server can handle multiple client connections concurrently using Java's thread management.
- **WebSocket Support**: Supports WebSocket protocol for real-time, bidirectional communication between the server and clients.
- **Bit Manipulation**: Implements bit manipulation utilities for managing WebSocket headers and communication.
- **Client-Server Communication**: Allows the server to respond to client requests over WebSocket connections.

## **Table of Contents**

- [Requirements](#requirements)
- [Setup](#setup)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [License](#license)
- [Contact](#contact)
- [Future Improvements](#future-improvements)

---

## **Requirements**

- **Java**: This project is developed using **Java 8+**.
- **JDK**: You will need to have the **Java Development Kit (JDK)** installed to compile and run the server.
- **WebSocket Client**: Any WebSocket client (like **Postman**, **web browser console**, or a custom client) that supports WebSocket protocol can be used to connect to the server.

---

## **Setup**

To set up the server, follow these steps:

1. **Clone the Repository**

   ```bash
   git clone https://github.com/NaveenMuralidharan/MSD.git
   ```
2. Compile the Server Code
Ensure you have the JDK 8+ installed. Then, compile the server code:

``` bash
   javac -d bin src/*.java
```
3. Run the Server
Start the server by running the main class:
```bash
   java -cp bin Main
```
The server will start listening for WebSocket connections on the specified port (usually 8080).

## Usage

Client WebSocket Connection
To test the WebSocket server, you can connect using any WebSocket client. Here’s how to connect using a web browser:

Open the browser’s developer tools (usually F12 or Ctrl+Shift+I).
Navigate to the Console tab.
Use the following JavaScript to open a WebSocket connection:
```bash
var socket = new WebSocket("ws://localhost:8080");
socket.onopen = function() {
    console.log("Connected to the server");
   //to join a chat room
    socket.send("join, ${room name}, ${user name} ");
   //to send messages
    socket.send("message, ${user name}, ${message} ");
   //to leave a room
   socket.send("leave");
};
socket.onmessage = function(event) {
    console.log("Received message: " + event.data);
};
socket.onclose = function() {
    console.log("Connection closed");
};
```
## Server Behavior
The server listens for incoming WebSocket connections on port 8080.
When a client sends a message, the server processes it and sends back an appropriate response.

## Code Structure

Here’s a breakdown of the key classes in the project:

- Main: This is the entry point of the server. It initializes the HTTP and WebSocket server and starts listening for client connections.
HttpServer: Manages incoming WebSocket connections and delegates client communication to a new thread via HttpRunnable.
WebSocketHandler: Handles WebSocket handshakes and message processing. It includes logic for handling WebSocket headers. Contains utility methods for bit-level manipulation, such as setting WebSocket headers.Handles communication between the client and server over WebSocket.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contact

For any questions or inquiries, please contact:

Author: Naveen Muralidharan
Email: naveenspec@gmail.com (replace with actual email)

## Future Improvements

- Add Authentication: Implement JWT-based authentication for securing WebSocket connections.
- Rate Limiting: Add rate-limiting to prevent abuse of the WebSocket API.
- Scalability: Optimize server performance to handle more concurrent WebSocket connections.
- Logging: Add structured logging for better debugging and monitoring.
- Error Handling: Improve error handling for WebSocket connections and message processing.
