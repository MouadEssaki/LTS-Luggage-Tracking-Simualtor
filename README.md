# LTS - Luggage Tracking Simulator

## Description
LTS - Luggage Tracking Simulator is an industrial simulation project. This system simulates real-time baggage flow within an automated sorting center.

The objective is to demonstrate the management of telemetry data streams, their processing through a microservices architecture, and their dynamic visualization via an industrial dashboard coupled with a 3D scene.

---

## Tech Stack

| Component | Technology | Role |
| :--- | :--- | :--- |
| Backend | Java 21 + Spring Boot 3 | Simulation, Business Logic, and API |
| Messaging | Apache Kafka | Asynchronous Data Transport |
| Frontend | Angular 22 | User Interface and Dashboard |
| Visualization | Three.js | Real-time 3D Rendering of Baggage |
| Real-Time | WebSockets (STOMP) | Data Push from Backend to UI |
| DevOps | Docker & Docker Compose | Containerization and Orchestration |
| Quality | JUnit 5 & Javadoc | Unit Testing and Technical Documentation |