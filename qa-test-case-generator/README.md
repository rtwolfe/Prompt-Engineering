<div align="center">

# QA Test Case Generator

### Convert PRs or requirements into risk-based, traceable QA test cases — ready for execution.

<br>

![QA](https://img.shields.io/badge/QA-blue?style=for-the-badge)
![SDLC Automation](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
PR or Requirements  →  Risk-Based Test Suite (executable, traceable, automation-ready)
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Examples](#examples) · [Domains](#domains) · [Pro Tips](#pro-tips)

</div>

<br>

---

<br>

## Overview

Most QA test cases are written after the fact — skimming a PR, guessing at edge cases, copying from last sprint's template. The result: inconsistent coverage, missed risk areas, and test suites that catch what's obvious but miss what matters.

**QA Test Case Generator** takes the actual input — a PR description with diffs or a set of requirements with acceptance criteria — and produces a complete, execution-ready test suite. Every test case has an ID, a priority, explicit steps, concrete data, and a traceable link back to what it verifies.

> You don't write test cases. You paste the PR. The generator writes them. You review and execute.

<br>

### Why This Exists

| Without the Generator | With the Generator |
|---|---|
| Skim PR, write tests from memory | Structured analysis of every changed behavior |
| Miss negative and edge cases | Negative, edge, and regression tests generated automatically |
| No traceability to requirements | Every test traces back to a specific input element |
| "Verify it works" as a test step | Numbered steps with concrete data and exact expected results |
| Manual risk assessment (or none) | Risk model built per behavior — Critical, High, Medium, Low |
| Automation candidates unclear | Each test marked: automate now, automate later, manual only |

<br>

---

<br>

## How It Works

<div align="center">

```
┌─────────────────────┐
│                     │
│  PR Description     │      ┌──────────────────────────────────┐
│  + Diff Summary     │      │                                  │
│                     │      │   QA TEST CASE GENERATOR         │
│  ── OR ──           │      │                                  │
│                     │─────▶│   1. Detect input mode            │      ┌───────────────────┐
│  Requirements       │      │   2. Extract testable behaviors  │─────▶│  Execution-Ready  │
│  + Acceptance       │      │   3. Build risk model            │      │  Test Suite        │
│    Criteria         │      │   4. Generate traceability       │      │                   │
│                     │      │   5. Produce test cases          │      │  ■ Test cases     │
│  ── OPTIONAL ──     │      │   6. Recommend automation        │      │  ■ Traceability   │
│                     │      │   7. Surface gaps                │      │  ■ Risk model     │
│  Project Context    │      │                                  │      │  ■ Automation recs│
│  (app type, auth,   │      └──────────────────────────────────┘      └───────────────────┘
│   tooling)          │
└─────────────────────┘
```

</div>

<br>

**Two input modes, one output format:**

| Mode | What You Provide | Best For |
|------|-----------------|----------|
| **PR Mode** | PR title, description, diff summary | Code reviews, sprint QA, regression |
| **Requirements Mode** | User story, acceptance criteria, NFRs | Sprint planning, test design, UAT prep |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`qa-test-case-generator.md`](./qa-test-case-generator.md) into a new AI conversation as the system prompt.

### 2. Paste your input

```
PR #482: Add email verification on signup

Changes: Added POST /api/verify-email endpoint. Users receive a
6-digit code after registration. Code expires in 10 minutes.
Three failed attempts lock verification for 1 hour.
```

### 3. Get your test suite

A complete test suite appears — risk-ranked, traceable, with concrete steps and data for every test case. Review, adjust priorities if needed, and execute.

<br>

---

<br>

## What You Get

<div align="center">

```
┌──────────────────────────────────────────────────────┐
│  QA TEST SUITE OUTPUT                                │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Change Understanding   Scope, mode, assumptions   │
│  ■ Test Strategy          Risk model + distribution  │
│  ■ Traceability Map       Input → Test Case IDs      │
│  ■ Test Cases             Grouped by risk level      │
│    ├─ Functional          Happy path verification    │
│    ├─ Negative            Invalid input, auth bypass │
│    ├─ Edge Case           Boundaries, timing, limits │
│    ├─ Regression          Existing behavior held     │
│    └─ Non-Functional      Perf, security, a11y      │
│  ■ Automation Backlog     Now / Later / Manual only  │
│  ■ Open Questions         Gaps and ambiguities       │
│  ■ Coverage Checklist     Behavior → covered?        │
│                                                      │
└──────────────────────────────────────────────────────┘
```

</div>

<br>

Every test case follows this format:

```
TC-001 | P0 | Functional
Title: Valid 6-digit code verifies email successfully
Preconditions:
  - User registered with jane.doe@example.com
Steps:
  1. POST /api/verify-email with code 483921
  2. Assert response status 200
  3. Query users.email_verified
Expected Result:
  - Response: {"verified": true}
  - email_verified = true
Test Data:
  - Email: jane.doe@example.com | Code: 483921
Traceability: PR #482 — verify-email endpoint
```

<br>

---

<br>

## Examples

### What You Can Test

| Input Type | Example | Test Cases Generated |
|-----------|---------|---------------------|
| Auth PR | `POST /api/verify-email` with lockout | Functional, negative (bad code), edge (expiry boundary), regression |
| Payment feature | Stripe checkout with promo codes | Happy path, invalid card, expired promo, concurrent checkout |
| RBAC requirement | "Admins can delete users, editors cannot" | Permission matrix, privilege escalation, role switching |
| API migration | REST → GraphQL for `/users` endpoint | Contract parity, error format, pagination, auth header |
| Mobile feature | Offline-first sync for notes app | Sync on reconnect, conflict resolution, partial upload |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  PR #482: Add email verification on signup                         │
│  Added POST /api/verify-email. 6-digit code. Expires 10 min.      │
│  3 failed attempts = 1 hour lockout.                               │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ GENERATOR ───────────────────────────────────────────────────────┐
│                                                                    │
│  Mode: PR                                                          │
│  Scope: Email verification — new endpoint, expiry, lockout         │
│                                                                    │
│  Risk Model:                                                       │
│   Critical (3): Auth bypass, lockout enforcement, expiration       │
│   High (4): Happy path, invalid codes, schema integrity            │
│   Medium (3): Resend, timing edge, UI feedback                     │
│   Low (2): Email format, cosmetic                                  │
│                                                                    │
│  12 test cases │ Traceability map │ Automation backlog             │
│  3 open questions │ Coverage checklist                              │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Domains

| Domain | What This Generator Covers |
|--------|---------------------------|
| **Web Applications** | Form validation, auth flows, CRUD operations, session management, responsive behavior |
| **APIs** | Endpoint contracts, status codes, error formats, rate limiting, pagination, auth headers |
| **Mobile** | Offline behavior, push notifications, deep links, permissions, gesture handling |
| **Infrastructure** | Config changes, migration scripts, environment parity, rollback scenarios |
| **Security** | Auth bypass, injection, CSRF, privilege escalation, data exposure |

<br>

---

<br>

## Pro Tips

**Include the diff, not just the description.**
PR descriptions tell you what the author intended. Diffs tell you what actually changed. The generator produces better tests when it can see both.

**Add project context.**
"This is a React + Express app using JWT auth and Playwright for E2E" gives the generator enough to tailor test data, suggest frameworks, and flag auth-specific edge cases.

**Use it at two points in the sprint.**
Run it on requirements during planning (catch ambiguity early) and again on the PR (catch implementation gaps). The two suites complement each other.

**Review the Open Questions first.**
If the generator flagged ambiguities, resolve them before executing tests. An ambiguous requirement produces ambiguous test results.

**Pipe into your test management tool.**
The structured format (ID, priority, steps, expected result) maps directly to Jira/Zephyr, TestRail, qTest, or Azure Test Plans. Copy-paste or script the import.

<br>

---

<br>

## File Structure

```
INTAKE/
├── qa-test-case-generator.md                        # The prompt (paste into AI)
├── qa_test_case_generator_prs_requirements.md       # Original spec
├── SPEC.md                                          # Spec (copy)
├── README.md                                        # You are here
└── POST.md                                          # LinkedIn post
```

<br>

## Contributing

1. Fork the repository
2. Add domain-specific test patterns or edge cases to the prompt
3. Test with 3-5 real PRs or requirement sets across different domains
4. Verify generated test suites are executable — run them, don't just read them
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**QA Test Case Generator**

From change to coverage in one pass.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
