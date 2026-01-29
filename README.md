# Charis Web Services

![Charis Web Services](/cover.jpg)

**Charis Web Services** provides full-access, secure, server-side proxy endpoints for a variety of third-party APIs.

All requests are authenticated, safe, and optimized for performance, caching, and reliability. API keys and secrets never leave the server.

This service allows developers, portfolios, and personal websites to integrate external APIs without exposing sensitive credentials, while handling validation, error responses, timeouts, and temporary file cleanup.

All requests **must include a User API Token** from your dashboard.

---

## Authentication

Include the following headers in **every request**:

```http
Authorization: Bearer YOUR_CHARIS_TOKEN
charis-secret: YOUR_CHARIS_SECRET
```

Without valid credentials, requests will return `401 Unauthorized`.

---

## Why Use Charis Web Services?

* **Server-side security**: API keys and sensitive data never leave the backend.
* **Full access**: All endpoints are available without limitations.
* **Optimized performance**: Caching, timeouts, and temporary file cleanup handled automatically.
* **Reliable & robust**: Detailed logging, validation, and error handling included.
* **Developer-focused**: Ideal for portfolios, personal websites, and lightweight backend integrations.

---

## Pricing

| Plan       | Price         | Notes                                                          |
| ---------- | ------------- | -------------------------------------------------------------- |
| Free       | Free          | 7-day trial                                                    |
| PRO        | 500k IDR/mo   | Full access to all endpoints, priority support, faster caching |
| Enterprise | Contact Sales | SLA, dedicated IP, and custom caching rules                    |

---

## Documentation

Detailed integration guides with code examples:

- [Cloudinary Media Management](https://charisprod.xyz/apis/cloudinary)
- [Weather Data Fetching](https://charisprod.xyz/apis/weather)
- [Spotify Music Integration](https://charisprod.xyz/apis/spotify)
- [ICD-10 WHO](https://charisprod.xyz/apis/icd-10)

Built with charm, beauty, and a touch of creativity ✨
