# IMed Helix

> **AI-powered medical appointment and pre-diagnosis kiosk system.**  
> A research and development project conducted at **Tyumen Industrial University (TIU)** — designed to revolutionize patient–clinic interaction through neural network–driven triage, intelligent scheduling, and offline-first kiosk infrastructure.

![Status](https://img.shields.io/badge/status-prototype-blue)
![Stack](https://img.shields.io/badge/stack-Python%20%7C%20FastAPI%20%7C%20PyTorch-orange)
![License](https://img.shields.io/badge/source-proprietary--TIU-lightgrey)

> ⚠️ **Important Notice**  
> **The full source code of this project is the intellectual property of Tyumen Industrial University (TIU) and is not publicly available.**  
> This repository is a **technical showcase and portfolio document** describing the project's goals, architecture, methodology, and my individual contribution.  
> No proprietary code, datasets, or trained models are published here.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Problem Statement](#problem-statement)
3. [Goals and Objectives](#goals-and-objectives)
4. [Solution](#solution)
5. [System Architecture](#system-architecture)
6. [Functional Modules](#functional-modules)
7. [Key Performance Indicators](#key-performance-indicators)
8. [Competitive Analysis](#competitive-analysis)
9. [Target Audience](#target-audience)
10. [Market Analysis](#market-analysis)
11. [My Role and Contribution](#my-role-and-contribution)
12. [Security Implementation](#security-implementation)
13. [Technology Stack](#technology-stack)
14. [Team](#team)
15. [Project Context](#project-context)
16. [Note on Source Code](#note-on-source-code)

---

## Project Overview

**IMed Helix** is an integrated software–hardware solution that simplifies the process of booking appointments and visiting medical specialists. The system combines a self-service kiosk, a neural network–based pre-diagnosis engine, and a real-time clinic optimization layer.

The product is designed to reduce administrative load on medical staff, eliminate long queues, and provide patients with a fast, intuitive, and personalized experience — all while operating fully offline within the clinic's local infrastructure.

The project was developed as part of the university research initiative at **Tyumen Industrial University (Тюменский индустриальный университет, ТИУ)** during the 2025 academic cycle.

---

## Problem Statement

Even in regions with high digitization, patients continue to experience friction when scheduling and visiting doctors.

**Quantitative findings:**

| Indicator | Value |
|-----------|-------|
| Patients in major clinics and medical centers (sample) | 20,000+ |
| Patients reporting dissatisfaction with current booking systems | **55%** |
| Average time doctors spend per patient (incl. admin tasks) | **15 min** |

**Regional digitization rates (Russia):**

| Region | Digitization |
|--------|--------------|
| Saint Petersburg | 75% |
| Moscow / Republic of Buryatia | ~49% |
| Krasnodar Krai | 48% |
| Sverdlovsk Oblast / Tyumen | 45% |

**Core pain points:**
- Long appointment booking times (2–3 minutes on existing platforms).
- Patients are routed to the wrong specialist due to lack of pre-screening.
- Doctors lose ~30% of their consultation time on administrative work.
- Existing systems require stable internet — unreliable in remote regions.
- Limited integration between booking platforms and clinic-internal Medical Information Systems (MIS).

---

## Goals and Objectives

### Primary Goal
Revolutionize the medical appointment process by making it **fast, intuitive, and efficient** through the application of artificial intelligence — saving time for both patients and medical staff.

### Objectives
1. **Optimize patient flow** to reduce queues and bottlenecks at registration.
2. **Implement AI-driven pre-diagnosis** to route patients to the correct specialist.
3. **Radically simplify the booking process** down to a 30-second self-service interaction.
4. **Increase the operational efficiency** of medical institutions through schedule optimization and predictive analytics.

---

## Solution

IMed Helix is a self-service kiosk deployed at the entrance of a medical institution. The patient interacts with a touchscreen interface, authenticates via a personal QR code, describes their symptoms, and receives an automatic appointment with the most relevant specialist — all in approximately 30 seconds.

In parallel, the system continuously learns from anonymized usage patterns to:
- Predict daily and weekly patient load.
- Redistribute doctors' schedules dynamically.
- Personalize the booking experience based on each patient's history.
- Provide administrators with real-time analytics dashboards.

---

## System Architecture

```
                       ┌────────────────────────────┐
                       │   AI / ML Inference Layer  │
                       │  (PyTorch, scikit-learn)   │
                       └─────────────┬──────────────┘
                                     │
   ┌────────────┐    ┌───────────────▼────────────────┐    ┌───────────────┐
   │  Patient   | ── |      Intelligent Booking       │ ── |    Doctor /   |
   │  (Kiosk)   │    │           Module               │    │  Specialist   │
   └────────────┘    └───────────────┬────────────────┘    └───────────────┘
                                     │
        ┌────────────────────────────┼────────────────────────────┐
        ▼                            ▼                            ▼
┌────────────────┐         ┌──────────────────┐         ┌────────────────────┐
│  Schedule      │         │  Patient History │         │  Notification &    │
│  Optimizer     │         │  & Preferences   │         │  Reminder Service  │
└────────────────┘         └──────────────────┘         └────────────────────┘
        │                            │                            │
        └────────────────────────────┼────────────────────────────┘
                                     ▼
                       ┌────────────────────────────┐
                       │      REST / WebSocket      │
                       │            API             │
                       └─────────────┬──────────────┘
                                     │
                       ┌─────────────▼──────────────┐
                       │   Clinic MIS Integration   │
                       │ (Electronic Records, EHR,  │
                       │   Insurance Systems)       │
                       └────────────────────────────┘
```

---

## Functional Modules

| # | Module | Description |
|---|--------|-------------|
| 1 | **Intelligent Booking Module** | Analyzes patient-described symptoms via NLP + classifier and routes to the correct specialist. |
| 2 | **AI Pre-Diagnosis Engine** | Neural network providing probabilistic diagnosis suggestions to assist the doctor. |
| 3 | **Preference & History Analyzer** | Personalizes the booking experience based on the patient's previous visits and preferences. |
| 4 | **Patient Flow Predictor** | Forecasts patient load to help administrators allocate resources proactively. |
| 5 | **Notification & Reminder Service** | Sends appointment confirmations and reminders via SMS / Telegram / email. |
| 6 | **Schedule Optimizer** | Dynamically redistributes doctor availability based on real-time demand. |
| 7 | **Analytics Dashboard** | Provides administrators and physicians with KPIs and operational insights. |
| 8 | **Feedback Processing Module** | Collects and analyzes patient feedback for continuous service improvement. |
| 9 | **MIS Integration API** | Bridges the kiosk system with the clinic's existing Medical Information System. |

All modules communicate through an internal asynchronous event bus, allowing the system to function as a single, cohesive organism.

---

## Key Performance Indicators

| KPI | Target | Description |
|-----|--------|-------------|
| **Pre-diagnosis Accuracy** | **85%** | Accuracy of AI-based symptom-to-specialty classification. |
| **Booking Time** | **30 sec** | Average time required for a patient to complete an appointment via the kiosk. |
| **Throughput Increase** | **+40%** | Improvement in the number of patients a clinic can process per day. |
| **Queue Wait Time** | **−70%** | Reduction in average patient wait time in the registration queue. |

---

## Competitive Analysis

| Feature | **IMed Helix** | EMIAS / Gosuslugi | Microsoft AI Health | Legacy Kiosks |
|---------|:--:|:--:|:--:|:--:|
| AI-based pre-diagnosis | ✅ | ❌ | ✅ | ❌ |
| Offline / local deployment | ✅ | ❌ | ❌ | ⚠ Partial |
| QR-code authentication | ✅ | ⚠ App only | ❌ | ❌ |
| Full MIS integration | ✅ | ⚠ State only | ❌ | ⚠ Basic |
| Personal data protection | ✅ (on-premise) | ✅ | ⚠ Cloud | ✅ |
| Booking time | **30 sec** | 2–3 min | 1–2 min | 1–2 min |
| Intuitive interface | ✅ | ⚠ Complex nav | ✅ | ⚠ Outdated UI |
| Self-learning system | ✅ | ❌ | ✅ | ❌ |

**Key differentiators:** offline-first deployment, on-premise data isolation, sub-minute booking flow, and a self-improving AI core.

---

## Target Audience

The product targets three interconnected user groups:

| Group | Share of Market / Users | Notes |
|-------|--:|-------|
| **Medical Institutions** | 65% | Primary buyers — public clinics (40%) and private clinics (25%). |
| **Medical Personnel** | 20% | Physicians (12%) and administrative staff (8%). |
| **Patients** | 15% | Direct end-users of the kiosk interface. |

**Key insight:** medical institutions are the *purchasers*, but value is distributed across all three groups. The system exhibits a **synergistic effect** — the more participants use it, the higher its overall efficiency becomes.

---

## Market Analysis

The market size was calculated using the **top-down** methodology.

### Market Composition (Russia)

| Institution Type | Count |
|------------------|------:|
| State hospitals | 5,065 |
| Private clinics | 3,692 |
| Non-commercial medical organizations | 312 |
| **Total** | **9,069** |

### Market Sizing

| Metric | Value |
|--------|------:|
| **TAM** (Total Addressable Market) | ₽171,395,000 |
| Competitor share | 33.9% |
| **SAM** (Serviceable Addressable Market) | ₽8,989,600 |
| Realistic capture share | 11% |
| **SOM** (Serviceable Obtainable Market) | ₽961,887 |
| Projected revenue at 10% institution coverage | ₽17,139,500 |
| **Payback period** | **201 days** |

The 201-day payback period makes IMed Helix highly attractive from an investment perspective, especially given the recurring nature of clinic licensing.

---

## My Role and Contribution

**Saveliy Golubev** — *Neural Network Algorithm Developer & Security Engineer*.

### AI / ML Track

- Designed the **symptom-to-specialty classification** model achieving 85% accuracy.
- Built the **personalization layer** that adapts the booking flow to individual patient history.
- Developed the **patient flow prediction** model used by the schedule optimizer.
- Engineered the full **ML pipeline**: dataset preparation, feature engineering, training, validation, and inference deployment.
- Integrated the inference layer with the backend API via asynchronous endpoints.

### Security Track

Took on the additional responsibility of designing the system's security architecture. See the next section for detail.

---

## Security Implementation

Given that IMed Helix processes sensitive medical data, security was treated as a first-class architectural concern. As the security engineer, I implemented:

- **Patient data encryption** — at rest (AES-256) and in transit (TLS 1.3).
- **QR-code authentication** — short-lived signed tokens with session-bound nonces to prevent replay attacks.
- **Input validation & sanitization** — strict schema validation on every API endpoint to mitigate injection vectors.
- **Role-Based Access Control (RBAC)** — separate permission tiers for patients, medical staff, and administrators.
- **Rate limiting** — adaptive throttling on authentication and booking endpoints to mitigate brute-force and abuse.
- **Secure API design** — JWT-based session management, CSRF protections, and full security header coverage (CSP, HSTS, X-Frame-Options).
- **HIPAA-aligned data handling** — minimal data retention, audit logging of all access to patient records, and a clear data lifecycle policy.
- **Local-first architecture** — sensitive data never leaves the clinic's local network unless explicitly authorized.

---

## Technology Stack

| Layer | Technologies |
|-------|--------------|
| **Language** | Python 3.11+ |
| **Backend** | FastAPI, asyncio, WebSocket |
| **AI / ML** | PyTorch, scikit-learn, pandas, NumPy |
| **Frontend (Kiosk UI)** | React, TypeScript |
| **Database** | PostgreSQL (clinic data), SQLite (kiosk-local cache) |
| **Authentication** | JWT, signed QR tokens |
| **Deployment** | Docker, on-premise local servers |
| **Integration** | REST API, HL7/FHIR-compatible adapters for MIS |

---

## Team

| Member | Role | Responsibilities |
|--------|------|------------------|
| **Polina Goglacheva** | Project Manager | Team coordination and project execution |
| **Saveliy Golubev** | Neural Network Developer & Security Engineer | AI models, ML pipeline, system security |
| **Lavr Albychev** | Backend Developer | Server-side architecture, API, data persistence |
| **Eva Sklyarenko** | UI/UX Designer | Kiosk interface, user-experience design |
| **Sofya Sokolova** | Data Analyst | Data collection, processing, and market research |

---

## Project Context

- **Institution:** Tyumen Industrial University (Тюменский индустриальный университет, ТИУ)
- **Course:** ПР7 — Programming in Python
- **Project type:** Research & Development (R&D)
- **Year:** 2025
- **Format:** Cross-functional team of five
- **Outcome:** Working prototype, full project documentation, market analysis, and presentation to the academic review board.

---

## Note on Source Code

The full source code of IMed Helix is the **intellectual property of Tyumen Industrial University** and is therefore not published in this repository. This repository serves as a **public technical showcase and portfolio document** describing the project's goals, architecture, methodology, and the author's individual contribution.

For inquiries regarding access to source materials, please contact the university directly.

---

*Maintained by [@NovaCode37](https://github.com/NovaCode37) — Saveliy Golubev.*
