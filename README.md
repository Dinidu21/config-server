# Config Server

Centralized external configuration server for the EventSphere microservices platform, built with **Spring Cloud Config Server**.

## Student Information

- **Student Name:** Dinidu Sachintha
- **Student Number:** 241711028
- **Slack Handle:** [U0BF767MA4S](https://ijse-eca-hdse-71-72.slack.com/team/U0BF767MA4S)
- **GCP Project ID:** eventsphere-504909

## Overview

The Config Server provides a centralized location for external configuration properties across all microservices. Configuration files are stored in a Git repository and served to client applications at runtime, enabling dynamic configuration updates without redeployment.

## Tech Stack

- **Framework:** Spring Boot 4.1.0
- **Configuration Server:** Spring Cloud Config Server
- **Service Discovery:** Netflix Eureka Client
- **Version Control:** Git (config-repo)
- **Monitoring:** Spring Boot Actuator
- **Java:** 25

## Configuration

| Property | Value |
|----------|-------|
| Server Port | 8888 |
| Config Repo URL | https://github.com/Dinidu21/config-repo.git |
| Git Timeout | 10 seconds |
| Clone On Start | false |

## Architecture

```
Config Server (Port 8888)
    ├── Git Repository (config-repo)
    │   ├── eureka-server.yml
    │   ├── config-server.yml
    │   ├── api-gateway.yml
    │   ├── user-service.yml
    │   ├── event-booking-service.yml
    │   └── review-notification-service.yml
    └── Microservice Clients
        ├── Eureka Server
        ├── API Gateway
        ├── User Service
        └── Review & Notification Service
```

## Configuration Files

The Config Server serves the following application configuration files:

| File | Service | Port |
|------|---------|------|
| `eureka-server.yml` | Eureka Server | 8761 |
| `config-server.yml` | Config Server | 8888 |
| `api-gateway.yml` | API Gateway | 8080 |
| `user-service.yml` | User Service | 8081 |
| `event-booking-service.yml` | Event Booking Service | 8082 |
| `review-notification-service.yml` | Review & Notification Service | 8083 |

## Accessing Configuration

Microservices can access their configuration at:

```
http://localhost:8888/{application}/{profile}
```

Example:
```
http://localhost:8888/api-gateway/default
http://localhost:8888/user-service/default
```

## Running Locally

### Prerequisites

- Java 25
- Maven 3.9+
- Git installed and accessible

### Steps

```bash
# Build the service
mvn clean package

# Run the service
java -jar target/config-server-0.0.1-SNAPSHOT.jar
```

## Actuator Endpoints

- `GET /actuator/health` - Health check
- `GET /actuator/info` - Application info
- `POST /actuator/refresh` - Refresh configuration (when used with Spring Boot Actuator and Bus)

## Git Repository

Configuration files are stored in: https://github.com/Dinidu21/config-repo
