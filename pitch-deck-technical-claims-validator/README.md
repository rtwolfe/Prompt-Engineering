<div align="center">

# Pitch Deck Technical Claims Validator

### Surface the gap between pitch deck promises and codebase reality before investors do.

<br>

![Domain](https://img.shields.io/badge/Due_Diligence-blue?style=for-the-badge)
![SDLC Automation](https://img.shields.io/badge/SDLC_Automation-purple?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI_Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
Pitch Deck + Codebase  →  Verification Report (✅ ⚠️ ❌ 🔍)
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips)

</div>

<br>

---

<br>

## Overview

Pitch decks are sales documents. Founders present aspirational claims about performance, scale, proprietary technology, and compliance readiness. Some claims are accurate. Some are optimistic. Some are vaporware. Investors conducting technical due diligence will eventually look under the hood—and when pitch deck assertions don't match codebase reality, deals collapse or terms worsen.

**Pitch Deck Technical Claims Validator** systematically extracts technical claims from pitch materials and cross-references each against actual code evidence, producing a verification report that distinguishes what's verified, what's partially supported, and what's unsubstantiated. For investors, it's a first-pass red flag detector. For founders, it's a pre-diligence audit that lets you fix the narrative before it's challenged.

> It transforms "trust us" into "here's the evidence."

<br>

### Why This Exists

| Without This Tool | With Pitch Deck Technical Claims Validator |
|---|---|
| Investors discover claim gaps during diligence | Founders fix narrative before investor scrutiny |
| "We'll verify this later" becomes dealbreaker | Claims pre-validated with evidence citations |
| Vague assertions create due diligence friction | Each claim mapped to specific code evidence |
| Optimistic claims treated the same as fabrications | Clear distinction: verified, partial, unverified |
| Technical diligence takes weeks of back-and-forth | Structured report surfaces issues in hours |
| Founders blindsided by investor technical questions | Investor questions anticipated with prepared answers |

<br>

---

<br>

## How It Works

<div align="center">

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                   PITCH DECK TECHNICAL CLAIMS VALIDATOR                     │
└─────────────────────────────────────────────────────────────────────────────┘

     INPUTS                        PROCESS                        OUTPUT
┌─────────────────┐         ┌─────────────────────┐         ┌─────────────────┐
│                 │         │                     │         │  VERIFICATION   │
│  PITCH DECK     │         │  ┌───────────────┐  │         │     REPORT      │
│  ───────────    │         │  │    Extract    │  │         │                 │
│  • Slide claims │────────▶│  │    Claims     │  │         │ ┌─────────────┐ │
│  • Metrics      │         │  └───────┬───────┘  │         │ │✅ Verified  │ │
│  • Assertions   │         │          │          │         │ │⚠️ Partial   │ │
│                 │         │          ▼          │         │ │❌ Unverified│ │
└─────────────────┘         │  ┌───────────────┐  │         │ └─────────────┘ │
                            │  │   Cross-Ref   │  │         │                 │
     CODEBASE               │  │   Against     │  │────────▶│ Evidence tables │
┌─────────────────┐         │  │   Codebase    │  │         │ w/ file paths   │
│  ───────────    │         │  └───────┬───────┘  │         │                 │
│  • Source code  │────────▶│          │          │         │ Investor Qs     │
│  • Configs      │         │          ▼          │         │                 │
│  • Tests        │         │  ┌───────────────┐  │         │ Narrative       │
│  • Benchmarks   │         │  │   Generate    │  │         │ adjustments     │
│                 │         │  │   Verdicts    │  │         │                 │
└─────────────────┘         │  └───────────────┘  │         └─────────────────┘
                            └─────────────────────┘
```

</div>

<br>

**The 4-phase pipeline:**

| Phase | What Happens |
|-------|-------------|
| **1. Extract** | Parse pitch deck for explicit and implicit technical claims. Classify by category. Assess materiality. |
| **2. Recon** | Map repository structure. Locate evidence directories. Extract actual technical capabilities. |
| **3. Verify** | Cross-reference each claim against code evidence. Performance, scale, security, compliance, proprietary tech—each verified against category-specific standards. |
| **4. Synthesize** | Assign verdicts. Generate investor questions. Draft narrative adjustments. Calculate verification score. Produce executive summary. |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`pitch-deck-technical-claims-validator.md`](./pitch-deck-technical-claims-validator.md) into a Claude, ChatGPT, or any LLM conversation with codebase access.

### 2. Provide inputs

```
PITCH DECK CLAIMS:

Slide 4 (Technology):
1. "Proprietary ML pipeline achieves 94% accuracy on fraud detection"
2. "Sub-50ms API response time at p99"

Slide 7 (Security):
3. "SOC 2 Type II certified"
4. "End-to-end encryption for all customer data"

CODEBASE: github.com/your-company/platform (access granted)
```

### 3. Receive verification report

A structured report with per-claim verdicts, evidence tables with file paths, investor questions, and narrative adjustments.

<br>

---

<br>

## What You Get

```
┌──────────────────────────────────────────────────────┐
│  VERIFICATION REPORT                                 │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Executive Summary     Score + red/yellow/green    │
│                          flags at a glance           │
│                                                      │
│  ■ Claim Analysis        Per-claim verdict with      │
│                          evidence tables, file        │
│                          paths, and code refs         │
│                                                      │
│  ■ Investor Questions    Sharp, specific follow-ups  │
│                          for diligence meetings       │
│                                                      │
│  ■ Narrative Fixes       Suggested rewording that    │
│                          is accurate AND compelling   │
│                                                      │
│  ■ Methodology           What was analyzed, what     │
│                          couldn't be verified         │
│                                                      │
│  ■ Evidence Catalog      Complete file-to-claim      │
│                          mapping + glossary           │
│                                                      │
└──────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Domains

| Claim Category | What Gets Verified |
|---|---|
| **Performance** | Latency, accuracy, throughput metrics against benchmarks, load tests, APM configs |
| **Scale** | Volume and capacity claims against infrastructure configs, auto-scaling, load test results |
| **Security** | Encryption, authentication, vulnerability posture against actual code implementation |
| **Compliance** | SOC 2, GDPR, HIPAA controls against code; flags when external audit reports are needed |
| **Proprietary Tech** | "Proprietary" and "patent-pending" claims against actual differentiation vs. standard libraries |
| **Traction** | Uptime, volume, customer claims against monitoring configs; flags for external validation |

<br>

---

<br>

## Examples

### What You Can Validate

| Pitch Deck Claim | What The Validator Checks |
|---|---|
| "Sub-50ms p99 latency" | Load test results, APM configs, performance benchmarks |
| "SOC 2 Type II certified" | Audit logging, access controls, encryption—flags need for actual audit report |
| "Proprietary ML pipeline" | Custom code vs. standard library wrappers, actual differentiation |
| "Handles 1M transactions/day" | Infrastructure capacity, auto-scaling limits, load test ceilings |
| "End-to-end encryption" | TLS config, encryption at rest, application-layer crypto |
| "99.99% uptime" | Monitoring config, health checks, multi-AZ deployment, historical data |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  Validate these claims against our repos:                          │
│                                                                    │
│  Slide 4: "Proprietary NLP engine — 96% accuracy"                 │
│  Slide 6: "Platform handles 500K API calls/day"                   │
│  Slide 8: "End-to-end encryption for all customer data"           │
│                                                                    │
│  Repos: github.com/chatwise/platform, /nlp-engine, /infra         │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ VALIDATOR ────────────────────────────────────────────────────────┐
│                                                                    │
│  Verification Score: 50%                                           │
│                                                                    │
│  ⚠️ NLP accuracy: 92.3% (not 96%) — eval file shows discrepancy  │
│     → Suggest: "92%+ accuracy across 15K+ test samples"            │
│                                                                    │
│  ❌ 500K API calls: Infrastructure ceiling is 150K/day             │
│     → ECS: 6 tasks × 25K = 150K max                               │
│     → Suggest: "Architecture designed for 500K+; provisioned       │
│       for 150K with scaling headroom"                              │
│                                                                    │
│  ✅ Encryption: TLS 1.3, KMS at rest, field-level PII crypto      │
│     → Claim is well-supported. No changes needed.                  │
│                                                                    │
│  Red Flag: Scale claim 3x beyond infrastructure capacity           │
│  Green Flag: Encryption implementation is comprehensive            │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Provide all repos, not just the main one.** Infrastructure repos (Terraform, K8s) are where scale and security claims get verified or debunked. ML repos contain the evaluation data that accuracy claims depend on.

**Include optional artifacts.** Load test results, API specs, and monitoring configs dramatically increase verification depth. Without them, more claims land in "Unable to Assess."

**Run it before your investors do.** The best use case isn't investor diligence—it's founder pre-diligence. Fix the narrative gaps before they become dealbreakers.

**Use the narrative adjustments.** The validator doesn't just flag problems—it suggests accurate, still-compelling alternatives. A claim adjusted from "handles 500K" to "architecture designed for 500K, provisioned for 150K" is still strong.

**Share the report proactively.** A founder who hands investors a self-audited verification report signals confidence and transparency. It reframes diligence from adversarial to collaborative.

<br>

---

<br>

## File Structure

```
INTAKE/
├── pitch-deck-technical-claims-validator.md  # The prompt (paste into AI)
├── README.md    # You are here
├── SPEC.md      # Full specification
└── POST.md      # LinkedIn post
```

<br>

## Contributing

1. Fork the repository
2. Add verification standards for new claim categories
3. Test with 3-5 real pitch deck claim sets
4. Verify reports are evidence-based with specific file citations
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Pitch Deck Technical Claims Validator**

Your pitch deck makes promises. Your codebase keeps receipts.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by **Vox** — VDD: Voice Driven Development

</div>
