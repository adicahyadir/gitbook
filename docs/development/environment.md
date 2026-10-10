---
description: Environment configuration, secret handling, security boundaries, and schema validation with Zod.
---

# Environment Configuration

## 🔐 Configuration Philosophy

Applications across the **ACR Ecosystem** decouple configuration from source code. Secrets and environment variables are:
1. **Never committed** to version control (`.gitignore` enforces ignoring `.env*` except `.env.example`).
2. **Strictly validated at startup** using **Zod** schema schemas to prevent runtime `undefined` crashes.
3. **Partitioned** into server-only variables and client-exposed variables (`NEXT_PUBLIC_*`).

---

## 📄 Standard `.env.example`

Create a `.env.local` file in your project root by copying the template:

```bash
cp .env.example .env.local
```

```ini
# ==============================================================================
# ACR Application Environment Template
# ==============================================================================

# Node Runtime Environment (development | test | production)
NODE_ENV=development

# Canonical Application Origin
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Public API Gateway Base URL
NEXT_PUBLIC_API_URL=http://localhost:3000/api

# ------------------------------------------------------------------------------
# Database & Persistence (Server Only)
# ------------------------------------------------------------------------------
DATABASE_URL=postgresql://postgres:password@localhost:5432/acr_db?schema=public
DIRECT_URL=postgresql://postgres:password@localhost:5432/acr_db?schema=public

# ------------------------------------------------------------------------------
# Authentication & Encryption (Server Only)
# ------------------------------------------------------------------------------
AUTH_SECRET=generate_with_openssl_rand_base64_32
NEXTAUTH_URL=http://localhost:3000

# ------------------------------------------------------------------------------
# Rate Limiting & Distributed Cache (Server Only)
# ------------------------------------------------------------------------------
UPSTASH_REDIS_REST_URL=https://your-upstash-instance.upstash.io
UPSTASH_REDIS_REST_TOKEN=your_upstash_token_here

# ------------------------------------------------------------------------------
# AI & Third-Party APIs (Server Only)
# ------------------------------------------------------------------------------
OPENAI_API_KEY=sk-proj-...
GEMINI_API_KEY=AIzaSy...
```

---

## 🔍 Variable Definition & Purpose

| Variable Name | Exposure | Required | Purpose & Format |
| :--- | :--- | :--- | :--- |
| `NODE_ENV` | Server | Yes | Specifies execution mode (`development`, `production`). |
| `NEXT_PUBLIC_APP_URL` | Client/Server | Yes | Absolute base URL for metadata, SEO canonical tags, and OpenGraph images. |
| `NEXT_PUBLIC_API_URL` | Client/Server | No | API endpoint prefix used by client components. |
| `DATABASE_URL` | Server Only | Yes | Pooled PostgreSQL connection string for Prisma/Drizzle. |
| `AUTH_SECRET` | Server Only | Yes | 32-byte cryptographic secret used to sign session cookies. |
| `UPSTASH_REDIS_REST_URL` | Server Only | Conditional | REST endpoint for low-latency Edge cache and rate limiters. |
| `OPENAI_API_KEY` | Server Only | Optional | Bearer token for LLM inference requests. |

---

## 🛡️ Fail-Fast Schema Validation (Zod)

To guarantee that no application builds or runs with missing or malformed keys, every ACR project uses a type-safe environment parser:

```typescript
// src/env.ts - Type-safe environment validation
import { z } from 'zod';

const envSchema = z.object({
  // Server-side environment variables
  NODE_ENV: z.enum(['development', 'test', 'production']).default('development'),
  DATABASE_URL: z.string().url('DATABASE_URL must be a valid PostgreSQL connection string'),
  AUTH_SECRET: z.string().min(32, 'AUTH_SECRET must be at least 32 characters long'),
  UPSTASH_REDIS_REST_URL: z.string().url().optional(),
  UPSTASH_REDIS_REST_TOKEN: z.string().optional(),
  OPENAI_API_KEY: z.string().startsWith('sk-').optional(),

  // Client-exposed variables (Prefixed with NEXT_PUBLIC_)
  NEXT_PUBLIC_APP_URL: z.string().url().default('http://localhost:3000'),
  NEXT_PUBLIC_API_URL: z.string().default('/api'),
});

const parsed = envSchema.safeParse(process.env);

if (!parsed.success) {
  console.error('❌ Invalid environment variables detected:');
  console.error(parsed.error.flatten().fieldErrors);
  throw new Error('Invalid environment variables. Check terminal output above.');
}

export const env = parsed.data;
```

With this validation in place, importing `env` guarantees 100% type safety and autocompletion anywhere in the project.
