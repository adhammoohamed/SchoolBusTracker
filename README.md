# SchoolBusTracker 🚌

**A Native Android School Bus Tracking System**

SchoolBusTracker is an Android application designed to improve school transportation visibility, communication, and operational reliability through real-time bus tracking and trip management.

Built with **Kotlin** and **Jetpack Compose**, this project explores modern Android development practices, scalable application architecture, background location tracking, offline-first capabilities, and real-time communication.

> **Project Status:** 🚧 Under Active Development

---

## 🎯 Project Goals

The primary goal is to design and build a reliable Android application for school transportation, while applying real-world software engineering principles throughout the development process.

This project also serves as an engineering learning environment for exploring and implementing:

- Modern Android development with Kotlin and Jetpack Compose.
- Gradle multi-module architecture and modularization strategies.
- Clean Architecture, MVVM, and unidirectional data flow.
- Reliable background location tracking and Foreground Services.
- Offline-first data management and synchronization.
- REST API integration and real-time communication.
- Dependency injection, automated testing, and CI/CD.
- Android performance, security, and battery optimization.

---

## 👥 Application Roles

The application is designed around two primary user roles.

### 🚌 Driver

The driver experience focuses on managing assigned school trips and sharing the bus's live location.

Planned capabilities:

- Secure authentication.
- Retrieve assigned trips and bus information.
- View students, pickup points, and planned routes.
- Start and end trips.
- Share live GPS location with the backend.
- Confirm student boarding.
- Mark students as absent.
- Handle network interruptions and synchronize pending actions.

### 👨‍👩‍👧 Parent

The parent experience focuses on tracking the assigned school bus and receiving trip updates.

Planned capabilities:

- View the bus's live location on a map.
- Track estimated arrival time and distance.
- View pickup point and trip information.
- Receive notifications about approaching buses.
- Receive arrival and boarding updates.
- Access the latest available trip information.

---

## 🏗️ Architecture & Technology Stack

The project is being developed using modern Android technologies and architectural principles.

| Area                    | Technology / Approach             |
| ----------------------- | --------------------------------- |
| Language                | Kotlin                            |
| UI                      | Jetpack Compose                   |
| Design System           | Material 3                        |
| Architecture            | Clean Architecture + MVVM         |
| UI State                | Coroutines + StateFlow            |
| Dependency Injection    | Hilt                              |
| Networking              | Retrofit + OkHttp                 |
| Local Database          | Room                              |
| Preferences             | DataStore                         |
| Maps                    | Google Maps SDK / Maps Compose    |
| Location                | Fused Location Provider           |
| Background Execution    | Foreground Services + WorkManager |
| Real-time Communication | WebSockets                        |
| Push Notifications      | Firebase Cloud Messaging          |
| Testing                 | JUnit 5 and Android testing tools |
| Build System            | Gradle Kotlin DSL                 |
| CI/CD                   | GitHub Actions                    |

*Technology choices and implementation details may evolve as the project progresses.*

---

## 🧩 Planned Project Structure

The application will follow a feature-based modular architecture.

```text
SchoolBusTracker/
│
├── app/
│
├── core/
│   ├── common/
│   ├── designsystem/
│   ├── network/
│   ├── database/
│   ├── location/
│   ├── maps/
│   └── notifications/
│
├── feature/
│   ├── authentication/
│   ├── driver-trip/
│   ├── parent-tracking/
│   └── boarding/
│
├── build-logic/
│
├── gradle/
│
├── docs/
│   ├── architecture/
│   ├── adr/
│   ├── api-contracts/
│   ├── diagrams/
│   └── testing/
│
└── .github/
    └── workflows/
```

This is the proposed structure, not a claim that all modules have already been implemented.

Modules will be introduced incrementally based on actual architectural needs, avoiding unnecessary complexity and premature abstraction.

---

## 🗺️ How It Works

The intended high-level workflow is:

