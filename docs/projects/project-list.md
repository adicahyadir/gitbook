---
description: Catalogue of ACR Engineering portfolio projects — verified from source repositories.
---

# Project Showcase & Ecosystem

The following catalogue documents the engineering artifacts, web applications, and architectural solutions built by **Adi Cahyadi Ramadhan, S.T. (EnigmaAura)**. 

Live visual previews and interactive walkthroughs are accessible via the official portfolio:  
👉 **[adicahyadir-portfolio.vercel.app](https://adicahyadir-portfolio.vercel.app/)**

---

## 🧭 Showcase Index

| Project Name | Classification | Stack Focus | Timeline | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Absensi App** | Web App / GovTech System | NestJS, React, PostgreSQL, Tailwind CSS 4 | 2025 | `Completed` |
| **App Letter C** | Web App / GovTech / GIS | Laravel 12, MySQL, Google Workspace API, DDD | 2025 | `Completed` |
| **CBT Desa** | Full Stack / Exam System | Node.js (Fastify), React, MySQL, Zod | 2025 | `Completed` |
| **Temen Musik** | Web App / Marketplace | Laravel 12, React 19, Vite, Midtrans, AWS S3 | 2025 | `Completed` |
| **Sistem Informasi Kependudukan** | Web App / GovTech Admin | React 19, TypeScript, Fastify 5, MySQL 8 | 2025 | `Completed` |
| **Portfolio Evan** | Personal Portfolio | React 19, TypeScript, Vite 8, Firebase Auth | 2025 | `Completed` |
| **Perpus** | Web App / Library Management | CodeIgniter 3, PHP 8.1+, MySQL 8 | 2025 | `Completed` |
| **Carita Cerita** | Front End / Media Experience | React 19, TypeScript, Vite 6, @google/genai | 2025 | `Completed` |
| **Enigma Villa** | Creative Web / Hospitality | React 19, TypeScript, Tailwind CSS 4, Framer Motion | 2025 | `Completed` |

---

## 📦 1. Absensi App

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_absensi_1779341457906.png" alt="Absensi App" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Enterprise attendance system for village officials and organizational personnel.
* **Category:** Web App / GovTech System.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Replaces obsolete manual sign-in books with a tamper-resistant digital attendance system for village office officials and organizational personnel.

### Technical Architecture
* **Architecture:** Full-stack NestJS monorepo with React frontend and PostgreSQL database.
* **Authentication:** JWT-based authentication with role-based access control.
* **Real-time Features:** WebSocket integration for live attendance status.
* **Reporting:** Automated attendance reports with export capabilities.

---

## 🏛️ 2. App Letter C

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_appletter_1779341457906.png" alt="App Letter C" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Village land registration and official letter generation system.
* **Category:** Web App / GovTech / GIS.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Digitizes village land registration processes and official letter generation with spatial data support.

### Technical Architecture
* **Architecture:** Laravel 12 application with MySQL database and GIS polygon support.
* **Spatial Features:** Uses `matanyadaev/laravel-eloquent-spatial` for geographic data handling.
* **API Integration:** Google Workspace API for official document workflows.
* **Real-time Features:** Pusher PHP server for real-time updates.

---

## 🎓 3. CBT Desa

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_cbt_1779341457906.png" alt="CBT Desa" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Computer-based testing for village apparatus recruitment examinations.
* **Category:** Full Stack / Exam System.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Eliminates manual paper examination bias and delays in official village apparatus hiring tests through a secure, computerized assessment test (CAT-style) with live scoring.

### Technical Architecture
* **Architecture:** Node.js (Fastify 5) backend with React frontend and MySQL 8 database.
* **Integrity Features:** Browser tab switch monitoring, anti-cheat detection, randomized question pools.
* **Reporting:** Instant export of official test result sheets (PDF/CSV) with cryptographic validation.
* **Real-time Features:** Live scoring and progress monitoring.

---

## ☕ 4. Temen Musik

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_musik_1779341457906.png" alt="Temen Musik" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Music marketplace for buying, selling, and streaming music tracks.
* **Category:** Web App / Marketplace.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Provides a platform for musicians and listeners to connect with secure payment processing and digital delivery.

### Technical Architecture
* **Architecture:** Laravel 12.61.1 with React 19 + Vite 8 frontend.
* **Payment Processing:** Midtrans PHP SDK 2.6 for secure payment processing.
* **Storage:** AWS S3 integration for music file storage and delivery.
* **Authentication:** Laravel Sanctum for API authentication, Socialite for social login.

---

## 👥 5. Sistem Informasi Kependudukan

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_kependudukan_1779341457906.png" alt="Sistem Informasi Kependudukan" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Village population administration and demographic data management.
* **Category:** Web App / GovTech Admin.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Centralizes village population data management for administrative purposes, including resident registration, population reporting, and demographic analysis.

### Technical Architecture
* **Architecture:** React 19 + TypeScript frontend with Fastify 5 backend and MySQL 8 database.
* **Validation:** Zod for request validation, Argon2 for password hashing.
* **Data Import/Export:** ExcelJS for bulk import/export of population data.
* **API Routing:** VITE_API_BASE_URL=/api/v1 for API configuration.

---

## 📘 6. Portfolio Evan

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_evan_1779341457906.png" alt="Portfolio Evan" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Personal portfolio website for Evan showcasing projects and skills.
* **Category:** Personal Portfolio.
* **Timeline:** 2025 • **Status:** `Completed`
* **Purpose:** Professional portfolio presentation with project showcase, about section, and contact information.

### Technical Architecture
* **Architecture:** React 19 + TypeScript + Vite 8 + Tailwind CSS 4.
* **Authentication:** Firebase Authentication with custom claims and TOTP 2FA.
* **State Management:** Redux Toolkit for client state.
* **Data Visualization:** Recharts for project metrics and statistics.
* **Emulator Mode:** Local testing without production Firebase credentials via `npm run firebase:emulator:start`.
* **Admin Provisioning:** `npm run firebase:grant-admin` for admin claim provisioning.

---

## 📚 7. Perpus

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_perpus_1779341457906.png" alt="Perpus" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** School library management system for catalog, borrowing, returns, fines, and reporting.
* **Category:** Web App / Library Management.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Modernizes school library operations with digital catalog, circulation management, and comprehensive reporting.

### Technical Architecture
* **Architecture:** CodeIgniter 3 with PHP 8.1/8.2+ and MySQL 8/MariaDB 10.3+.
* **Authentication:** Multi-role authentication with different permission levels.
* **Barcode Generation:** CODE128 format with BRC prefix and cryptographic random values.
* **PDF Generation:** Dompdf for report generation.
* **Reporting:** Monthly/yearly circulation reports, member reports by class.

---

## 📖 8. Carita Cerita

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_cerita_1779341457906.png" alt="Carita Cerita" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Digital platform for preserving and sharing local community stories.
* **Category:** Front End / Media Experience.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Transforming long-form narratives and cultural stories into an immersive, reader-friendly digital experience that encourages user retention.

### Technical Architecture
* **Architecture:** React 19 + TypeScript + Vite 6 frontend with native PHP backend.
* **AI Integration:** @google/genai for Generative AI features.
* **Storage:** Firebase Firestore optional (ready to activate), localStorage fallback for development.
* **Backend:** PHP native (no framework) with PDO for database abstraction.

---

## 🏛️ 9. Enigma Villa

<p align="center">
  <img src="https://emiozfkxrasjzwhkulwb.supabase.co/storage/v1/object/public/uploads/img_0xwsx9y_1779250660179.png" alt="Enigma Villa" width="85%" style="border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);" />
</p>

### Overview
* **Domain:** Luxury Hospitality, Villa Booking & Architectural Presentation.
* **Category:** Creative Web / Template.
* **Timeline:** 2025 • **Status:** `Completed`
* **Problem Solved:** Luxury hospitality demands evocative visual storytelling combined with accurate availability booking. Enigma Villa bridges high-end architectural aesthetics with a fluid booking flow.

### Technical Architecture
* **Frontend:** React 19, TypeScript, Tailwind CSS 4.
* **Visuals & Motion:** Framer Motion 12, GSAP 3.15, @studio-freight/lenis for smooth scrolling.
* **Form Logic:** Interactive date picker with calendar conflict detection.
* **Charts:** Recharts 3.8.1 for data visualization.

---

## 🔒 Private Client Engagements (Confidentiality & NDA)

> [!IMPORTANT]
> **Client Privacy & Intellectual Property Notice:**  
> A substantial portion of engineering systems developed by Adi Cahyadi Ramadhan are **proprietary enterprise applications and custom government back-offices** created under strict **Non-Disclosure Agreements (NDA)**.

These private engagements include:
1. **Operator SIKS-NG Support Modules & Institutional Data Tools:** Internal automation, verification workflows, and demographic welfare analytics.
2. **Enterprise Administration Portals:** Custom multi-tenant dashboards, accounting back-offices, and inventory synchronization services.
3. **Internal Microservices & Business Automations:** Private webhook workers, data ETL bridges, and restricted-access client infrastructure.

In compliance with professional ethics, source code, database architectures, client credentials, and proprietary workflows for these private systems remain strictly confidential and will not be published in public repositories.
