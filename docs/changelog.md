# Changelog

All notable changes to the **ACR Engineering Documentation** and associated architecture specifications are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2026-10-10

### Added
* **Documentation Core:** Official launch of the centralized **ACR Engineering Documentation** GitBook portal.
* **Architecture Specifications:** Comprehensive system blueprints, sequence diagrams, and client/server data flow topologies.
* **Technology Stack Audit:** Detailed documentation and best practice guidelines for Next.js (App Router), TypeScript, Tailwind CSS, Framer Motion, and Three.js/WebGL.
* **Design System Guide:** Complete specification for ACR design tokens, dark-mode obsidian palettes, glassmorphism standards, and copy-paste component primitives (`Button`, `GlassCard`).
* **API Specification:** RESTful endpoint catalog (`GET /health`, `GET /projects`, `POST /contact`, `POST /admin/revalidate`) with JSON schema contracts and error handling conventions.
* **Authentication Standards:** Dual-tier auth pattern documentation covering API keys (`X-API-Key`) and session JWTs with Role-Based Access Control (RBAC).
* **Developer Workflows:** End-to-end setup instructions, fail-fast Zod environment validation, and deployment recipes for Vercel and Docker.
* **Project Showcase & RFC Template:** Catalogued flagship applications (`adicahyadir.dev`, ACR Design System, Enigma AI Studio) and created a standard engineering RFC template for new projects.

---

## Planned for [1.1.0]
* Interactive component playground with live code previews directly inside GitBook.
* OpenAPI / Swagger 3.1 automated generation from route handlers.
* Multi-language documentation support (English & Indonesian).
