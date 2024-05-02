# Chat Application Backend Documentation

This document provides an overview and explains the backend architecture of a Node.js-based chat application. The application uses Express.js, Socket.IO, MongoDB, bcryptjs, and JSON Web Tokens (JWT) for its operations.

## Key Components and Libraries

- **Express.js**: A Node.js web application framework that provides features for web and mobile applications.
- **Socket.IO**: Facilitates real-time, bidirectional and event-based communication.
- **bcryptjs**: Utilized for hashing and salting passwords to enhance security.
- **jsonwebtoken**: Used to generate JWTs to secure communication between client and server.
- **cors**: Middleware for enabling CORS (Cross-Origin Resource Sharing) with various options.
- **Mongoose**: ORM for MongoDB that manages relationships between data, provides schema validation, and is used to translate between objects in code and the representation of those objects in MongoDB.

## Server Initialization

- Configures express to use middleware for JSON handling, URL encoding, and CORS.
- Sets up a Socket.IO server on port 8080 configured to accept requests from any origin.

## Socket.IO Events

### Connection

Establishes user connection and manages various events:

- `sendMessage`: Handles sending messages from one user to another.
- `addUser`: Manages online user status and updates the database upon user connection.
- `disconnect`: Removes a user from the online list and updates their status when they disconnect.
- `userOffline`: Explicitly sets a user's status to offline and updates the list accordingly.

## Express Routes

### Basic Route

- **GET `/`**: Returns a simple welcome message.

### User Authentication

- **POST `/api/register`**: Registers a new user, checks for existence, hashes the password, and stores the user.
- **POST `/api/login`**: Authenticates a user, compares hashed passwords, and issues a JWT if credentials are valid.

### Conversation Management

- **POST `/api/conversation`**: Creates a new conversation or retrieves existing ones.
- **GET `/api/conversations/:userId`**: Retrieves all conversations that involve a specific user.

### Message Handling

- **POST `/api/message`**: Handles sending messages and managing conversations.
- **GET `/api/message/:conversationId`**: Retrieves all messages associated with a specific conversation.

### User Management

- **GET `/api/users/:userId`**: Provides details of all users except the one making the request.

## Mock Large Language Model API

- **GET `/api/mock-llm`**: Simulates a delayed response from a language model based on a given prompt, demonstrating asynchronous API integration.

## Summary

The application architecture is designed for scalability and real-time interactions, crucial for modern messaging platforms that require instantaneous data exchange and robust security features.
# Chat-App
