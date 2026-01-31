<div align="center">

# Backend API Tester Pro

### Generate exhaustive API test suites from specs — contracts, security, performance, and edge cases automatically.

<br>

![Domain](https://img.shields.io/badge/QA%20%2F%20DevOps-blue?style=for-the-badge)
![SDLC](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
OpenAPI Spec  →  82 executable test cases (pytest / Jest / k6 / Postman)
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

Most teams write happy-path tests and call it done. The contract violations, authorization holes, boundary failures, and performance regressions surface in production — where they cost the most.

**Backend API Tester Pro** generates comprehensive, executable test suites directly from your API specification. One OpenAPI spec in, a multi-dimensional test suite out — covering contract validation, OWASP API Top 10 security checks, load/stress scenarios, and boundary/edge case permutations.

> You don't write 200 test cases by hand. You feed it your spec. It generates the tests that catch what manual testing misses.

<br>

### Why This Exists

| Without Backend API Tester Pro | With Backend API Tester Pro |
|---|---|
| Write happy-path tests manually, miss authorization holes until production incident | Generate BOLA/BFLA tests automatically from spec, catch privilege escalation in CI |
| Copy-paste boundary tests for every numeric field, still miss edge cases | Derive boundary tests from schema constraints — min, max, min-1, max+1 — automatically |
| "We should add security tests" stays on the backlog for six sprints | OWASP API Top 10 coverage generated in minutes, blocking deploy on failures |
| Performance testing happens the week before launch (or never) | Load/stress scenarios with concrete SLO thresholds ready for CI/CD integration |
| QA manually writes 200 test cases, spec changes, half are now stale | Regenerate test suite from updated spec — tests always match current contract |

<br>

---

<br>

## How It Works

<div align="center">

```
┌─────────────────────┐
│   OpenAPI Spec      │
│   (or GraphQL /     │
│    endpoint docs)   │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────┐
│                 BACKEND API TESTER PRO                       │
│                                                             │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌───────┐ │
│  │  Contract   │ │  Security   │ │ Performance │ │ Edge  │ │
│  │  Analyzer   │ │  Scanner    │ │  Planner    │ │ Case  │ │
│  │             │ │  (OWASP)    │ │             │ │ Finder│ │
│  └─────────────┘ └─────────────┘ └─────────────┘ └───────┘ │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                  EXECUTABLE TEST SUITE                       │
│  • pytest / Jest / Postman / k6                             │
│  • 60-100+ test cases per API                               │
│  • CI/CD ready with failure thresholds                      │
└─────────────────────────────────────────────────────────────┘
```

</div>

<br>

**The pipeline:**

| Step | Input | Output |
|------|-------|--------|
| **1. Parse** | OpenAPI / Swagger / GraphQL schema | Internal constraint model |
| **2. Analyze** | Constraint model + test scope | Test case matrix |
| **3. Generate** | Test case matrix + output format | Executable test suite |
| **4. Package** | Test suite + environment config | CI/CD-ready test artifact |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`backend-API-tester-pro.md`](./backend-API-tester-pro.md) into a new Claude conversation.

### 2. Paste your API spec

```yaml
openapi: 3.0.3
info:
  title: Order Management API
  version: 1.2.0
paths:
  /orders:
    post:
      summary: Create new order
      # ... your full spec here
```

### 3. Declare scope

```
Test Scope: All dimensions
Authentication: Bearer token (JWT)
Output Format: pytest with requests library
Priority Endpoints: POST /orders, GET /orders/{orderId}
```

### 4. Receive your test suite

A structured test suite with 60-100+ test cases, organized by category, ready to drop into your CI/CD pipeline.

<br>

---

<br>

## What You Get

<div align="center">

```
┌──────────────────────────────────────────────────────┐
│  GENERATED TEST SUITE                                │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Coverage Summary       Test counts by category    │
│                                                      │
│  ■ Contract Validation    Schema, status codes,      │
│                           required fields, types     │
│                                                      │
│  ■ Security Tests         OWASP API Top 10:          │
│    (OWASP-aligned)        BOLA, Auth, Property Auth, │
│                           Injection, SSRF, Misconfig │
│                                                      │
│  ■ Performance Scenarios  Baseline, stress, spike,   │
│                           endurance + SLO thresholds │
│                                                      │
│  ■ Edge Case / Boundary   Boundary values, type      │
│                           coercion, unicode, nulls   │
│                                                      │
│  ■ Test Data Requirements Fixtures, mocks, seed data │
│                                                      │
│  ■ CI/CD Integration      Pipeline stages, parallel  │
│                           strategy, failure gates     │
│                                                      │
└──────────────────────────────────────────────────────┘
```

</div>

<br>

---

<br>

## Domains

| Domain | What Gets Tested |
|--------|-----------------|
| **REST APIs** | OpenAPI 3.0+, Swagger 2.0 — full endpoint coverage with schema-derived assertions |
| **GraphQL** | Query/mutation shapes, depth limits, introspection exposure, variable type mismatches |
| **Authentication** | JWT, OAuth, API keys — missing, expired, malformed, wrong scheme, cross-user reuse |
| **Authorization** | BOLA, BFLA, property-level auth — multi-user context tests with horizontal/vertical escalation |
| **Performance** | Load, stress, spike, endurance — concrete SLO thresholds (p50/p95/p99 latency, error rate, RPS) |
| **Security** | OWASP API Top 10 (2023) — injection, SSRF, misconfiguration, resource consumption |

<br>

---

<br>

## Examples

### What You Can Test

| Feed It | Get Back |
|---------|---------|
| Order Management API (2 endpoints) | 82 test cases: 18 contract, 24 security, 8 performance, 32 edge case |
| User Profile API (2 endpoints) | 58 test cases: 12 contract, 18 security, 6 performance, 22 edge case |
| Payment Gateway (10 endpoints) | 200+ test cases with PCI-relevant security checks |
| Microservice mesh (50+ endpoints) | Tiered coverage: full depth on priority endpoints, contract-only for the rest |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  [OpenAPI spec for User Profile API v2.0.0]                       │
│  Test Scope: All | Output: pytest | Auth: Bearer JWT              │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ BACKEND API TESTER PRO ──────────────────────────────────────────┐
│                                                                    │
│  Coverage: 58 tests | 2/2 endpoints | 4 categories                │
│                                                                    │
│  CONTRACT:                                                        │
│  ├── CV001: GET returns 200 with valid UserProfile schema         │
│  ├── CV002: GET returns 404 for nonexistent user                  │
│  └── CV005: PATCH returns 400 on invalid payload                  │
│                                                                    │
│  SECURITY:                                                        │
│  ├── SEC001: [BOLA] User A cannot access User B's profile        │
│  ├── SEC004: [Auth] No-token request rejected with 401           │
│  └── SEC008: [Property Auth] Cannot escalate role to admin       │
│                                                                    │
│  EDGE CASES:                                                      │
│  ├── EDGE001: displayName at minLength (1 char) accepted         │
│  ├── EDGE003: displayName at maxLength+1 (51 chars) rejected     │
│  └── EDGE014: Unicode characters handled correctly               │
│                                                                    │
│  + Test data fixtures, performance configs, CI/CD integration     │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Scope it or drown in output.**
Full scope on a 50-endpoint API produces 500+ tests. Use `Priority Endpoints` to focus depth where it matters. Use `Test Scope: Security` to generate just the OWASP checks.

**Specify your framework.**
The default is framework-agnostic HTTP examples. Specify `pytest`, `Jest/Supertest`, `k6`, or `Postman` and get ready-to-run code with correct imports, assertions, and fixtures.

**Feed it your gaps.**
Add `Existing test gaps: We had a BOLA incident on /orders last month` and the prompt will prioritize authorization tests on that endpoint with deeper coverage.

**Regenerate on spec change.**
Spec changed? Regenerate. The test suite always matches the current contract. No more stale tests.

**Chain with CI/CD.**
The output includes pipeline stage placement and failure thresholds. Drop the generated tests into your CI pipeline and block deploys on security or contract failures.

<br>

---

<br>

## File Structure

```
INTAKE/
├── SPEC.md       # Prompt specification (source of truth)
├── backend-API-tester-pro.md   # The prompt — paste into AI
├── README.md     # You are here
```

<br>

## Contributing

1. Fork the repository
2. Add support for additional API spec formats or test frameworks
3. Test with 3-5 real API specifications
4. Verify generated test suites are executable and catch real issues
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Backend API Tester Pro**

One spec. Four test dimensions. Production-ready.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
