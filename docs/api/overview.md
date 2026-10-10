---
description: High-level architectural standards, protocols, response formats, and error handling for ACR APIs.
---

# API Overview

## 🌐 Introduction

The **ACR API** provides standardized programmatic access to public portfolios, showcase projects, telemetry, contact pipelines, and internal micro-services across `adicahyadir.dev`.

Our API design aligns with modern RESTful patterns, strict type-safety conventions, and idempotent operations where mutations are executed.

---

## 📍 Base URLs

The API is deployed across multi-region edge nodes:

| Environment | Base URL |
| :--- | :--- |
| **Production** | `https://api.adicahyadir.dev/v1` |
| **Staging / Preview** | `https://staging-api.adicahyadir.dev/v1` |
| **Local Development** | `http://localhost:3000/api/v1` |

---

## 📦 Request & Response Protocols

All requests must communicate using JSON payloads over HTTPS with UTF-8 encoding:

```http
Content-Type: application/json
Accept: application/json
```

### Standard Success Response Schema

Every successful response wraps its payload inside a predictable envelope:

```json
{
  "status": "success",
  "data": {
    "id": "proj_99a8b1",
    "title": "ACR Creative Portal",
    "slug": "acr-creative-portal",
    "status": "published"
  },
  "meta": {
    "timestamp": "2026-10-10T05:30:00Z",
    "version": "v1.0.0",
    "requestId": "req_88f01a3c-b19e-4c7b"
  }
}
```

### Standard Error Response Schema

In the event of an exception or validation failure, a consistent error contract is returned:

```json
{
  "status": "error",
  "error": {
    "code": "VALIDATION_FAILED",
    "message": "The provided request body failed schema validation.",
    "details": [
      {
        "field": "email",
        "issue": "Must be a valid email format"
      }
    ]
  },
  "meta": {
    "timestamp": "2026-10-10T05:30:00Z",
    "requestId": "req_88f01a3c-b19e-4c7b"
  }
}
```

---

## 🛑 HTTP Status Codes

The API strictly adheres to standard HTTP status codes:

| Code | Status | Meaning |
| :--- | :--- | :--- |
| `200` | **OK** | Request completed successfully. |
| `201` | **Created** | New resource successfully generated. |
| `204` | **No Content** | Request succeeded with no body returned. |
| `400` | **Bad Request** | Malformed syntax or invalid parameters. |
| `401` | **Unauthorized** | Missing or invalid API key / bearer token. |
| `403` | **Forbidden** | Caller does not possess adequate permissions. |
| `404` | **Not Found** | Specified resource does not exist. |
| `429` | **Too Many Requests** | Rate limit quota exceeded. |
| `500` | **Internal Error** | Unhandled server error (reported to telemetry). |

---

## ⏱️ Rate Limiting & Quotas

To safeguard infrastructure against abusive bursts, all endpoints enforce token-bucket rate limiting via Upstash Redis at the edge:

* **Public Read Endpoints:** 60 requests per minute per IP.
* **Authenticated Endpoints:** 600 requests per minute per API Key.
* **Form Submissions (Contact/Feedback):** 5 requests per 10 minutes per IP.

### Rate Limit Headers

```http
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 59
X-RateLimit-Reset: 1696914000
```

When throttled, the server returns HTTP `429 Too Many Requests` with a `Retry-After: <seconds>` response header.
