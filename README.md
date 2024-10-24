
# NestJs Application with Redis, PostgreSQL, and Kafka

This application is an API (Express) using NestJs as the framework, Redis for authentication caching, PostgreSQL as the application's default database, and Kafka for sending and receiving log messages.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Swagger](#swagger)
- [Redis](#redis)
- [Kafka Integration](#kafka-integration)

## Features

- **User Authentication**: Registration, login, and endpoint protection with JWT.
- **User Management**: Complete CRUD (Create, Read, Update, Delete) operations for users.
- **PostgreSQL**: Used as the main database to store user data.
- **Redis**: Used as a database for caching the authorization token.
- **Kafka**: Integrated for messaging and event-driven architecture.
- **Swagger**: Automatic documentation of endpoints.

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/Vitor-742/starsoft-test.git
   cd starsoft-test
   ```

2. **Install dependencies**:

   ```bash
   npm install
   ```

3. **Start the Docker containers**:

   ```bash
   docker-compose up -d
   ```

## Running the Application

1. **Start the application**:

   ```bash
   npm start
   ```

   The application will start on the port specified in your `.env` file (default: `3000`).

## API Endpoints
- To see all the API endpoints, visit Swagger.

## Swagger

- [Local Swagger](http://localhost:3000/api/)
- To authenticate requests using a Bearer Token in the Swagger interface, follow these steps:
    - Login in Swagger is done with predefined information, so the default is to work with the already configured credentials. If you want to use your own authentication or are on the local repository, register through the POST /users endpoint, which is also public.
    - Obtain the Token: First, log in through the /auth/login endpoint to get the JWT token. This token will be returned in the accessToken field of the response.
    - Set up Authentication in Swagger: In the top right corner of the Swagger interface, click the Authorize button. A modal window will open.
    - Enter the Token: In the authentication field, enter the JWT token preceded by the word Bearer, for example: Bearer your_token_here. Click Authorize to apply the token.
    - Make Requests: Now you can make authenticated requests to the protected API endpoints. The token will be automatically included in the Authorization header of each request.

## Redis
- In the application, Redis is being used as a cache for user authentication; thus, after 5 minutes, your token expires, and you need to re-authenticate the user.

## Kafka Integration

The application is integrated with Kafka for messaging. Kafka is used to publish and consume events related to user operations, such as creating and updating users.

- **Kafka Topics**:
  - `user_created`: Published when a new user is created.
  - `user_updated`: Published when a user is updated.

  - As a visual response from Kafka, every time a user is created or updated, a log message is emitted to the console.

![Screenshot 2024-08-12 201301](https://github.com/user-attachments/assets/46b6bd5b-935d-4963-b759-f12360f653ff)
