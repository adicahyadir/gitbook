---
description: Deployment strategies, platform recipes (Vercel, Docker, VPS), and production pre-flight checklists.
---

# Deployment Guide

This guide details the deployment pipeline for **ACR Ecosystem** web applications and technical portals.

---

## 🚀 1. Primary Deployment: Vercel (Edge Network)

The default hosting platform for ACR Next.js applications is **Vercel**, providing zero-configuration edge middleware, instant preview environments, and global static edge caching.

### Step-by-Step Vercel Deployment

1. **Connect Repository:** Link your GitHub repository in the Vercel Dashboard.
2. **Framework Preset:** Vercel automatically detects `Next.js`.
3. **Configure Environment Variables:** Add all variables defined in `docs/development/environment.md` into the Vercel Project Settings (`Production`, `Preview`, `Development`).
4. **Build & Output Settings:**
   * **Build Command:** `npm run build`
   * **Output Directory:** `.next`
   * **Install Command:** `npm install`
5. **Deploy:** Click **Deploy**. Each Git push to `main` automatically triggers an atomic production deployment.

---

## 🐳 2. Containerized Deployment: Docker

For self-hosted virtual private servers (VPS), AWS ECS, or Kubernetes, applications can be packaged using a multi-stage Docker build utilizing Next.js standalone mode.

### Production `Dockerfile`

```dockerfile
# ------------------------------------------------------------------------------
# Stage 1: Dependency Installation
# ------------------------------------------------------------------------------
FROM node:20-alpine AS deps
RUN apk add --no-cache libc6-compat
WORKDIR /app
COPY package.json package-lock.json* ./
RUN npm ci

# ------------------------------------------------------------------------------
# Stage 2: Application Build
# ------------------------------------------------------------------------------
FROM node:20-alpine AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
ENV NEXT_TELEMETRY_DISABLED=1
ENV NODE_ENV=production
RUN npm run build

# ------------------------------------------------------------------------------
# Stage 3: Minimal Production Runner
# ------------------------------------------------------------------------------
FROM node:20-alpine AS runner
WORKDIR /app

ENV NODE_ENV=production
ENV NEXT_TELEMETRY_DISABLED=1
ENV PORT=3000
ENV HOSTNAME="0.0.0.0"

RUN addgroup --system --gid 1001 nodejs
RUN adduser --system --uid 1001 nextjs

# Copy standalone runtime output
COPY --from=builder /app/public ./public
COPY --from=builder --chown=nextjs:nodejs /app/.next/standalone ./
COPY --from=builder --chown=nextjs:nodejs /app/.next/static ./.next/static

USER nextjs
EXPOSE 3000

CMD ["node", "server.js"]
```

### Building & Running Container

```bash
# Build the Docker image
docker build -t acr-app:latest .

# Run container with injected environment secrets
docker run -p 3000:3000 --env-file .env.production acr-app:latest
```

---

## 📋 3. Production Pre-Flight Checklist

Before cutting a production release, the following checklist must be satisfied:

* [ ] **Type Integrity:** `npm run typecheck` passes with zero errors.
* [ ] **Linter Quality:** `npm run lint` reports zero warnings or errors.
* [ ] **Environment Validation:** `src/env.ts` parses all production credentials successfully.
* [ ] **Security Headers:** HTTP headers include `Content-Security-Policy`, `X-Frame-Options: DENY`, and `X-Content-Type-Options: nosniff`.
* [ ] **Performance Audit:** Google Lighthouse performance score exceeds 95 on mobile and desktop.
* [ ] **Bundle Analysis:** No duplicate packages or client-side leakage of server-only modules.
* [ ] **Error Monitoring:** Sentry or equivalent logging agent initialized with current release version tag.
* [ ] **Robots & Sitemap:** `robots.txt` and `sitemap.xml` correctly route search engine crawlers.
