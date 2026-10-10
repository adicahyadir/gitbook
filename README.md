# ACR Engineering Documentation

<p align="center">
  <strong>Technical Knowledge Base by Adi Cahyadi Ramadhan (EnigmaAura)</strong>
</p>

<p align="center">
  <em>Frontend Engineer • UI/UX Designer • Creative Developer</em>
</p>

<p align="center">
  <a href="https://adicahyadir-portfolio.vercel.app/"><img src="https://img.shields.io/badge/Live%20Portfolio-adicahyadir--portfolio.vercel.app-000000?style=flat-square&logo=vercel" alt="Live Portfolio" /></a>
  <a href="https://adicahyadir.dev"><img src="https://img.shields.io/badge/Domain-adicahyadir.dev-0969da?style=flat-square" alt="Domain" /></a>
  <a href="docs/README.md"><img src="https://img.shields.io/badge/GitBook-Documentation-blueviolet?style=flat-square" alt="GitBook" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License" /></a>
  <img src="https://img.shields.io/badge/Architecture-Clean%20%26%20Modular-informational?style=flat-square" alt="Architecture" />
</p>

---

## 🧭 Overview

Welcome to the **ACR Engineering Documentation Portal**. This repository serves as the official developer documentation and engineering handbook for all projects, applications, UI/UX design tokens, micro-experiments, and system architecture blueprints developed by **Adi Cahyadi Ramadhan** (alias **EnigmaAura**).

Designed in full compliance with **GitBook**, this repository structures technical knowledge using industry-grade documentation standards inspired by **Vercel Docs**, **Next.js**, **Stripe API**, and **Linear Engineering**.

> **Engineering Principle:**  
> *"Fast • Beautiful • Functional • User-Centered"*

---

## 📚 Documentation Structure

```text
docs/
├── README.md              # Landing Documentation & Quick Navigator
├── introduction.md        # About EnigmaAura / ACR & Engineering Philosophy
├── tech-stack.md          # Technology Stack, Frameworks & Best Practices
├── architecture.md        # System Architecture & Clean Component Flow
├── api/
│   ├── overview.md        # API Architecture, Protocols & Standards
│   ├── authentication.md  # Auth Patterns, JWT, OAuth & RBAC
│   └── endpoints.md       # Standardized Endpoints & Request/Response Contracts
├── projects/
│   ├── project-list.md    # Showcase of ACR Ecosystem Projects & Repos
│   └── project-template.md# Engineering RFC & Production Project Template
├── components/
│   └── design-system.md   # ACR Design System, Tokens, Typography & Reusable Components
├── development/
│   ├── setup.md           # Local Prerequisites & Installation Guide
│   ├── environment.md     # Secrets, .env Schema & Zod Validation
│   └── deployment.md      # CI/CD Workflows, Vercel & Production Checklist
└── changelog.md           # Version Release History & Milestones
```

---

## ⚡ Quick Navigation

| Section | Description | Link |
| :--- | :--- | :--- |
| **Introduction** | Background, engineering philosophy, and creative developer mindset. | [Read Introduction](docs/introduction.md) |
| **Tech Stack** | Deep dive into React, Next.js, TypeScript, Tailwind CSS, Three.js, and Framer Motion. | [Explore Stack](docs/tech-stack.md) |
| **Architecture** | Component lifecycle, state topology, data-flow diagrams with Mermaid. | [Inspect Architecture](docs/architecture.md) |
| **API Reference** | Specifications, authentication workflows, and REST/RPC endpoints. | [API Docs](docs/api/overview.md) |
| **Design System** | Neon dark-mode palette, glassmorphism tokens, and responsive UI components. | [Design System](docs/components/design-system.md) |
| **Development** | Setup commands, environment secrets, and deployment recipes. | [Dev Guide](docs/development/setup.md) |

---

## 🛠️ Local Development & Preview

To preview this documentation locally using GitBook CLI or a markdown live server:

### Prerequisites

- [Node.js](https://nodejs.org/) (>= 18.x)
- npm or pnpm

### Running with GitBook or Markdown Viewer

```bash
# Clone the repository
git clone https://github.com/adicahyadir/gitbook.git
cd gitbook

# Option A: Preview via GitBook CLI (if installed globally)
npx gitbook-cli serve

# Option B: Run a local markdown live server
npx docsify-cli serve docs
```

---

## 👤 Author & Connect

- **Engineer:** Adi Cahyadi Ramadhan
- **Alias:** EnigmaAura
- **Brand:** ACR • `adicahyadir.dev`
- **GitHub:** [@adicahyadir](https://github.com/adicahyadir)
- **Role:** Frontend Engineer • UI/UX Designer • Creative Developer

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for full details.
