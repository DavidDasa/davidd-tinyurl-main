# README for TinyURL Project

This project demonstrates the implementation of a URL shortening service (TinyURL) using Spring Boot, Redis, MongoDB, and Cassandra. The system is designed to generate short URLs, store them in Redis, log analytics in MongoDB, and record user clicks in Cassandra.

## Setup

### 1. Hosts Configuration

Edit the `/etc/hosts` file to include the following entries:

```bash
sudo vi /etc/hosts

127.0.0.1 cassandra
127.0.0.1 redis
127.0.0.1 mongo
```

### 2. Swagger Configuration

Update the `pom.xml` file to use Swagger version 2.5.2:

```xml
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>2.5.2</version>
</dependency>

<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>2.5.2</version>
</dependency>
```

Configure Swagger in `config/SwaggerConfig.java` and create a sample API in `controller/AppController.java`.

Access Swagger UI at [http://localhost:8080/swagger-ui.html#](http://localhost:8080/swagger-ui.html#).

### 3. Redis Configuration

Update `docker-compose.yml` to include a Redis service:

```yaml
services:
  redis:
    image: redis
    ports:
      - 6379:6379
    privileged: true
```

Run Redis using:

```bash
docker-compose up -d
docker ps
docker exec -it [your container] /bin/bash 
cd /usr/local/bin/
redis-cli SET abc 1
redis-cli GET abc
redis-cli SETNX abc 1
redis-cli SETNX abcd 1
```

### 4. MongoDB Configuration

Update `pom.xml` with MongoDB dependencies:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>

<dependency>
    <groupId>joda-time</groupId>
    <artifactId>joda-time</artifactId>
    <version>2.10.13</version>
</dependency>
```

Update `docker-compose.yml` to include a MongoDB service:

```yaml
services:
  mongo:
    image: mongo:4.0
    ports:
      - 27017:27017
    privileged: true
```

### 5. Cassandra Configuration

Update `pom.xml` with Cassandra dependencies:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-cassandra</artifactId>
</dependency>
```

Update `docker-compose.yml` to include a Cassandra service:

```yaml
services:
  cassandra:
    image: "cassandra:3.11.9"
    ports:
      - "9042:9042"
    environment:
      - "MAX_HEAP_SIZE=256M"
      - "HEAP_NEWSIZE=128M"
```

Run the following Cassandra CQL command:

```cql
CREATE KEYSPACE tiny_keyspace
WITH replication = {'class':'SimpleStrategy', 'replication_factor' : 1};
```

### 6. Application Configuration

Update `application.properties` with respective configurations for Redis, MongoDB, and Cassandra.

### 7. Run the Application

Run the application and access the various functionalities provided by the TinyURL service, including URL shortening, analytics logging, and user clicks.

