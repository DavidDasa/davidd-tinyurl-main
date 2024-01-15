# TinyURL Project Summary

The TinyURL project is a comprehensive demonstration of a URL shortening service implemented with Spring Boot, Redis, MongoDB, and Cassandra. The system enables the generation of short URLs, their storage in Redis, analytics logging in MongoDB, and user click tracking in Cassandra.

## Key Components

### 1. Swagger Documentation

Integrates Swagger for API documentation, allowing easy exploration of available endpoints and functionalities.

### 2. Redis Integration

Utilizes Redis as a fast and efficient in-memory data store for managing short URLs and related data.

### 3. MongoDB Analytics Logging

Logs analytics data in MongoDB, providing insights into URL usage and user interactions with the service.

### 4. Cassandra User Click Tracking

Records user clicks on shortened URLs in Cassandra, enabling detailed tracking and analysis of user engagement.

## Setup Instructions

1. **Hosts Configuration:** Modify the `/etc/hosts` file to include necessary local development entries.

2. **Swagger Configuration:** Update the `pom.xml` file to use Swagger version 2.5.2 for API documentation.

3. **Redis Configuration:** Add a Redis service to the `docker-compose.yml` file for storing short URLs and related data.

4. **MongoDB Configuration:** Integrate MongoDB by adding dependencies to the `pom.xml` file and including a MongoDB service in the `docker-compose.yml` file.

5. **Cassandra Configuration:** Add Cassandra dependencies to the `pom.xml` file and include a Cassandra service in the `docker-compose.yml` file.

6. **Application Configuration:** Update the `application.properties` file with the necessary configurations for Redis, MongoDB, and Cassandra.

7. **Run the Application:** Start the application to explore and use the various features of the TinyURL service.

