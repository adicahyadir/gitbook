---
description: Comprehensive catalogue of flagship projects, interactive applications, and engineering experiments.
---

# Project Showcase & Ecosystem

The following catalogue documents the core applications and production systems engineered by **Adi Cahyadi Ramadhan (EnigmaAura)**.

---

## 🌟 1. adicahyadir.dev (Flagship Digital Garden & Portfolio)

### Overview
* **Purpose:** The primary personal engineering portal and interactive showcase for Adi Cahyadi Ramadhan.
* **Problem Solved:** Traditional developer portfolios are static and passive. This platform showcases real-time WebGL graphics, live performance telemetry, and interactive case studies.
* **Target Users:** Engineering leaders, tech recruiters, creative directors, and developer communities.

### Technology Stack
* **Frontend:** Next.js (App Router), TypeScript, React 19
* **Styling & Motion:** Tailwind CSS, Framer Motion, Three.js, React Three Fiber (R3F)
* **Backend:** Next.js Route Handlers, Edge Middleware
* **Database & Cache:** Supabase (PostgreSQL), Upstash Redis
* **Infrastructure:** Vercel Edge Network, Cloudflare DNS, Cloudinary CDN

### Key Highlights
* 98+ Google Lighthouse Performance score despite dynamic 3D WebGL scenes.
* Native Dark Mode with custom glassmorphism shaders.
* Zero client-side re-render cascades using Zustand and modular Server Components.

---

## 🎨 2. ACR Design System

### Overview
* **Purpose:** A unified, accessible component library built to power all ACR applications with visual consistency and predictable keyboard ergonomics.
* **Problem Solved:** Eliminates fragmented UI code, inconsistent spacing, and accessibility gaps across disparate repositories.
* **Target Users:** Internal engineering projects and open-source contributors.

### Technology Stack
* **Primitives:** Radix UI Unstyled Primitives
* **Styling:** Tailwind CSS with CSS Variables design tokens
* **Icons:** Lucide React
* **Type Safety:** TypeScript with strict props contracts

---

## 🤖 3. Enigma AI Studio (Agentic Workspace)

### Overview
* **Purpose:** A developer interface for orchestrating multi-agent LLM workflows, streaming markdown outputs, and testing custom system prompts.
* **Problem Solved:** Solves the friction of testing tool-calling LLMs and prompt chaining in a standard chat UI.
* **Target Users:** AI engineers, prompt researchers, and power users.

### Technology Stack
* **Frontend:** Next.js, Tailwind CSS, Monaco Editor
* **AI Engine:** Vercel AI SDK, OpenAI API, Google Gemini API
* **Persistence:** PostgreSQL with pgvector for semantic retrieval

---

## 🌌 4. Creative WebGL & Shader Lab

### Overview
* **Purpose:** An experimental sandbox exploring fragment shaders, particle physics, audio-reactive visualizers, and mathematical generative art.
* **Problem Solved:** Pushes the boundaries of browser graphics and translates computational art into production web hero sections.
* **Target Users:** Creative developers, generative art enthusiasts.

### Technology Stack
* **Core:** Three.js, GLSL (OpenGL Shading Language), Web Audio API
* **Framework:** React Three Fiber, Drei

---

## 📖 5. ACR GitBook Knowledge Base (This Repository)

### Overview
* **Purpose:** Centralized Single Source of Truth (SSOT) developer handbook and technical documentation for all ACR projects.
* **Problem Solved:** Prevents tribal knowledge loss and provides standardized architectural documentation for all repositories.
* **Target Users:** Software engineers, collaborators, open-source maintainers.
