# 🏋️ Fit Arena

<div align="center">

![Fit Arena Logo](https://img.shields.io/badge/Fit-Arena-blue?style=for-the-badge)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen?style=flat-square&logo=spring)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat-square&logo=react)](https://reactjs.org/)
[![Kafka](https://img.shields.io/badge/Apache%20Kafka-Latest-black?style=flat-square&logo=apache-kafka)](https://kafka.apache.org/)
[![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED?style=flat-square&logo=docker)](https://www.docker.com/)

**AI-Powered Cloud-Native Fitness Platform**

[Features](#features) • [Architecture](#architecture) • [Getting Started](#getting-started) • [Documentation](#api-documentation)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [API Documentation](#api-documentation)
- [Microservices](#microservices)
- [Security](#security)
- [Event Streaming](#event-streaming)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

**Fit Arena** is a scalable, cloud-native fitness platform built using microservices architecture. It provides personalized health and workout analytics powered by AI, helping users achieve their fitness goals through intelligent recommendations and real-time activity tracking.

The platform leverages modern cloud technologies, event-driven architecture, and AI capabilities to deliver a seamless fitness experience with robust security and scalability.

---

## ✨ Features

### Core Functionality
- 🏃 **Activity Tracking**: Real-time monitoring of user workouts and physical activities
- 💪 **Workout Management**: Create, schedule, and track custom workout routines
- 📊 **Health Analytics**: Comprehensive dashboard with health metrics and progress visualization
- 🤖 **AI Recommendations**: Personalized workout and diet plans powered by Google Gemini API
- 📈 **Progress Tracking**: Historical data analysis and trend visualization
- 🔔 **Real-time Notifications**: Event-driven updates on achievements and milestones

### Technical Highlights
- ⚡ **Microservices Architecture**: Independently deployable and scalable services
- 🔐 **Enterprise Security**: OAuth2 and RBAC implementation via Keycloak
- 🌊 **Event Streaming**: Real-time data processing with Apache Kafka
- 🚀 **API Gateway**: Centralized routing and load balancing
- 📦 **Service Discovery**: Dynamic service registration with Eureka Server
- 🐳 **Containerization**: Docker support for easy deployment
- ☁️ **Cloud-Ready**: Designed for cloud deployment with Spring Cloud

---

## 🏗️ Architecture

### System Architecture Diagram


┌─────────────────────────────────────────────────────────────────┐
│                         Client Layer                             │
│                     (React Frontend)                             │
└────────────────────────────┬────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────┐
│                   Spring Cloud Gateway                           │
│              (API Gateway + Load Balancer)                       │
└──────┬──────────────────────────────────────────────────────────┘
│
├──────────────────┬──────────────────┬────────────────────┐
▼                  ▼                  ▼                    ▼
┌─────────────┐   ┌─────────────┐   ┌─────────────┐   ┌──────────────┐
│   User      │   │  Workout    │   │  Activity   │   │     AI       │
│  Service    │   │  Service    │   │  Service    │   │Recommendation│
│             │   │             │   │             │   │   Service    │
└──────┬──────┘   └──────┬──────┘   └──────┬──────┘   └──────┬───────┘
│                 │                 │                  │
└─────────────────┴─────────────────┴──────────────────┘
│
▼
┌────────────────────────┐
│   Eureka Server        │
│ (Service Discovery)    │
└────────────────────────┘
│
┌─────────────────────┼─────────────────────┐
▼                     ▼                     ▼
┌─────────────┐   ┌────────────────┐   ┌──────────────────┐
│  Keycloak   │   │ Apache Kafka   │   │ Config Server    │
│   (Auth)    │   │(Event Stream)  │   │(Configuration)   │
└─────────────┘   └────────────────┘   └──────────────────┘
│                     │
▼                     ▼
┌─────────────┐   ┌────────────────┐
│ PostgreSQL  │   │  Google Gemini │
│   / MySQL   │   │      API       │
└─────────────┘   └────────────────┘


### Microservices Overview

| Service | Purpose | Port | Database |
|---------|---------|------|----------|
| **Eureka Server** | Service discovery and registration | 8761 | - |
| **Config Server** | Centralized configuration management | 8888 | - |
| **API Gateway** | Request routing, load balancing, security | 8080 | - |
| **User Service** | User management, profiles, authentication | 8081 | PostgreSQL |
| **Workout Service** | Workout plans, exercises, scheduling | 8082 | PostgreSQL |
| **Activity Service** | Activity tracking, real-time monitoring | 8083 | PostgreSQL |
| **AI Recommendation Service** | AI-powered personalized recommendations | 8084 | PostgreSQL |
| **Frontend** | React-based user interface | 3000 | - |

---

## 🛠️ Tech Stack

### Backend
- **Framework**: Spring Boot 3.x
- **Microservices**: Spring Cloud (Gateway, Config, Netflix Eureka)
- **Security**: Keycloak (OAuth2, OpenID Connect)
- **Message Broker**: Apache Kafka
- **Database**: PostgreSQL / MySQL
- **API Documentation**: Swagger/OpenAPI
- **Build Tool**: Maven / Gradle

### Frontend
- **Framework**: React 18.x
- **State Management**: Redux / Context API
- **UI Library**: Material-UI / Tailwind CSS
- **HTTP Client**: Axios
- **Routing**: React Router

### AI & Analytics
- **AI Engine**: Google Gemini API
- **Data Processing**: Apache Kafka Streams

### DevOps
- **Containerization**: Docker
- **Orchestration**: Docker Compose
- **CI/CD**: GitHub Actions (optional)
- **Monitoring**: Spring Boot Actuator

---

## 📦 Prerequisites

Before running Fit Arena, ensure you have the following installed:

- **Java 17+** ([Download](https://www.oracle.com/java/technologies/downloads/))
- **Node.js 16+** and npm ([Download](https://nodejs.org/))
- **Docker** and Docker Compose ([Download](https://www.docker.com/))
- **PostgreSQL 14+** or **MySQL 8+** ([PostgreSQL](https://www.postgresql.org/) | [MySQL](https://www.mysql.com/))
- **Apache Kafka** (or use Docker Compose)
- **Maven 3.8+** ([Download](https://maven.apache.org/download.cgi))
- **Git** ([Download](https://git-scm.com/))

### API Keys Required
- **Google Gemini API Key** ([Get API Key](https://ai.google.dev/))

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/fit-arena.git
cd fit-arena
```

### 2. Configure Environment Variables

Create a `.env` file in the root directory:

```env
# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_NAME=fitarena
DB_USERNAME=your_db_user
DB_PASSWORD=your_db_password

# Keycloak Configuration
KEYCLOAK_URL=http://localhost:8180
KEYCLOAK_REALM=fitarena
KEYCLOAK_CLIENT_ID=fitarena-client
KEYCLOAK_CLIENT_SECRET=your_keycloak_secret

# Kafka Configuration
KAFKA_BOOTSTRAP_SERVERS=localhost:9092

# Google Gemini API
GEMINI_API_KEY=your_gemini_api_key

# Config Server
CONFIG_SERVER_URL=http://localhost:8888

# Eureka Server
EUREKA_SERVER_URL=http://localhost:8761/eureka
```

### 3. Start Infrastructure Services

Using Docker Compose:

```bash
# Start PostgreSQL, Kafka, Zookeeper, and Keycloak
docker-compose up -d
```

**docker-compose.yml** (Create this file in the root):

```yaml
version: '3.8'

services:
  postgres:
    image: postgres:14
    container_name: fitarena-postgres
    environment:
      POSTGRES_DB: fitarena
      POSTGRES_USER: fitarena_user
      POSTGRES_PASSWORD: fitarena_pass
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

  zookeeper:
    image: confluentinc/cp-zookeeper:latest
    container_name: fitarena-zookeeper
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
      ZOOKEEPER_TICK_TIME: 2000
    ports:
      - "2181:2181"

  kafka:
    image: confluentinc/cp-kafka:latest
    container_name: fitarena-kafka
    depends_on:
      - zookeeper
    ports:
      - "9092:9092"
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://localhost:9092
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1

  keycloak:
    image: quay.io/keycloak/keycloak:latest
    container_name: fitarena-keycloak
    environment:
      KEYCLOAK_ADMIN: admin
      KEYCLOAK_ADMIN_PASSWORD: admin
    ports:
      - "8180:8080"
    command: start-dev

volumes:
  postgres_data:
```

### 4. Start Microservices

#### Start in the following order:

**1. Config Server**
```bash
cd config-server
mvn spring-boot:run
```

**2. Eureka Server**
```bash
cd eureka-server
mvn spring-boot:run
```

**3. API Gateway**
```bash
cd api-gateway
mvn spring-boot:run
```

**4. Core Services** (in parallel)
```bash
# Terminal 1 - User Service
cd user-service
mvn spring-boot:run

# Terminal 2 - Workout Service
cd workout-service
mvn spring-boot:run

# Terminal 3 - Activity Service
cd activity-service
mvn spring-boot:run

# Terminal 4 - AI Recommendation Service
cd ai-recommendation-service
mvn spring-boot:run
```

### 5. Start Frontend

```bash
cd frontend
npm install
npm start
```

### 6. Access the Application

- **Frontend**: http://localhost:3000
- **API Gateway**: http://localhost:8080
- **Eureka Dashboard**: http://localhost:8761
- **Keycloak Admin**: http://localhost:8180 (admin/admin)

---

## ⚙️ Configuration

### Spring Cloud Config

Configuration files are managed centrally through Spring Cloud Config Server. Create configuration files in the `config-repo` directory:

config-repo/
├── application.yml           # Common configuration
├── user-service.yml         # User service specific
├── workout-service.yml      # Workout service specific
├── activity-service.yml     # Activity service specific
└── ai-recommendation-service.yml

**Example application.yml**:

```yaml
spring:
  datasource:
    url: jdbc:postgresql://${DB_HOST}:${DB_PORT}/${DB_NAME}
    username: ${DB_USERNAME}
    password: ${DB_PASSWORD}
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true

eureka:
  client:
    service-url:
      defaultZone: ${EUREKA_SERVER_URL}

management:
  endpoints:
    web:
      exposure:
        include: health,info,metrics

logging:
  level:
    root: INFO
    com.fitarena: DEBUG
```

### Keycloak Setup

1. Access Keycloak Admin Console: http://localhost:8180
2. Create a new realm: `fitarena`
3. Create client: `fitarena-client`
4. Configure OAuth2 settings
5. Create roles: `USER`, `ADMIN`, `TRAINER`
6. Create test users

---

## 📚 API Documentation

### User Service API

#### Authentication
```http
POST /api/auth/register
POST /api/auth/login
POST /api/auth/logout
POST /api/auth/refresh
```

#### User Management
```http
GET    /api/users/{id}
PUT    /api/users/{id}
DELETE /api/users/{id}
GET    /api/users/profile
PUT    /api/users/profile
```

### Workout Service API

```http
GET    /api/workouts
POST   /api/workouts
GET    /api/workouts/{id}
PUT    /api/workouts/{id}
DELETE /api/workouts/{id}
GET    /api/workouts/user/{userId}
POST   /api/workouts/{id}/exercises
```

### Activity Service API

```http
GET    /api/activities
POST   /api/activities
GET    /api/activities/{id}
GET    /api/activities/user/{userId}
GET    /api/activities/stats
POST   /api/activities/track
```

### AI Recommendation Service API

```http
POST   /api/recommendations/workout
POST   /api/recommendations/diet
GET    /api/recommendations/user/{userId}
POST   /api/recommendations/analyze
```

**Swagger Documentation**: Available at `http://localhost:8080/swagger-ui.html` when services are running.

---

## 🔐 Security

### Authentication Flow

1. User authenticates via Keycloak
2. Keycloak issues JWT access token
3. API Gateway validates token for each request
4. Services use token to identify user and enforce RBAC

### Security Features

- **OAuth2 / OpenID Connect**: Industry-standard authentication
- **Role-Based Access Control (RBAC)**: Fine-grained permissions
- **JWT Tokens**: Stateless authentication
- **API Gateway Security**: Centralized security enforcement
- **HTTPS**: Encrypted communication (production)

---

## 📡 Event Streaming

### Kafka Topics

| Topic | Producer | Consumer | Purpose |
|-------|----------|----------|---------|
| `workout-events` | Workout Service | Activity Service, AI Service | Workout creation/updates |
| `activity-events` | Activity Service | AI Service, User Service | Real-time activity tracking |
| `user-events` | User Service | All Services | User profile changes |
| `recommendation-events` | AI Service | User Service, Notification Service | AI recommendations |

### Event Schema Example

```json
{
  "eventId": "uuid",
  "eventType": "WORKOUT_COMPLETED",
  "userId": "user-123",
  "timestamp": "2024-01-15T10:30:00Z",
  "data": {
    "workoutId": "workout-456",
    "duration": 3600,
    "caloriesBurned": 450,
    "exercises": [...]
  }
}
```

---

## 🧪 Testing

### Run Unit Tests
```bash
mvn test
```

### Run Integration Tests
```bash
mvn verify
```

### Test Coverage
```bash
mvn jacoco:report
```

---

## 📊 Monitoring

### Spring Boot Actuator Endpoints

- **Health**: `http://localhost:8080/actuator/health`
- **Metrics**: `http://localhost:8080/actuator/metrics`
- **Info**: `http://localhost:8080/actuator/info`

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Commit changes**: `git commit -m 'Add amazing feature'`
4. **Push to branch**: `git push origin feature/amazing-feature`
5. **Open a Pull Request**

### Coding Standards
- Follow Java Code Conventions
- Write unit tests for new features
- Update documentation as needed
- Use meaningful commit messages

---


## 👥 Authors

- **KARAN PATIDAR** - *Initial work* - [YourGitHub](https://github.com/karanpatel47)

---

## 🙏 Acknowledgments

- Spring Boot and Spring Cloud teams
- Apache Kafka community
- Keycloak project
- Google Gemini API
- All contributors

---

<div align="center">

**⭐ Star this repo if you find it helpful!**


</div>
