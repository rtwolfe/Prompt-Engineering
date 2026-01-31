<div align="center">

# Technical Due Diligence Analyzer

**Transform codebases into investor-grade technical risk assessments in minutes, not weeks.**

![SDLC Automation](https://img.shields.io/badge/SDLC-Automation-blue?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI-Powered-purple?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-VC%20%2F%20DevOps%20%2F%20QA-teal?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

```
Codebase + Context ──▶ [ 7-Phase Analysis ] ──▶ Investment-Grade Risk Report
```

</div>

---

[Overview](#overview) | [How It Works](#how-it-works) | [Quick Start](#quick-start) | [What You Get](#what-you-get) | [Domains](#domains) | [Examples](#examples) | [Pro Tips](#pro-tips) | [File Structure](#file-structure) | [Contributing](#contributing) | [License](#license)

---

## Overview

VC technical due diligence currently requires 20+ hours of manual expert review per deal—analyzing repos, interviewing engineers, and translating findings into investment risk language. This prompt automates the entire pipeline: systematic assessment of codebases, architectures, and engineering practices into structured reports that quantify technical debt, scalability risk, security posture, bus factor, and IP defensibility.

Built for VC associates, technical advisors, M&A teams, and founders preparing for diligence. Replaces weeks of billable hours with actionable intelligence that surfaces dealbreakers before they become post-investment surprises.

| Without This Tool | With Technical Due Diligence Analyzer |
|-------------------|---------------------------------------|
| 20+ hours of manual code review per deal | Comprehensive analysis in under 1 hour |
| Expensive external technical advisors ($5K-15K/engagement) | Consistent, repeatable assessment at fraction of cost |
| Subjective assessments that miss buried risks | Systematic coverage of security, scalability, debt, and team risk |
| Technical findings that don't translate to term sheets | Every finding quantified with investment impact and dollar costs |
| Pitch deck claims taken at face value | Claims cross-referenced against actual code evidence |
| Bus factor and knowledge concentration invisible | Contribution analysis surfaces key-person dependencies |

---

## How It Works

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    TECHNICAL DUE DILIGENCE ANALYZER                         │
└─────────────────────────────────────────────────────────────────────────────┘

     INPUTS                         ANALYSIS                        OUTPUT
┌─────────────────┐         ┌─────────────────────┐         ┌─────────────────┐
│ • GitHub Repos  │         │  ┌───────────────┐  │         │   INVESTMENT-   │
│ • Tech Stack    │────────▶│  │ Code Quality  │  │────────▶│   GRADE REPORT  │
│ • Company Stage │         │  │   Analysis    │  │         │                 │
│ • Team Size     │         │  └───────┬───────┘  │         │ • Risk Rating   │
│ • Pitch Claims  │         │          │          │         │ • Key Findings  │
└─────────────────┘         │  ┌───────▼───────┐  │         │ • TDR + $Cost   │
                            │  │ Architecture  │  │         │ • Security Gaps │
     OPTIONAL               │  │  & Scalability│  │         │ • Bus Factor    │
┌─────────────────┐         │  └───────┬───────┘  │         │ • Claims Verify │
│ • CI/CD Configs │         │          │          │         │ • Remediation   │
│ • IaC Files     │────────▶│  ┌───────▼───────┐  │         │   Roadmap       │
│ • API Specs     │         │  │   Security    │  │         │                 │
│ • Test Reports  │         │  │   Assessment  │  │         │ ┌─────────────┐ │
│ • Coverage Data │         │  └───────┬───────┘  │         │ │ Go/No-Go/   │ │
└─────────────────┘         │          │          │         │ │ Conditional │ │
                            │  ┌───────▼───────┐  │         │ └─────────────┘ │
                            │  │ Team & Process│  │         └─────────────────┘
                            │  │   Analysis    │  │
                            │  └───────┬───────┘  │
                            │          │          │
                            │  ┌───────▼───────┐  │
                            │  │ IP & Claims   │  │
                            │  │  Validation   │  │
                            │  └───────────────┘  │
                            └─────────────────────┘
```

**7 phases. 23 steps. One report.**

1. **Repository Intake** — Enumerate structure, detect languages, catalog configs
2. **Code Quality Analysis** — Technical debt ratio, test coverage, dependency health
3. **Architecture Assessment** — Pattern classification, IaC coverage, scalability readiness
4. **Security Posture** — Auth audit, secret scanning, OWASP API Top 10, compliance
5. **Team & Process** — Bus factor calculation, velocity indicators, CI/CD maturity
6. **IP & Claims Validation** — Proprietary tech evaluation, pitch deck claim verification
7. **Synthesis** — Risk ratings, remediation roadmap, Go/No-Go recommendation

---

## Quick Start

1. **Provide company context** — Stage, product type, team size, company age
2. **Declare the tech stack** — Languages, frameworks, infrastructure, databases
3. **Grant repository access** — GitHub/GitLab URLs or local paths
4. **Add pitch deck claims** (optional) — Technical claims you want validated
5. **Run the prompt** — Receive a structured due diligence report

```
COMPANY CONTEXT:
- Company: [Name]
- Stage: [Pre-seed | Seed | Series A | Series B+]
- Product Type: [B2B SaaS | Consumer | API/Platform | AI/ML | DevTools]
- Team Size: [X] engineers
- Age: [X] months since first commit

TECH STACK:
- Languages: [e.g., Python, TypeScript, Go]
- Frameworks: [e.g., FastAPI, React, Gin]
- Infrastructure: [e.g., AWS (ECS, RDS, S3)]
- Database: [e.g., PostgreSQL, Redis]

REPOSITORY ACCESS:
- [repo URL] (access granted)

PITCH DECK CLAIMS TO VALIDATE:
1. "[Claim from pitch materials]"
```

---

## What You Get

```
┌──────────────────────────────────────────────────────────────┐
│                   DUE DILIGENCE REPORT                       │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  Executive Summary          Risk Rating + Go/No-Go/Cond.    │
│  ─────────────────          ─────────────────────────────    │
│  Top 5 findings with        Clear recommendation with       │
│  investment impact           specific conditions             │
│                                                              │
│  Codebase Health            Architecture & Scale             │
│  ───────────────            ──────────────────               │
│  TDR score + $ cost         Pattern + IaC + SPOFs            │
│  Test coverage vs bench     Scaling readiness 1-10           │
│  Dependency CVE count       Performance bottlenecks          │
│                                                              │
│  Security Posture           Team & Process                   │
│  ────────────────           ──────────────                   │
│  OWASP API Top 10 audit     Bus factor per component         │
│  Auth + secrets scan        Dev velocity + CI/CD maturity    │
│  Compliance readiness       Knowledge concentration map      │
│                                                              │
│  IP & Claims                Remediation Roadmap              │
│  ──────────                 ───────────────────              │
│  Proprietary tech eval      Critical: before close           │
│  Pitch claim verdicts       High: 90-day post-close          │
│  OSS risk analysis          Debt paydown plan + $ cost       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Domains

| Domain | Coverage |
|--------|----------|
| SDLC Automation | Technical debt quantification, CI/CD maturity, development velocity |
| Quality Control / QA | Test coverage analysis, code quality metrics, dependency health |
| DevOps | Infrastructure-as-Code audit, scalability assessment, deployment strategy |
| Security | OWASP API Top 10, secret scanning, auth audit, compliance readiness |
| Investment Diligence | Risk ratings, claims validation, remediation costing, Go/No-Go |

**Supported Languages:** Python, JavaScript/TypeScript, Go, Java, Ruby, Rust, and mixed-language repositories.

**Stage Calibration:** Pre-seed through Series B+ with stage-appropriate benchmarks.

---

## Examples

### Series A SaaS — Real-time Video Platform

```
Input:
  Company: StreamForge | Series A | 8 engineers | 26 months
  Stack: Go + Python + TypeScript | AWS EKS | PyTorch CV models
  Claims: "40% bandwidth reduction vs H.265", "50K concurrent streams"

Output:
  Risk Rating: Medium
  Recommendation: Conditional Go

  Key Findings:
  ├── ❌ Critical: ML bus factor = 1 (single contributor: 89%)
  ├── ❌ High: API rate limiting absent on billing endpoints
  ├── ⚠️ High: Security audit 14 months stale
  ├── ⚠️ Medium: ML test coverage 45% (benchmark: 55%)
  └── ⚠️ Medium: 23 deps with known CVEs (4 High)

  Claims Validation:
  ├── ✅ 40% compression: Verified (38-43% in benchmarks)
  ├── ⚠️ Sub-200ms latency: Partial (720p only)
  ├── ⚠️ 50K streams: Partial (28K validated, 35K infra limit)
  └── ✅ 2M+ hours training data: Verified (2.3M hours)

  Remediation: 6-8 eng-weeks (~$72K)
```

---

## Pro Tips

- **Include pitch deck claims.** The claims validation engine is one of the highest-value sections for investors—it produces clear Verified/Partial/Unverified verdicts with code evidence.

- **Provide CI/CD and IaC files.** These dramatically improve infrastructure and process assessment depth. Without them, those sections rely on inference.

- **Specify company stage.** Benchmarks are stage-calibrated. A Seed startup's 50% test coverage is fine; for Series B, it's a yellow flag.

- **Grant access to all repos.** Partial access produces partial reports. The tool documents limitations but can't assess what it can't see.

- **Include coverage reports.** If available, actual coverage data beats file-ratio estimation every time.

---

## File Structure

```
technical-due-diligence-analyzer/
├── technical-due-diligence-analyzer.md   # Self-contained prompt — copy and use directly
├── README.md                             # This file
├── SPEC.md                               # Full specification and design document
```

---

## Contributing

Contributions are welcome. To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built by [Tim Wolfe](https://github.com/rtwolfe)** | [t.me/timwolfe](https://t.me/timwolfe)

Powered by **Vox** — VDD: Voice Driven Development

</div>
