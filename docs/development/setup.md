---
description: Comprehensive step-by-step developer workstation setup, dependencies, scripts, and debugging tools.
---

# Local Development Setup

This guide walks you through preparing your local development environment to contribute to or run applications within the **ACR Ecosystem**.

---

## 💻 1. Prerequisites

Before cloning and running any project, ensure your environment meets the minimum software specifications:

| Dependency | Minimum Version | Recommended | Notes |
| :--- | :--- | :--- | :--- |
| **Node.js** | `>= 18.18.0` | `20.x LTS` | JavaScript runtime engine. |
| **Package Manager** | `npm 9.x` | `pnpm 9.x` | Faster installations and strict dependency graphs. |
| **Git** | `>= 2.38.0` | Latest | Version control with SSH or GPG signing. |
| **Operating System** | Windows 11 / macOS / Linux | Any | WSL2 recommended for Windows users when using Docker. |

Verify installed versions in your terminal:

```bash
node -v
npm -v
git --version
```

---

## 📥 2. Repository Cloning & Dependency Installation

Clone the target repository via HTTPS or SSH:

```bash
# Clone repository
git clone https://github.com/adicahyadir/gitbook.git

# Navigate into workspace
cd gitbook

# Install pinned dependencies
npm install
```

---

## ⚙️ 3. npm Scripts & Command Registry

Standardized scripts available in all ACR repositories:

```bash
# Start local development server with Fast Refresh (default: http://localhost:3000)
npm run dev

# Compile TypeScript and generate production distribution bundle
npm run build

# Run local production server against the compiled bundle
npm run start

# Execute ESLint static analysis and code style checks
npm run lint

# Validate type integrity across all TypeScript files
npm run typecheck

# Format code with Prettier
npm run format

# Execute unit and component test suites (Vitest / Jest)
npm run test
```

---

## 🔍 4. Recommended IDE Extensions (VS Code / Cursor)

To ensure consistency with team engineering standards, the following extensions are strongly recommended:

* **Tailwind CSS IntelliSense** (`bradlc.vscode-tailwindcss`) - Autocompletion and class linting.
* **ESLint** (`dbaeumer.vscode-eslint`) - In-editor error highlights.
* **Prettier - Code Formatter** (`esbenp.prettier-vscode`) - Format on save.
* **Pretty TypeScript Errors** (`yoavbls.pretty-ts-errors`) - Human-readable TypeScript compiler tooltips.

### Editor Settings (`.vscode/settings.json`)

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "typescript.tsdk": "node_modules/typescript/lib"
}
```

---

## 🐛 5. Debugging Workflows

### Debugging in VS Code / Cursor
To launch a Node.js / Next.js debugger session, add the following configuration to `.vscode/launch.json`:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Next.js: debug server-side",
      "type": "node-terminal",
      "request": "launch",
      "command": "npm run dev"
    }
  ]
}
```
Set breakpoints directly in your server components or route handlers and inspect execution states in real-time.
