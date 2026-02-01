<div align="center">

# Playwright Test Scaffolder

### Convert user stories into production-ready Playwright tests with page objects and full coverage.

<br>

![Domain](https://img.shields.io/badge/QA%20%2F%20SDLC-blue?style=for-the-badge)
![SDLC](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
User Story + Acceptance Criteria  →  Page Object + Test File + Coverage Summary
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

Your team writes acceptance criteria in Jira. Then a QA engineer spends 2-4 hours translating each story into Playwright tests — choosing locators inconsistently, missing edge cases, and burying assertions inside page objects.

**Playwright Test Scaffolder** takes a user story with acceptance criteria and produces a complete, immediately-runnable test scaffold: TypeScript test file, Page Object Model class, realistic test data, and coverage across happy path, negative, and edge-case scenarios.

> One user story in. A production-ready test scaffold out. Every locator follows Playwright's official hierarchy. Every test runs in isolation.

<br>

### Why This Exists

| Without this tool | With Playwright Test Scaffolder |
|---|---|
| 2-4 hours translating each user story into test code | Complete test scaffold in under 60 seconds |
| Inconsistent locator strategies across the team (CSS, XPath, mixed) | Every locator follows Playwright's official getByRole-first hierarchy |
| Happy path only — edge cases discovered in production | Automatic edge case derivation from acceptance criteria |
| Page Objects with mixed concerns — assertions buried in POM classes | Clean separation: locators and actions in POM, assertions in tests only |
| No traceability from test to requirement | Every test links back to its acceptance criterion number |

<br>

---

<br>

## How It Works

<div align="center">

```
┌─────────────────────┐
│   User Story +      │
│   Acceptance         │
│   Criteria           │
│   + Page Context     │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────┐
│              PLAYWRIGHT TEST SCAFFOLDER                       │
│                                                             │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌───────┐ │
│  │   Parse     │ │  Locator    │ │  Page Object│ │ Test  │ │
│  │   Story     │ │  Strategy   │ │  Builder    │ │ Gen   │ │
│  │             │ │             │ │             │ │       │ │
│  └─────────────┘ └─────────────┘ └─────────────┘ └───────┘ │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                  OUTPUT                                       │
│  ├── pages/feature.page.ts    (Page Object Model)           │
│  ├── tests/feature.spec.ts    (Test file)                   │
│  └── Coverage Summary         (Matrix + suggestions)        │
└─────────────────────────────────────────────────────────────┘
```

</div>

<br>

**The pipeline:**

| Step | Input | Output |
|------|-------|--------|
| **1. Parse** | User story + acceptance criteria | Testable conditions + edge cases |
| **2. Design** | Page context + AC language | Locator strategy per element |
| **3. Build POM** | Locator strategy + pages | TypeScript Page Object classes |
| **4. Generate** | Testable conditions + POM | Test file + coverage summary |

<br>

---

<br>

## Quick Start

### Option 1: Interactive Form (Recommended)

Open [`QUICKSTART.html`](./QUICKSTART.html) in your browser. Fill in your user story, acceptance criteria, and options. Click **Generate Prompt** and paste the result into Claude, ChatGPT, or any LLM.

### Option 2: Direct Prompt

1. Copy [`playwright-scaffolder.md`](./playwright-scaffolder.md) into a new AI conversation.

2. Paste your user story:

```
USER STORY: As a returning customer, I want to add items to my shopping
cart from the product listing page so that I can purchase multiple
products in a single checkout.

ACCEPTANCE CRITERIA:
1. Clicking "Add to Cart" on any product card adds that product to the cart
2. The cart icon in the header updates to show the correct item count
3. Adding the same product twice increments the quantity
4. Cart state persists across page navigation

BASE URL: https://shop.example.com
```

3. Receive your test scaffold — Page Object, test file, and coverage summary — ready to drop into your project.

<br>

---

<br>

## What You Get

<div align="center">

```
┌──────────────────────────────────────────────────────┐
│  GENERATED TEST SCAFFOLD                             │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Page Object Model     Typed locators, action      │
│    (.page.ts)            methods, zero assertions    │
│                                                      │
│  ■ Test File             Happy path, negative path,  │
│    (.spec.ts)            edge cases per AC           │
│                                                      │
│  ■ Coverage Summary      AC-to-test matrix,          │
│                          uncovered areas, suggested  │
│                          enhancements                │
│                                                      │
│  ■ Locator Strategy      getByRole → getByLabel →   │
│                          getByText → getByTestId     │
│                                                      │
│  ■ Traceability          Every test links to its     │
│                          acceptance criterion #      │
│                                                      │
│  ■ Test Isolation        Every test runs standalone  │
│                          — no shared state           │
│                                                      │
└──────────────────────────────────────────────────────┘
```

</div>

<br>

---

<br>

## Domains

| Domain | What Gets Scaffolded |
|--------|---------------------|
| **E-commerce** | Cart interactions, checkout flows, product filtering, inventory states |
| **Authentication** | Registration, login, password reset, session management, MFA |
| **Forms** | Multi-field validation, conditional fields, file uploads, multi-step wizards |
| **Dashboards** | Data tables, filtering, sorting, pagination, real-time updates |
| **Search** | Query input, result rendering, filtering, empty states, autocomplete |
| **CRUD** | Create/read/update/delete flows with optimistic UI and error recovery |

<br>

---

<br>

## Examples

### What You Can Scaffold

| Feed It | Get Back |
|---------|---------|
| Registration form (7 ACs) | 18 tests: field validation, password strength, email format, edge cases |
| Shopping cart (7 ACs) | 15 tests: add/remove, quantity, persistence, max limits, out of stock |
| Search with filters (5 ACs) | 12 tests: query, filter combos, empty state, pagination, debounce |
| Admin user management (10 ACs) | 24 tests: CRUD, roles, permissions, bulk actions, audit logging |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  USER STORY: As a new user, I want to register for an account     │
│  ACCEPTANCE CRITERIA: 7 items (fields, validation, redirect...)   │
│  BASE URL: https://app.example.com                                │
│  PAGE CONTEXT: Registration page at /register                     │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ PLAYWRIGHT TEST SCAFFOLDER ──────────────────────────────────────┐
│                                                                    │
│  Coverage: 18 tests | 7/7 ACs | 3 categories                     │
│                                                                    │
│  PAGE OBJECT (registration.page.ts):                              │
│  ├── RegistrationPage class                                       │
│  ├── 6 locators (getByLabel, getByRole)                          │
│  ├── fillForm(), submit(), goto()                                │
│  └── getFieldError(), getValidationMessage()                     │
│                                                                    │
│  TESTS (registration.spec.ts):                                    │
│  ├── HAPPY PATH: register + redirect to /welcome                 │
│  ├── AC #2: 5 required field validation tests                    │
│  ├── AC #3: 3 email format tests                                 │
│  ├── AC #4: 5 password strength tests + boundary                 │
│  ├── AC #5: 2 password match tests                               │
│  ├── AC #7: 1 duplicate email test                               │
│  └── EDGE: special chars, whitespace, form preservation          │
│                                                                    │
│  COVERAGE: 7/7 ACs covered (1 partial — needs seeded data)       │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Include page context.**
The more you describe the actual DOM — element labels, button text, layout — the better the locators. Without page context, every locator gets an `// INFERRED LOCATOR` comment and will need manual validation.

**Specify authentication.**
Add `AUTH: storageState from auth.setup.ts` or `AUTH: API login via POST /api/auth/login`. Without it, generated tests assume no auth and add TODO comments.

**Reference existing page objects.**
If you already have a `LoginPage` class, mention it: `EXISTING POM: LoginPage with login(email, password) method`. The scaffolder will import it instead of regenerating.

**Use numbered acceptance criteria.**
The traceability system maps tests to AC numbers. Numbered criteria produce cleaner coverage matrices than bullet points or free-form prose.

**Iterate per story.**
Feed one user story at a time. The output is scoped to that story's acceptance criteria. Run it per story in your sprint and build coverage incrementally.

<br>

---

<br>

## File Structure

```
INTAKE/
├── SPEC.md                              # Prompt specification (source of truth)
├── playwright-scaffolder.md              # The prompt — paste into AI
├── README.md                            # You are here
├── POST.md                              # LinkedIn post
└── QUICKSTART.html                      # Interactive intake form
```

<br>

## Contributing

1. Fork the repository
2. Test with 3-5 real user stories from different domains
3. Verify generated tests follow Playwright best practices and run in isolation
4. Check coverage summaries accurately reflect AC mapping
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Playwright Test Scaffolder**

One story. Full coverage. Production-ready.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
