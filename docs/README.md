---
description: Welcome to the official ACR Engineering Documentation & Technical Knowledge Base.
---

# ACR Engineering Documentation

> **Official Technical Knowledge Base & Handbook**  
> Engineered by **Adi Cahyadi Ramadhan (EnigmaAura)**  
> *Frontend Engineer • UI/UX Designer • Creative Developer*

---

## 🚀 Welcome to the Portal

The **ACR Engineering Documentation** portal is the centralized single source of truth (SSOT) for all digital products, open-source software, design systems, and experimental applications built across the **ACR** ecosystem (`adicahyadir.dev`).

This documentation is crafted for software engineers, designers, and collaborators looking for deep technical clarity, predictable development workflows, and architectural standards.

```
┌────────────────────────────────────────────────────────────────────────┐
│                                                                        │
│   A C R   E N G I N E E R I N G   H A N D B O O K                      │
│   "Fast • Beautiful • Functional • User-Centered"                      │
│                                                                        │
│   • Frontend Engineering   • UI/UX Systems    • Creative WebGL/3D      │
│   • Modern Architecture    • API Standards    • Developer Experience   │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 🎯 Engineering Philosophy

Every solution, whether a lightweight component or an end-to-end distributed system, is guided by four immutable pillars:

1. **Fast (Performance First):** Sub-second Time to Interactive (TTI), optimized bundle splitting, server-driven rendering where sensible, and 60fps+ fluid micro-interactions.
2. **Beautiful (Visual Excellence):** Elevated aesthetic standards. No bare-bones MVPs; we leverage curated dark palettes, subtle glassmorphism, refined typography, and purposeful motion.
3. **Functional (Robust Engineering):** Strict type safety with TypeScript, clean separation of concerns, comprehensive error boundaries, and defensive input validation.
4. **User-Centered (Human Experience):** Empathy in design. Keyboard accessibility (WCAG AA compliant), clear state feedback, optimistic UI updates, and zero jarring layout shifts (CLS < 0.1).

---

## 🔍 Core Specializations

* **Frontend Engineering:** Enterprise-grade single page & server-rendered applications utilizing React, Next.js (App Router), Vue, and modern state architectures.
* **UI/UX Engineering & Design Systems:** Token-based component libraries, atomic design methodology, accessible primitives (Radix UI / Headless UI), and fluid responsive layouts.
* **Creative Web & Motion:** Immersive visual storytelling via Three.js, React Three Fiber, GLSL shaders, Framer Motion, and GSAP.
* **AI-Powered Applications:** Seamless integration of LLM endpoints, vector embeddings, streaming interfaces, and developer tool augmentations.
* **Developer Experience (DX):** Streamlined scaffolding, strict linting rules, automated CI/CD pipelines, and clear self-documenting codebases.

---

## 🧭 Documentation Map

Explore the sections of the technical handbook below:

### 1. [Introduction & Background](introduction.md)
Discover the biography, career trajectory, core values, and creative developer mindset behind **Adi Cahyadi Ramadhan**.

### 2. [Technology Stack](tech-stack.md)
Comprehensive technical audit of chosen frameworks, languages, CSS architectures, state management patterns, and utility libraries.

### 3. [System Architecture](architecture.md)
High-level system topology, clean frontend boundaries, data flow pipelines, caching strategies, and Mermaid architectural diagrams.

### 4. [API Specification](api/overview.md)
API conventions, response schemas, error protocols, authentication schemes (JWT/OAuth), and endpoint contracts.

### 5. [Projects & Ecosystem](projects/project-list.md)
Detailed architectural and implementation breakdowns of key applications and open-source experiments.

### 6. [ACR Design System](components/design-system.md)
Color tokens, typography scale, elevation, glassmorphism rules, and copy-paste component specifications.

### 7. [Development Workflow](development/setup.md)
Step-by-step local machine configuration, package managers, testing baselines, and Vercel/Docker deployment checklists.

---

## ⚡ Quick Start Command Cheat Sheet

```bash
# Clone an ACR repository
git clone https://github.com/adicahyadir/<project-name>.git

# Navigate into project directory
cd <project-name>

# Install pinned dependencies
npm install --frozen-lockfile

# Configure local secrets
cp .env.example .env.local

# Launch the hot-reloading development server
npm run dev
```

For detailed setup instructions, please visit the [Local Setup Guide](development/setup.md).
