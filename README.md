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

javac -d bin src/*.java

3. Run the Server
Start the server by running the main class:

java -cp bin ServerMain
The server will start listening for WebSocket connections on the specified port (usually 8080).
Usage

Client WebSocket Connection
To test the WebSocket server, you can connect using any WebSocket client. Here’s how to connect using a web browser:

Open the browser’s developer tools (usually F12 or Ctrl+Shift+I).
Navigate to the Console tab.
Use the following JavaScript to open a WebSocket connection:
var socket = new WebSocket("ws://localhost:8080");
socket.onopen = function() {
    console.log("Connected to the server");
    socket.send("Hello Server");
};
socket.onmessage = function(event) {
    console.log("Received message: " + event.data);
};
socket.onclose = function() {
    console.log("Connection closed");
};
Server Behavior
The server listens for incoming WebSocket connections on port 8080.
When a client sends a message, the server processes it and sends back an appropriate response.
Code Structure

Here’s a breakdown of the key classes in the project:

ServerMain: This is the entry point of the server. It initializes the WebSocket server and starts listening for client connections.
WebSocketServer: Manages incoming WebSocket connections and delegates client communication to a new thread.
WebSocketHandler: Handles WebSocket handshakes and message processing. It includes logic for handling WebSocket headers.
BitManipulationUtils: Contains utility methods for bit-level manipulation, such as setting WebSocket headers.
ClientHandler: A separate thread for each connected client. Handles communication between the client and server over WebSocket.
Testing

To test the WebSocket server, you can use the following:

WebSocket Client (such as Postman, or browser-based tools)
Automated Unit Tests: You can implement unit tests to validate WebSocket handshake functionality, header management, and message processing.
To run any automated tests (if present), use the following command:

mvn test
License

This project is licensed under the MIT License. See the LICENSE file for details.

Contact

For any questions or inquiries, please contact:

Author: Naveen Muralidharan
Email: naveen@example.com (replace with actual email)
Future Improvements

Add Authentication: Implement JWT-based authentication for securing WebSocket connections.
Rate Limiting: Add rate-limiting to prevent abuse of the WebSocket API.
Scalability: Optimize server performance to handle more concurrent WebSocket connections.
Logging: Add structured logging for better debugging and monitoring.
Error Handling: Improve error handling for WebSocket connections and message processing.
