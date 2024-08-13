# NestJS Application with PostgreSQL and Kafka

This is a NestJS application that integrates with PostgreSQL for database management and Kafka for messaging. The application provides endpoints for user authentication and CRUD operations on users.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
  - [Authentication](#authentication)
  - [User Management](#user-management)
- [Kafka Integration](#kafka-integration)
- [Database Migrations](#database-migrations)
- [License](#license)

## Features

- **User Authentication**: Sign up, login, and secure endpoints with JWT.
- **User Management**: Full CRUD (Create, Read, Update, Delete) operations on users.
- **PostgreSQL**: Used as the primary database for storing user data.
- **Kafka**: Integrated for messaging and event-driven architecture.

## Installation

1. **Clone the repository**:

   \`\`\`bash
   git clone https://github.com/your-username/your-repository.git
   cd your-repository
   \`\`\`

2. **Install dependencies**:

   \`\`\`bash
   npm install
   \`\`\`

3. **Set up environment variables**:

   Create a \`.env\` file in the root of the project and configure it according to your environment.

## Environment Variables

Set the following environment variables in your \`.env\` file:

\`\`\`plaintext
# Application
PORT=3000
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=3600s

# PostgreSQL
DATABASE_URL=postgres://user:password@localhost:5432/your_database

# Kafka
KAFKA_BROKER=kafka:9092
KAFKA_CLIENT_ID=nestjs-app
KAFKA_GROUP_ID=nestjs-group
\`\`\`

## Running the Application

1. **Run the database migrations**:

   \`\`\`bash
   npm run typeorm migration:run
   \`\`\`

2. **Start the application**:

   \`\`\`bash
   npm run start:dev
   \`\`\`

   The application will start on the port specified in your \`.env\` file (default: \`3000\`).

## API Endpoints

### Authentication

- **POST /auth/signup**: Register a new user.

  Request body:

  \`\`\`json
  {
    "username": "string",
    "password": "string"
  }
  \`\`\`

- **POST /auth/login**: Authenticate a user and return a JWT token.

  Request body:

  \`\`\`json
  {
    "username": "string",
    "password": "string"
  }
  \`\`\`

### User Management

- **GET /users**: Get a list of all users.

- **GET /users/:id**: Get details of a specific user by ID.

- **POST /users**: Create a new user.

  Request body:

  \`\`\`json
  {
    "username": "string",
    "password": "string",
    "email": "string"
  }
  \`\`\`

- **PUT /users/:id**: Update details of a specific user by ID.

  Request body:

  \`\`\`json
  {
    "username": "string",
    "email": "string"
  }
  \`\`\`

- **DELETE /users/:id**: Delete a user by ID.

## Kafka Integration

The application is integrated with Kafka for messaging. Kafka is used to publish and consume events related to user operations, such as user creation and updates.

- **Kafka Topics**:
  - \`user_created\`: Published when a new user is created.
  - \`user_updated\`: Published when a user is updated.
  - \`user_deleted\`: Published when a user is deleted.

Configure the Kafka broker using the \`KAFKA_BROKER\` environment variable.

## Database Migrations

This application uses TypeORM for database management. Run migrations with the following command:

\`\`\`bash
npm run typeorm migration:run
\`\`\`

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
