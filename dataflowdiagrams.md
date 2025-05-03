
# 📘 Halistawi Health Application – Level 2 Data Flow Diagrams

This document contains detailed **Level 2 Data Flow Diagrams (DFD)** for each major module of the Halistawi application. These diagrams represent the internal interactions between the user interface, backend services (Laravel API), and the database (MySQL).

---

## 📊 A1c Module

```mermaid
graph TD
  User[User]
  App[Mobile App]
  API[Laravel API]
  DB[(MySQL Database)]

  User --> App
  App -->|Submit A1c Reading| API
  App -->|View A1c History| API
  App -->|Download A1c Report| API

  API --> DB
```

---

## 📅 Appointments Module

```mermaid
graph TD
  User[User]
  App[Mobile App]
  API[Laravel API]
  DB[(MySQL Database)]
  Admin[Admin Panel]

  User --> App
  App -->|Record Appointment| API
  App -->|Update Appointment| API
  App -->|View Appointments| API

  Admin -->|Manage Appointments| API

  API --> DB
```

---

## 🧪 Test Results Module

```mermaid
graph TD
  User[User]
  App[Mobile App]
  API[Laravel API]
  DB[(MySQL Database)]
  Admin[Admin Panel]

  Admin -->|Setup Test Limits| API
  Admin -->|Record Test Results| API

  User --> App
  App -->|View Test Results| API
  App -->|Download Test Reports| API

  API --> DB
```

---

## 💬 Feedback Module

```mermaid
graph TD
  User[User]
  App[Mobile App]
  API[Laravel API]
  DB[(MySQL Database)]

  User --> App
  App -->|Submit Feedback| API
  App -->|View Feedback History| API

  API --> DB
```

---

## 💊 Medication Module

```mermaid
graph TD
  User[User]
  App[Mobile App]
  API[Laravel API]
  DB[(MySQL Database)]

  User --> App
  App -->|Create Medication| API
  App -->|Update Medication| API
  App -->|Mark as Taken| API
  App -->|Refill Medication| API
  App -->|Activate/Deactivate| API
  App -->|Download Medication Reports| API

  API --> DB
```

---

## 💳 Subscriptions Module

```mermaid
graph TD
  User[User]
  App[Mobile App]
  API[Laravel API]
  DB[(MySQL Database)]

  User --> App
  App -->|View Subscription Plans| API
  App -->|Subscribe - Individual| API
  App -->|Subscribe - Group| API
  App -->|View Subscription Status| API

  API --> DB
```

---
