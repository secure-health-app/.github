# SmartGuardian

SmartGuardian is a secure AI-integrated healthcare monitoring system designed to support vulnerable users through real-time fall detection, wearable health analysis, and emergency alerting.

## System Overview

SmartGuardian combines an IoT fall-detection device, a secure backend API, and a mobile-friendly web dashboard.

The Raspberry Pi detects falls locally, the backend processes health data, and the frontend displays alerts and trends.

## Application Preview

<p align="center">
  <img src="https://github.com/user-attachments/assets/6bab1671-a6b7-4cdf-841d-723ebaba740c" width="800">
</p>
<p align="center"><em>User dashboard, fall confirmation workflow, caregiver emergency response, acknowledged response</em></p>

## Live Demo

- [Watch SmartGuardian Screencast Demo (YouTube)](https://www.youtube.com/watch?v=i_r_CQjFKRY)
- [Frontend Application](https://health-app-frontend-1vl1.onrender.com/)

> Initial load may take a few seconds while the Render service wakes.
  
## Academic Deliverables 
- [Dissertation PDF](https://github.com/user-attachments/files/27100120/G00424657_Louise_Deeth_SmartGuardian_Dissertation.pdf)
- [Poster (PPTX)](https://github.com/user-attachments/files/27100141/Poster.pptx)

## Repositories

| Repository | Description |
|---|---|
| [health-app-backend](https://github.com/secure-health-app/health-app-backend) | Spring Boot REST API, JWT authentication, PostgreSQL |
| [health-app-frontend](https://github.com/secure-health-app/health-app-frontend) | React PWA dashboard |
| [pi-fall-detector](https://github.com/secure-health-app/pi-fall-detector) | Raspberry Pi fall detection and ML dataset generation |

> Each repository contains its own installation and run instructions.

## Project Objectives

- Detect fall events using motion sensing and machine learning
- Analyse long-term health trends using Fitbit wearable data
- Provide timely emergency alerts when a fall is detected
- Ensure secure handling of sensitive health data in line with GDPR principles
- Detect gradual health deterioration through Fitbit anomaly detection

## Key Results

- 99.7% test accuracy, 95% fall recall, 0 false emergency alerts during live testing (Random Forest)
- 3.74 s average end-to-end alert latency
- Fitbit integration for heart rate, sleep and activity trends
- SUS usability score: 97/100
- Fully deployed cloud-hosted prototype
  
## Technology Stack

- **Frontend:** React (Progressive Web App)
- **Backend:** Spring Boot (Java)
- **Security:** Spring Security, JWT authentication
- **Database:** PostgreSQL
- **IoT:** Raspberry Pi 5, Sense HAT V2 (accelerometer + gyroscope)
- **Machine Learning:** Python (scikit-learn)
- **External APIs:** Fitbit Web API


## System Architecture

```mermaid
flowchart TB
    Client["React PWA\nDashboard"]
    Backend["Spring Boot Backend API\n+ PostgreSQL Database"]
    Pi["Raspberry Pi 5\nSense HAT"]
    Fitbit["Fitbit Web API"]

    Client <-->|HTTPS + JWT| Backend
    Pi -->|Fall Alerts\nX-Device-Key| Backend
    Fitbit -->|Fitbit Metrics\n HR Steps Sleep| Backend
    Backend -->|REST API Responses| Client
```

## Detection Architecture (Edge Device)

```mermaid
flowchart LR
    IMU["Sense HAT IMU"]

    Rules["Rule-Based Detection
Freefall / Impact / Stillness"]

    Features["Sliding Window
Feature Extraction"]

    ML["Random Forest
Classifier"]

    Decision["Hybrid Decision Logic"]

    Alert["POST /api/alerts/fall"]

    Dataset["Training Dataset CSV"]

    IMU --> Rules
    IMU --> Features
    Features --> ML
    Features --> Dataset
    Rules --> Decision
    ML --> Decision
    Decision --> Alert
```

## Future Work

- Multi-user caregiver and healthcare provider dashboards
- Push notifications, SMS, and voice alerts
- Additional wearable integrations (Apple Health, Garmin)
- Voice activation ("help" command)
- Multi-factor authentication (MFA)
  
## Real World Impact

SmartGuardian was designed to improve emergency response times for falls, support independent living, and give caregivers better visibility into long-term health trends.

---

Developed by Louise Deeth • Atlantic Technological University Galway (ATU) • Final Year Project.
