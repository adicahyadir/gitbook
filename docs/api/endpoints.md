---
description: Full endpoint reference, query parameters, request payloads, and response contracts.
---

# Endpoints Reference

All endpoints documented below are relative to `https://api.adicahyadir.dev/v1`.

---

## 🟢 1. Health Check

```http
GET /health
```

Verifies the operational status of the API runtime, Edge CDN, and database connection.

* **Authentication:** None (Public)
* **Rate Limit:** 120 req/min

### Response `200 OK`

```json
{
  "status": "success",
  "data": {
    "service": "acr-api-gateway",
    "uptimeSeconds": 142850,
    "database": "healthy",
    "region": "sin1",
    "timestamp": "2026-10-10T05:35:00Z"
  }
}
```

---

## 📂 2. List Projects

```http
GET /projects
```

Retrieves a paginated list of published engineering projects, creative experiments, and design system components.

* **Authentication:** None (Public)
* **Rate Limit:** 60 req/min

### Query Parameters

| Parameter | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `page` | `integer` | No | `1` | Page number for pagination. |
| `limit` | `integer` | No | `10` | Records per page (Max: `50`). |
| `category`| `string` | No | `all` | Filter by category (`creative-web`, `enterprise-dashboard`, `ai-interface`). |
| `sort` | `string` | No | `desc` | Sort ordering by publication date (`asc`, `desc`). |

### Response `200 OK`

```json
{
  "status": "success",
  "data": [
    {
      "id": "proj_01",
      "slug": "asmodarkness-apparel",
      "title": "E-Commerce ASMODARKNESS™ APPAREL",
      "category": "template",
      "tagline": "Modern High-Performance Streetwear & Apparel E-Commerce",
      "technologies": ["Next.js", "TypeScript", "Tailwind CSS", "Framer Motion"],
      "liveUrl": "https://adicahyadir-portfolio.vercel.app/",
      "githubUrl": "https://github.com/adicahyadir",
      "featured": true,
      "status": "completed",
      "year": 2026
    },
    {
      "id": "proj_02",
      "slug": "cbt-desa",
      "title": "CBT DESA — Computer Based Test (CAT Style)",
      "category": "full-stack",
      "tagline": "Computer-Based Civil Service & Official Assessment Platform",
      "technologies": ["Node.js", "React", "PostgreSQL", "Tailwind CSS"],
      "liveUrl": "https://adicahyadir-portfolio.vercel.app/",
      "githubUrl": "https://github.com/adicahyadir",
      "featured": true,
      "status": "completed",
      "year": 2025
    }
  ],
  "meta": {
    "page": 1,
    "limit": 10,
    "totalRecords": 7,
    "totalPages": 1
  }
}
```

---

## 🔍 3. Get Project by ID or Slug

```http
GET /projects/:identifier
```

Fetches the complete specification, architecture notes, and metadata for a specific project.

* **Authentication:** None (Public)
* **Path Parameters:**
  * `:identifier` (`string`, required): The project UUID or unique slug (e.g. `asmodarkness-apparel`).

### Response `200 OK`

```json
{
  "status": "success",
  "data": {
    "id": "proj_01",
    "slug": "asmodarkness-apparel",
    "title": "E-Commerce ASMODARKNESS™ APPAREL",
    "category": "template",
    "description": "Editorial dark-mode streetwear commerce with zero-friction checkout, optimized media pipeline, and physics-based micro-interactions.",
    "technologies": ["Next.js", "TypeScript", "Tailwind CSS", "Framer Motion"],
    "metrics": {
      "lighthouseScore": 99,
      "bundleSizeKb": 128
    },
    "createdAt": "2026-01-15T00:00:00Z",
    "updatedAt": "2026-10-10T00:00:00Z"
  }
}
```

### Response `404 Not Found`

```json
{
  "status": "error",
  "error": {
    "code": "PROJECT_NOT_FOUND",
    "message": "No project exists matching identifier: invalid-slug"
  }
}
```

---

## ✉️ 4. Submit Contact / Collaboration Inquiry

```http
POST /contact
```

Accepts and sanitizes project inquiries or collaborative requests. Dispatches notifications to engineering webhooks.

* **Authentication:** None (Protected by Edge Anti-Bot Turnstile & Rate Limiter)
* **Rate Limit:** 5 req/10 mins

### Request Body Schema

```json
{
  "name": "Alex Mercer",
  "email": "alex.mercer@example.com",
  "subject": "Creative Engineering Project Inquiry",
  "message": "We would like to collaborate on an interactive 3D web experience with Next.js.",
  "turnstileToken": "0x4AAAAAA..."
}
```

### Response `201 Created`

```json
{
  "status": "success",
  "data": {
    "ticketId": "inq_78bc901a",
    "deliveryStatus": "dispatched",
    "message": "Inquiry successfully recorded. You will receive a response within 24-48 hours."
  }
}
```

---

## 🔄 5. On-Demand ISR Revalidation (Admin)

```http
POST /admin/revalidate
```

Triggers Incremental Static Regeneration (ISR) to instantly refresh cached pages.

* **Authentication:** Required (`admin` role or `X-API-Key`)
* **Headers:** `X-API-Key: acr_live_...`

### Request Body

```json
{
  "tag": "projects",
  "path": "/projects/enigma-portfolio"
}
```

### Response `200 OK`

```json
{
  "status": "success",
  "data": {
    "revalidated": true,
    "path": "/projects/enigma-portfolio",
    "timestamp": "2026-10-10T05:36:00Z"
  }
}
```
