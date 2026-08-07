# LTS - Luggage Tracking Simulator

## Description
LTS - Luggage Tracking Simulator is an industrial simulation project. This system simulates real-time baggage flow within an automated sorting center.

The objective is to demonstrate the management of telemetry data streams, their processing through a microservices architecture, and their dynamic visualization via an industrial dashboard coupled with a 3D scene.

---

## Tech Stack

| Component | Technology | Role |
| :--- | :--- | :--- |
| Backend | Java 21 + Spring Boot 4 | Simulation, Business Logic, and API |
| Messaging | Apache Kafka | Asynchronous Data Transport |
| Database | PostgreSQL | Persistence and application data |
| Frontend | Angular 22 | User Interface and Dashboard |
| Visualization | Three.js | Real-time 3D Rendering of Baggage |
| Real-Time | WebSockets (STOMP) | Data Push from Backend to UI |
| DevOps | Docker & Docker Compose | Containerization and Orchestration |
| Quality | JUnit 5 & Javadoc | Unit Testing and Technical Documentation |

---

## Local setup

### 1. Copy the environment template
```bash
copy .env.example .env
```

Then update the values in [.env](.env) with your local secrets.

### 2. Start the full stack
```bash
docker compose --env-file .env up --build
```

This starts:
- PostgreSQL on port 5432
- Zookeeper on the internal Docker network
- Kafka on port 9092
- Spring Boot backend on port 8080
- Angular frontend on port 4200

### 3. Useful commands
```bash
docker compose --env-file .env ps
docker compose --env-file .env logs -f backend
docker compose --env-file .env logs -f postgres
docker compose --env-file .env down
```

---

## Environment variables

The project uses a local [.env](.env) file for sensitive configuration. The example template is in [.env.example](.env.example).

Example values:
```env
POSTGRES_DB=ltsdb
POSTGRES_USER=postgres
POSTGRES_PASSWORD=change_me
POSTGRES_PORT=5432

SPRING_DATASOURCE_URL=jdbc:postgresql://postgres:5432/ltsdb
SPRING_DATASOURCE_USERNAME=postgres
SPRING_DATASOURCE_PASSWORD=change_me

KAFKA_BOOTSTRAP_SERVERS=kafka:9092
SPRING_KAFKA_BOOTSTRAP_SERVERS=kafka:9092
```

Do not commit the real [.env](.env) file.

---

## Notes

- Docker Compose uses the environment file for both PostgreSQL and Spring Boot configuration.
- The backend depends on PostgreSQL and Kafka being available before it starts cleanly.
- The project currently uses Spring Boot with JPA and PostgreSQL persistence enabled.