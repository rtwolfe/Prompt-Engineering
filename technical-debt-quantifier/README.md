<div align="center">

# Startup Technical Debt Quantifier

### Convert "we have some legacy code" into "$47,000 per quarter in lost engineering velocity."

<br>

![Domain](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![Category](https://img.shields.io/badge/Quality%20Control%20%2F%20QA-blue?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
Codebase + Team Size + Budget  →  Board-Ready Financial Debt Report
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips)

</div>

<br>

---

<br>

## Overview

Engineering teams can't get refactoring budget because they describe debt in technical terms. Boards don't approve "reducing cyclomatic complexity" — they approve investments with measurable ROI.

**Startup Technical Debt Quantifier** translates your codebase into the language of finance: dollars lost per quarter, remediation investment required, payback period, and 3-year ROI. It turns "we need to refactor" into a business case that gets funded.

> SonarQube reports technical debt in minutes. This prompt reports it in dollars that appear on income statements.

<br>

### Why This Exists

| Without This Tool | With Startup Technical Debt Quantifier |
|---|---|
| "We have some legacy code issues" | "Technical debt costs $156K/quarter" |
| Engineering asks for refactoring time; leadership asks "why?" | Complete ROI analysis: $141K investment, 5-month payback, 234% Year 1 return |
| Vague sense that velocity is declining | Precise measurement: 40% of engineering capacity lost to debt |
| Refactoring feels like a cost center | Remediation framed as investment with measurable returns |
| Board doesn't understand technical updates | CFO-ready report with financial metrics and benchmarks |
| No urgency to address debt | Compound interest model shows cost of delay |

<br>

---

<br>

## How It Works

<div align="center">

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    STARTUP TECHNICAL DEBT QUANTIFIER                        │
└─────────────────────────────────────────────────────────────────────────────┘

     INPUTS                        ANALYSIS                        OUTPUT
┌─────────────────┐         ┌─────────────────────┐         ┌─────────────────┐
│                 │         │                     │         │   BOARD-READY   │
│ • Codebase      │         │  ┌───────────────┐  │         │   FINANCIAL     │
│ • Team Size     │────────▶│  │  Code Quality │  │         │   REPORT        │
│ • Eng Budget    │         │  │   Analysis    │  │         │                 │
│ • Company Stage │         │  └───────┬───────┘  │         │ ┌─────────────┐ │
│                 │         │          │          │         │ │ $156K/QTR   │ │
└─────────────────┘         │          ▼          │         │ │ DEBT TAX    │ │
                            │  ┌───────────────┐  │         │ └─────────────┘ │
     OPTIONAL               │  │   Financial   │  │         │                 │
┌─────────────────┐         │  │   Modeling    │  │         │ ┌─────────────┐ │
│ • Sprint Data   │         │  │              │  │────────▶│ │ $187K       │ │
│ • Bug-Fix Ratio │────────▶│  │ $/hr × hours │  │         │ │ REMEDIATION │ │
│ • Coverage Rpts │         │  │ = $ impact   │  │         │ └─────────────┘ │
│ • CI/CD Configs │         │  └───────┬───────┘  │         │                 │
└─────────────────┘         │          │          │         │ ┌─────────────┐ │
                            │          ▼          │         │ │ 234% ROI    │ │
                            │  ┌───────────────┐  │         │ │ 5-MO PAYBACK│ │
                            │  │  Benchmarking │  │         │ └─────────────┘ │
                            │  │  & ROI Calc   │  │         │                 │
                            │  └───────────────┘  │         │ + Remediation   │
                            │                     │         │   Roadmap       │
                            └─────────────────────┘         └─────────────────┘
```

</div>

<br>

**The workflow is four phases:**

| Phase | What Happens | What It Produces |
|-------|-------------|-----------------|
| **1. Context** | Parse team size, budget, stage, data sources | Financial parameters + stage benchmarks |
| **2. Analysis** | Scan codebase for complexity, duplication, coverage, dependencies | Technical debt inventory with effort estimates |
| **3. Modeling** | Convert every metric to dollars, model accumulation | Debt tax, remediation costs, ROI projections |
| **4. Report** | Rank by business impact, build roadmap | Board-ready financial assessment |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`technical-debt-quantifier.md`](./technical-debt-quantifier.md) into a new Claude or ChatGPT conversation.

### 2. Provide context

```
COMPANY CONTEXT:
- Company: YourCo
- Stage: Series A
- Product Type: B2B SaaS
- Codebase Age: 2 years

ENGINEERING TEAM:
- Team Size: 8 engineers
- Average Fully-Loaded Cost: $195,000/year

REPOSITORY ACCESS:
- github.com/yourco/platform (access granted)
```

### 3. Receive your report

A complete financial assessment: executive summary with headline dollar figure, debt tax breakdown, remediation roadmap with ROI, and stage-appropriate benchmarks.

### 4. Present

Drop the report into your next board deck, investor update, or budget conversation. Every number is in dollars. Every recommendation has a payback period.

<br>

---

<br>

## What You Get

```
┌──────────────────────────────────────────────────────┐
│  TECHNICAL DEBT FINANCIAL ASSESSMENT                 │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Executive Summary     Headline $ figure + key     │
│                          metrics in one page         │
│                                                      │
│  ■ Financial Impact      Monthly debt tax breakdown  │
│                          with compound projections   │
│                                                      │
│  ■ Debt Inventory        By category with severity,  │
│                          cost, and remediation effort │
│                                                      │
│  ■ Top 10 Hotspots       Specific files ranked by    │
│                          business cost impact         │
│                                                      │
│  ■ Velocity Analysis     Current vs. potential with   │
│                          "equivalent engineers" math  │
│                                                      │
│  ■ ROI Analysis          Investment, payback period,  │
│                          3-year cumulative return     │
│                                                      │
│  ■ Remediation Roadmap   3 phases: Quick Wins, Core, │
│                          Sustain — with $ per phase   │
│                                                      │
│  ■ Benchmarks            Stage-appropriate comps      │
│                          (not enterprise standards)   │
│                                                      │
│  ■ Appendix              Full methodology so every    │
│                          number is traceable          │
│                                                      │
└──────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Domains

| Domain | What Gets Quantified |
|--------|---------------------|
| **SDLC Automation** | Build/deploy delays, CI pipeline waste, environment friction, release overhead |
| **Quality Control / QA** | Test coverage gaps, code complexity, duplication, documentation debt, review overhead |
| **AI in Software Dev** | ML pipeline debt, model versioning gaps, training infrastructure inefficiency |
| **DevOps** | Dependency staleness, security vulnerabilities, infrastructure configuration debt |

<br>

---

<br>

## Examples

### What It Looks Like

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  COMPANY: HealthSync | Series A | 8 engineers | $1.56M budget     │
│  CODEBASE: 2.5 years old | 48% test coverage | 40% bug-fix ratio │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ QUANTIFIER ─────────────────────────────────────────────────────────┐
│                                                                      │
│  HEADLINE: Technical debt costs $156,000 per quarter                 │
│            (40% of engineering budget)                                │
│                                                                      │
│  DEBT TAX:                                                           │
│  ├── Bug fixes & rework .............. $21,120/mo  (24% capacity)   │
│  ├── Legacy code workarounds ......... $9,680/mo   (11% capacity)   │
│  ├── Extended code reviews ........... $5,280/mo   (6% capacity)    │
│  ├── Build/deploy delays ............. $4,840/mo   (5.5% capacity)  │
│  └── Onboarding friction ............. $2,640/mo   (3% capacity)    │
│                                                                      │
│  INVESTMENT: $141,500 one-time  |  PAYBACK: 5.1 months              │
│  YEAR 1 ROI: 234%              |  3-YEAR SAVINGS: $849,500          │
│                                                                      │
│  ROADMAP:                                                            │
│  Phase 1 (Weeks 1-4): $44K → +8% velocity                          │
│  Phase 2 (Months 2-3): $97.5K → +12% velocity                      │
│  Phase 3 (Ongoing): 15% capacity allocation                         │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

<br>

### Audiences It Serves

| Audience | What They Get |
|----------|--------------|
| **Board of Directors** | One-page executive summary with headline cost and ROI |
| **Investors / VCs** | Due diligence-grade technical health assessment |
| **Engineering Managers** | Justified refactoring budget with payback math |
| **CTOs** | Prioritized remediation roadmap with effort estimates |
| **Fractional CTOs** | Portfolio company health reports in consistent format |

<br>

---

<br>

## Pro Tips

**Provide real data for real numbers.**
The more data you supply (sprint velocity, bug-fix ratio, coverage reports), the tighter the estimates. Without data, the prompt uses industry benchmarks and flags where it's estimating.

**Stage matters more than score.**
A seed startup with 20% TDR is healthy. A Series B company with 20% TDR needs intervention. The prompt calibrates automatically — don't panic at raw numbers without context.

**Run it before scaling the team.**
Adding engineers to a high-debt codebase multiplies the debt tax. If you're hiring 3 engineers into a 40% debt-tax environment, 1.2 of those engineers are immediately consumed by debt. Fix first, hire second.

**Use the roadmap, not just the headline.**
The headline number gets attention. The phased roadmap gets work done. Phase 1 Quick Wins are designed to show results in 4 weeks — use them to build momentum and trust.

**Re-run quarterly.**
Track your debt tax over time. The compound interest model projects forward, but measuring actuals lets you calibrate and show the board that remediation investment is paying off.

<br>

---

<br>

## File Structure

```
INTAKE/
├── technical-debt-quantifier.md    # The prompt (paste this into AI)
├── README.md    # You are here
├── POST.md      # LinkedIn post
└── SPEC.md      # Full specification
```

<br>

## Contributing

1. Fork the repository
2. Improve financial models or add industry-specific benchmarks
3. Test with 3-5 company profiles across different stages
4. Verify output is understandable by non-technical readers
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Startup Technical Debt Quantifier**

Your codebase has a price tag. Now your board can see it.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