1. The driver authenticates and retrieves their assigned trip.
2. The driver starts the trip.
3. A location Foreground Service begins collecting GPS updates.
4. Location updates are validated and sent to the backend.
5. The backend processes bus proximity, trip events, and estimated arrival information.
6. Parents receive real-time updates and notifications.
7. The driver confirms boarding or marks a student as absent.
8. The backend validates and persists these actions.
9. The driver ends the trip.

### Backend Responsibility

The backend is intended to remain the source of truth for:

- Driver, bus, and student assignments.
- Trip and boarding states.
- Route ordering and optimization.
- Proximity detection and arrival events.
- Estimated arrival information.
- Notification decisions and delivery triggers.

The Android application is responsible for location acquisition, local data management, user interactions, map visualization, and communication with backend services.

---

## 📡 Offline-First & Reliability

Reliable behavior under unstable network conditions is an important engineering objective.

Planned mechanisms include:

- Local persistence using Room.
- Pending location and action queues.
- Deferred synchronization when connectivity returns.
- Idempotent requests to prevent duplicate operations.
- Retry strategies and network error handling.
- WebSocket reconnection and state recovery.
- Clear distinction between locally pending actions and server-confirmed operations.

---

## 🧪 Testing Strategy

Testing will be introduced throughout development rather than postponed until the end.

Planned testing areas include:

- Unit testing for business rules and use cases.
- Repository and data-layer testing.
- Coroutine and Flow testing.
- REST API testing.
- Local database testing.
- Compose UI testing.
- Background location service testing.
- Offline synchronization and failure scenarios.
- WebSocket reconnection and event handling.

Special attention will be given to GPS accuracy, network interruptions, duplicate events, process death, and permission changes.

---

## 🔐 Security Considerations

Security will be considered throughout the implementation.

Areas of focus include:

- Secure authentication and session management.
- Safe credential and token storage.
- HTTPS communication.
- Proper authorization handling.
- Permission management.
- Avoiding sensitive information in application logs.
- Protecting API credentials and release secrets.

Authentication and authorization decisions will remain enforced by the backend.

---

## 📚 Engineering Documentation

Architecture and technical decisions will be documented as the project evolves.

The documentation will include:

- Architecture diagrams.
- Architecture Decision Records (ADRs).
- Module dependency diagrams.
- API contracts and event schemas.
- Testing strategy and test scenarios.
- Technical implementation notes.

The goal is to make architectural decisions explicit, explain their trade-offs, and keep the documentation aligned with the actual implementation.

---

## 🚀 Development Roadmap

The project will be developed incrementally.

- [ ] Requirements analysis and architecture design.
- [ ] Gradle fundamentals and multi-module project setup.
- [ ] Module dependency boundaries.
- [ ] Navigation architecture.
- [ ] Dependency injection setup.
- [ ] Authentication and session management.
- [ ] Trip domain and state management.
- [ ] Maps integration and GPS tracking.
- [ ] Background location Foreground Service.
- [ ] Room database and offline-first synchronization.
- [ ] WebSocket real-time communication.
- [ ] Boarding management and notifications.
- [ ] Automated testing and CI/CD.
- [ ] Performance, security, and reliability improvements.

Progress will be reflected in this roadmap as features are implemented and verified.

---

## 🛠️ Development Principles

The project follows several engineering principles:

- **Separation of Concerns:** Each component has a clearly defined responsibility.
- **Dependency Inversion:** Business logic should not depend on implementation details.
- **Single Source of Truth:** Backend-owned business states remain authoritative.
- **Testability:** Business rules and critical workflows should be independently testable.
- **Reliability:** Network failures and lifecycle changes are expected, not exceptional.
- **Incremental Architecture:** Complexity should be introduced only when justified.
- **Maintainability:** Code and documentation should support future development.

---

## 📌 Current Development Status

This repository is currently in its initial development stage.

The architecture, module boundaries, and technical decisions are being explored and documented before implementing the complete application.

Features listed above represent the planned scope and should not be considered completed unless explicitly marked as implemented.

---

## 📄 License

License information will be added once the project's distribution and usage requirements are defined.
