<div align="center">

# Conversational Code

### Paste any code, get a plain-English explanation anyone can understand.

<br>

![Domain](https://img.shields.io/badge/AI%20in%20Software%20Development-blue?style=for-the-badge)
![SDLC](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
Any code (any language)  →  Plain-English explanation anyone can understand
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

The vibe coding explosion of 2025-2026 created a new class of software builders — people who ship products but can't explain what their own code does. AI tools generate the code. Nobody reads it. It goes to production.

**Conversational Code** takes any code — a snippet, a function, a file, a config — and explains what it actually does in plain, conversational language. No CS degree required. No jargon without definitions. No line-by-line mechanical recitation.

> You don't need to learn to code to understand what your code does. You just need someone who speaks both languages.

<br>

### Why This Exists

| Without Conversational Code | With Conversational Code |
|---|---|
| Stare at AI-generated code you can't read and hope it works | Paste the code, get a plain-English explanation in seconds |
| Ask a developer friend to explain (and wait days for a reply) | Get a patient, jargon-free walk-through any time you need it |
| Ship vibe-coded apps you don't understand to real users | Understand exactly what your code does before it goes live |
| Sit in code review meetings nodding while understanding nothing | Walk in knowing what the code does and what to ask about |
| Pay a contractor and have no way to verify what they built | Read a plain-language explanation of every file they deliver |

<br>

---

<br>

## How It Works

<div align="center">

```
┌──────────────────┐     ┌──────────────────────┐     ┌──────────────────────────┐
│                  │     │                      │     │                          │
│   Paste Code     │────▶│ Conversational Code  │────▶│  Plain-English Briefing  │
│   (any language) │     │                      │     │                          │
│                  │     │  • Detects language   │     │  • Quick Version         │
│  + optional      │     │  • Finds moves        │     │  • Walk-Through          │
│    context       │     │  • Builds analogies   │     │  • Heads-Up (if needed)  │
│                  │     │  • Flags concerns      │     │                          │
└──────────────────┘     └──────────────────────┘     └──────────────────────────┘
```

</div>

<br>

**The pipeline:**

| Step | What Happens | What You Experience |
|------|-------------|---------------------|
| **1. Receive** | Takes your code and any context you provide | Paste and go — or add "I vibe-coded this" for tailored depth |
| **2. Detect** | Identifies language and high-level purpose | "This is your login system" — before any details |
| **3. Decompose** | Breaks code into 3-7 logical moves | Big picture first, then the story unfolds |
| **4. Explain** | Generates Quick Version + Walk-Through | Plain language, real analogies, no jargon walls |
| **5. Flag** | Scans for security, performance, and quality concerns | Friendly heads-up, not a formal audit |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`conversational-code.md`](./conversational-code.md) into a new Claude conversation.

### 2. Paste your code

```
I used Cursor to build a login page. Can you explain what this does?

[paste your code here]
```

### 3. Add context (optional)

```
I'm a non-technical founder reviewing what my contractor built.
```

### 4. Read your explanation

A three-layer briefing: the Quick Version (1-3 sentences), a conversational Walk-Through, and a Heads-Up if anything needs attention.

<br>

---

<br>

## What You Get

<div align="center">

```
┌──────────────────────────────────────────────────────┐
│  PLAIN-ENGLISH CODE BRIEFING                         │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Quick Version        1-3 sentences. What the      │
│                         code does. CEO-readable.      │
│                                                      │
│  ■ Walk-Through         Step-by-step in plain        │
│                         language with real-world      │
│                         analogies. No jargon.         │
│                                                      │
│  ■ Heads-Up             Security concerns, missing   │
│    (when relevant)      pieces, things to watch —    │
│                         in terms of consequences,    │
│                         not technical taxonomy.       │
│                                                      │
│  ■ Follow-Up Ready      Ask "what does line 14 do?" │
│                         or "is this safe?" and get   │
│                         a focused answer.             │
│                                                      │
│  ■ Audience-Adaptive    Adjusts depth based on your  │
│                         experience level — from       │
│                         non-technical to developer.   │
│                                                      │
│  ■ Honest Uncertainty   Names what it can't see      │
│                         instead of guessing.          │
│                                                      │
└──────────────────────────────────────────────────────┘
```

</div>

<br>

---

<br>

## Domains

| Domain | What It Explains |
|--------|-----------------|
| **Web Applications** | Login systems, APIs, routes, middleware, authentication flows, server configs |
| **Frontend** | React/Vue/Svelte components, state management, event handlers, CSS logic |
| **Backend** | Database queries, server endpoints, business logic, data processing pipelines |
| **DevOps / Infra** | Dockerfiles, Terraform configs, CI/CD pipelines, Kubernetes manifests, bash scripts |
| **Data** | SQL queries, data transformations, pandas pipelines, ETL scripts |
| **Any Language** | JavaScript, Python, TypeScript, Java, C#, Go, Rust, Ruby, PHP, Swift, Kotlin, YAML, and more |

<br>

---

<br>

## Examples

### What You Can Explain

| Paste This | Get This |
|-----------|---------|
| AI-generated login endpoint | "This is your login system. It checks the email, checks the password, and hands them a 24-hour digital pass." |
| Contractor's payment integration | Plain-language walk-through of every step money touches, plus security flags |
| Vibe-coded React component | What the UI does, how state changes, what triggers re-renders — in everyday terms |
| Terraform infrastructure config | "This sets up 3 servers, a database, and a load balancer on AWS" |
| Legacy COBOL from a bank | Best-effort logic explanation with honest uncertainty about syntax specifics |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  "I used Cursor to build a login page for my SaaS app.            │
│   I don't really understand what it generated."                    │
│                                                                    │
│  [pastes 20 lines of Express/bcrypt/JWT login code]               │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ CONVERSATIONAL CODE ────────────────────────────────────────────┐
│                                                                    │
│  THE QUICK VERSION                                                │
│  This is your login system. When someone types their email and    │
│  password and hits submit, it checks if the email exists, checks  │
│  the password, and hands them a digital pass for the next 24hrs. │
│                                                                    │
│  THE WALK-THROUGH                                                 │
│  ├── Gathers tools (web framework, password checker, pass maker) │
│  ├── Looks up the email in the database (like a hotel front desk)│
│  ├── Checks the password against a scrambled version (hash)      │
│  ├── Creates a token (wristband that proves you showed your ID)  │
│  └── Sends the token + basic account info back                    │
│                                                                    │
│  THE HEADS-UP                                                     │
│  ├── JWT secret key — if it's weak, someone could forge tokens   │
│  └── No rate limiting — nothing stops thousands of login attempts │
│       (might be handled elsewhere, or might be missing)           │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Add context for better explanations.**
"I'm a non-technical founder" and "I'm a junior dev" produce different explanations of the same code. Both are accurate — the framing changes.

**Ask follow-up questions.**
After the initial explanation, ask "what does line 14 do?" or "is this safe to deploy?" or "explain it like I'm telling my boss." The prompt is built for conversation, not one-shot answers.

**Paste more for better Heads-Ups.**
The more code you share, the more accurately the prompt can flag concerns. A single function gets a focused explanation. A full file gets the big picture plus connections between parts.

**Don't worry about specifying the language.**
The prompt auto-detects it. Just paste and go.

**Use it for code review prep.**
Before a code review meeting, paste the PR's changed files and get a plain-English summary. Walk in knowing what to ask about.

<br>

---

<br>

## File Structure

```
INTAKE/
├── spec.md                  # Prompt specification (source of truth)
├── conversational-code.md   # The prompt — paste into AI
├── README.md                # You are here
└── POST.md                  # LinkedIn post
```

<br>

## Contributing

1. Fork the repository
2. Test with users of different experience levels (non-technical, beginner, developer)
3. Verify explanations are accurate, accessible, and never condescending
4. Test with code in multiple languages and varying complexity
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Conversational Code**

Paste any code. Get a plain-English explanation anyone can understand.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
