<div align="center">

# Agentic Design Patterns Navigator

### Turn pattern libraries into production agent architectures.

Pattern notebooks in. Deployable system design out.

<br>

![Domain](https://img.shields.io/badge/AI%20Agents-blue?style=for-the-badge)
![SDLC Automation](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
Pattern Repo + Use Case  →  Production Agent Architecture
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

Agentic AI pattern libraries are everywhere. Notebooks show you what routing looks like, how reflection works, when to use multi-agent setups. What they don't tell you is **which patterns to use for your problem, which to skip, and how to ship the result safely**.

**Agentic Design Patterns Navigator** is the engineering translation layer. Give it a pattern repository and a use case, and it produces a **complete, production-ready agent architecture** — with pattern selection, exclusion justifications, tool contracts, guardrails, evaluation plans, and a phased rollout strategy.

> You don't read notebooks and guess. You describe your use case. The Navigator designs your architecture.

<br>

### Why This Exists

| Without the Navigator | With the Navigator |
|---|---|
| Read notebooks, guess which patterns apply | Pattern mapping with inclusion/exclusion rationale |
| No guardrails until something breaks | Confidence thresholds, escalation rules, and kill switches from day one |
| Ship everything, hope it works | Phased rollout — each phase independently deployable |
| "We'll add evals later" | Evaluation plan with explicit acceptance thresholds |
| Unbounded loops, runaway costs | Max loop counts, wall-clock timeouts, cost ceilings |
| Memory on by default, PII everywhere | Memory OFF by default, opt-in with redaction rules |

<br>

---

<br>

## How It Works

<div align="center">

```
                      ┌───────────────────────────────────┐
                      │                                   │
                      │   AGENTIC DESIGN PATTERNS         │
                      │   NAVIGATOR                       │
                      │                                   │
                      │   ┌───────────────────────────┐   │
 ┌──────────────┐     │   │  1. Normalize patterns     │   │     ┌──────────────────┐
 │ Pattern Repo │────▶│   │  2. Map to production      │   │────▶│ Agent Architecture│
 │ + Use Case   │     │   │  3. Design agent graph     │   │     │                  │
 │              │     │   │  4. Define tool contracts   │   │     │ ■ Pattern map    │
 │ "customer    │     │   │  5. Set guardrails         │   │     │ ■ Agent graph    │
 │  support     │     │   │  6. Build eval plan        │   │     │ ■ Tool contracts │
 │  triage"     │     │   │  7. Phase the rollout      │   │     │ ■ Eval plan      │
 └──────────────┘     │   └───────────────────────────┘   │     │ ■ Rollout phases │
                      │                                   │     └──────────────────┘
                      └───────────────────────────────────┘
```

</div>

<br>

**The workflow:**

| Step | What You Do | What You Get |
|------|------------|--------------|
| **1. Provide inputs** | Pattern repo URL + target use case + SLOs | — |
| **2. Run the Navigator** | Paste the prompt. Provide your inputs. | A complete agent architecture document. |
| **3. Build** | Hand the architecture to your engineering team. | An ops-ready, phased agent system. |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`agentic-design-patterns-navigator.md`](./agentic-design-patterns-navigator.md) into a Claude or ChatGPT conversation.

### 2. Provide your inputs

```
Pattern source: https://github.com/sarwarbeing-ai/Agentic_Design_Patterns
Use case: Customer support triage — classify tickets, route to teams, draft responses
Latency SLO: p50 < 2s, p95 < 5s
Safety tolerance: Low — customer-facing
```

### 3. Receive your architecture

A 12-section architecture document — pattern mapping, agent graph, tool contracts, guardrails, eval plan, and phased rollout.

### 4. Ship

Each phase deploys independently. Start with Phase 0 (Router + Telemetry). Add capabilities one phase at a time.

<br>

---

<br>

## What You Get

```
┌────────────────────────────────────────────────────────────┐
│  AGENT ARCHITECTURE DOCUMENT                               │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ■ Assumptions           Defaults applied, listed upfront  │
│  ■ Pattern Mapping       Notebook → role, inclusion,       │
│                          rationale                         │
│  ■ Exclusion Report      What's out and why                │
│                                                            │
│  ■ Agent Graph           ASCII diagram + node specs        │
│  ■ State Machine         States, transitions, terminals    │
│  ■ Tool Contracts        Schema, timeout, retry, validate  │
│                                                            │
│  ■ Memory Policy         Scope, TTL, redaction (or OFF)    │
│  ■ Trust Boundaries      Model / tool / data boundaries    │
│  ■ Guardrails            Thresholds, escalation, refusal   │
│                                                            │
│  ■ Evaluation Plan       Offline + online + metrics        │
│  ■ Observability         Tracing, logging, alerting        │
│  ■ Rollout Phases        Independent deployment gates      │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Domains

<div align="center">

```
                    ┌───────────────────┐
                    │                   │
                    │  AGENTIC AI       │
                    │  ARCHITECTURE     │
                    │  (primary)        │
                    │                   │
                    └────────┬──────────┘
                             │
             ┌───────────────┼───────────────┐
             │               │               │
      ┌──────▼──────┐ ┌─────▼──────┐ ┌──────▼─────┐
      │             │ │            │ │            │
      │  SDLC       │ │  AI Agent  │ │  DevOps    │
      │  Automation  │ │  Systems   │ │  & Ops     │
      │             │ │            │ │            │
      └─────────────┘ └────────────┘ └────────────┘
```

</div>

<br>

| Domain | What the Navigator Covers |
|--------|--------------------------|
| **Agentic AI Architecture** | Pattern selection, agent graphs, state machines, multi-agent coordination, reflection loops |
| **SDLC Automation** | Tool contracts, phased rollout, evaluation plans, deployment gates |
| **AI Agent Systems** | Routing, planning, memory policies, trust boundaries, guardrail design |
| **DevOps & Ops** | Observability, tracing, alerting, kill switches, degraded mode, incident playbooks |

<br>

---

<br>

## Examples

### What You Can Design

| Use Case | Key Patterns Selected | Key Pattern Excluded |
|----------|----------------------|---------------------|
| Customer support triage | Routing, Tool Use, Reflection | Multi-Agent (single-path pipeline) |
| Code review agent | Routing, Reflection, Planning | Memory (no persistent state needed) |
| Research assistant | Planning, Tool Use, Memory | Multi-Agent (single researcher sufficient) |
| Document processing pipeline | Routing, Tool Use, Multi-Agent | Reflection (deterministic extraction) |
| Incident response bot | Routing, Tool Use, Memory | Planning (speed over deliberation) |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  Pattern source: github.com/sarwarbeing-ai/Agentic_Design_Patterns│
│  Use case: Customer support triage                                 │
│  Latency SLO: p50 < 2s, p95 < 5s                                 │
│  Safety: Low tolerance — customer-facing                           │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ NAVIGATOR ───────────────────────────────────────────────────────┐
│                                                                    │
│  Pattern Mapping:                                                  │
│  ✓ Routing     → Router Node (YES — core requirement)             │
│  ✓ Tool Use    → Action Nodes (YES — CRM/KB lookup)              │
│  ✓ Reflection  → Verifier (YES — no hallucinated policy)         │
│  ~ Planning    → Draft Worker (CONDITIONAL — complex only)        │
│  ✗ Memory      → OFF (privacy risk with customer data)           │
│  ✗ Multi-Agent → NO (adds latency, no accuracy gain)             │
│                                                                    │
│  Agent Graph:                                                      │
│  TICKET → CLASSIFY → ROUTE → DRAFT → VERIFY → EMIT              │
│                         └── ESCALATE → HUMAN_HANDOFF              │
│                                                                    │
│  Guardrails:                                                       │
│  • Confidence < 0.85 → escalate                                   │
│  • Policy mentions → deterministic rule check                     │
│  • Max 2 draft iterations                                          │
│  • 4.5s wall-clock timeout                                        │
│                                                                    │
│  Rollout: Phase 0 (Router) → Phase 1 (Tools) → Phase 2 (Verify) │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Start with the use case, not the patterns.**
The Navigator selects patterns for you. Don't pre-decide which patterns to include — describe the job-to-be-done and let the mapping do the work.

**Include your SLOs.**
Latency and cost constraints are the primary drivers of pattern exclusion. Without them, the Navigator uses conservative defaults that may be more restrictive than you need.

**Trust the exclusion report.**
The most valuable part of the output is what it tells you *not* to build. Every excluded pattern saves weeks of unnecessary complexity.

**Phase your deployment.**
Don't launch Phase 3 before Phase 0 is stable. Each phase is designed to ship independently. Validate before you expand.

**Iterate on the architecture.**
The first output is a starting point. Adjust SLOs, add constraints, change the use case scope. Each iteration sharpens the design.

<br>

---

<br>

## File Structure

```
prompts/examples/agentic-design-patterns-navigator/
├── agentic-design-patterns-navigator.md  # The prompt (paste this into AI)
├── README.md     # You are here
├── POST.md       # LinkedIn post
└── SPEC.md       # Full build specification
```

<br>

## Contributing

1. Fork the repository
2. Add support for new pattern taxonomies or use case domains
3. Test with 3-5 different use cases across complexity levels
4. Verify architecture outputs are complete — all 12 sections present
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Agentic Design Patterns Navigator**

Pattern libraries explain what's possible. This tells you what to build.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
