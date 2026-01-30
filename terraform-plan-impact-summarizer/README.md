<div align="center">

# Terraform Plan Impact Summarizer

### Turn Terraform plans into clear, risk-aware change summaries for fast approvals.

<br>

![Domain](https://img.shields.io/badge/DevOps-blue?style=for-the-badge)
![SDLC Automation](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
terraform plan → Impact Summarizer → Risk Report + PR Comment
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [What It Catches](#what-it-catches) · [Examples](#examples) · [Pro Tips](#pro-tips)

</div>

<br>

---

<br>

## Overview

Terraform plans are verbose, hard to interpret, and often approved blindly — leading to outages, security exposure, and unexpected costs. Reviewers skim hundreds of lines of diff output and hope for the best.

**Terraform Plan Impact Summarizer** converts raw `terraform plan` output into a concise, structured change report. It highlights what will change, who is impacted, the risk level, blast radius, security signals, cost direction, and required pre-flight checks — all formatted for PR review.

> Stop skimming plans. Start reviewing impact.

<br>

### Why This Exists

| Without the Summarizer | With the Summarizer |
|---|---|
| Reviewers skim raw plan logs and hope for the best | Reviewers get a 60-second impact summary |
| Risky changes slip through approvals unnoticed | Explicit risk flags + per-change classification |
| Security and cost surprises surface after apply | Security + cost signals highlighted pre-merge |
| "Looks good to me" on a 200-line plan | Actionable checklist tailored to detected changes |
| No one catches the `0.0.0.0/0` buried in the diff | Public exposure flagged as CRITICAL with controls checklist |

<br>

---

<br>

## How It Works

<div align="center">

```
 ┌──────────────────┐      ┌─────────────────────────────────────┐      ┌──────────────────────┐
 │                  │      │                                     │      │                      │
 │  terraform plan  │      │     IMPACT SUMMARIZER               │      │  Change Impact       │
 │  (text or JSON)  │─────▶│                                     │─────▶│  Report              │
 │                  │      │  1. Parse plan + detect changes     │      │                      │
 │  + optional      │      │  2. Classify actions & risk         │      │  ■ Executive Summary │
 │    context:      │      │  3. Flag security / cost / downtime │      │  ■ Risk Assessment   │
 │    env, region,  │      │  4. Assess blast radius             │      │  ■ Pre-Flight Checks │
 │    service,      │      │  5. Generate PR-ready report        │      │  ■ PR Comment        │
 │    risk tolerance│      │                                     │      │                      │
 │                  │      │                                     │      │                      │
 └──────────────────┘      └─────────────────────────────────────┘      └──────────────────────┘
```

</div>

<br>

**The workflow:**

| Step | What You Do | What You Get |
|------|------------|--------------|
| **1. Paste** | Feed in `terraform plan` output (text, JSON, or CI logs) | — |
| **2. Add context** (optional) | Specify env, region, service, risk tolerance | More precise risk assessment |
| **3. Receive report** | Read the structured impact summary | Risk-rated changes, blast radius, security flags, pre-flight checklist, PR comment |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`terraform-plan-impact-summarizer.md`](./terraform-plan-impact-summarizer.md) into a new Claude or ChatGPT conversation.

### 2. Paste your plan

```
Context:
- env: prod
- region: us-west-2
- service: payments-api
- risk_tolerance: low

Terraform Plan:
  # aws_security_group.payments will be updated in-place
  ~ resource "aws_security_group" "payments" {
      ~ ingress = [
          ~ {
              from_port   = 443
              to_port     = 443
              protocol    = "tcp"
            - cidr_blocks = ["10.0.0.0/8"]
            + cidr_blocks = ["0.0.0.0/0"]
            }
        ]
    }

  # aws_db_instance.payments will be replaced
-/+ resource "aws_db_instance" "payments" {
      ~ instance_class = "db.m5.large" -> "db.m6i.large" # forces replacement
      ~ allocated_storage = 200 -> 300
      ~ identifier = "payments-prod"
    }

Plan: 0 to add, 1 to change, 1 to destroy.
```

### 3. Get your report

A structured impact report appears — executive summary, risk assessment, security flags, pre-flight checks, and a ready-to-paste PR comment.

<br>

---

<br>

## What You Get

```
┌──────────────────────────────────────────────────────┐
│  CHANGE IMPACT REPORT                                │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Executive Summary     Risk level, net changes,    │
│                          downtime, top concerns      │
│                                                      │
│  ■ Change Inventory      Adds / Updates /            │
│                          Replacements / Destroys     │
│                                                      │
│  ■ Risk Assessment       Per-change risk + drivers   │
│                                                      │
│  ■ Blast Radius          Affected components +       │
│                          dependencies                │
│                                                      │
│  ■ Security & Compliance Exposure changes, IAM,      │
│                          encryption signals          │
│                                                      │
│  ■ Availability          Downtime expectations       │
│                                                      │
│  ■ Cost Signals          Direction + flags           │
│                                                      │
│  ■ Pre-Flight Checks     Tailored checklist          │
│                                                      │
│  ■ PR Comment            Ready to paste              │
│                                                      │
│  ■ Unknowns              Only if genuinely needed    │
│                                                      │
└──────────────────────────────────────────────────────┘
```

<br>

---

<br>

## What It Catches

| Category | Signals |
|----------|---------|
| **Security** | Public exposure (`0.0.0.0/0`), IAM expansion, encryption/logging toggles, compliance violations |
| **Availability** | Stateful replacements, downtime risk, rollback constraints, blue/green readiness |
| **Cost** | Instance class upgrades, storage increases, new resource creation, scaling changes |
| **Operations** | Blast radius, dependency chains, pre-flight checks, maintenance window needs |

<br>

---

<br>

## Examples

### What You Can Analyze

| Plan Contains | Summarizer Flags |
|--------------|-----------------|
| Security group opens `0.0.0.0/0` | **CRITICAL** — public exposure increase, recommends WAF/ALB controls |
| RDS instance class change forces replacement | **CRITICAL** — stateful replacement, downtime expected, backup checklist |
| S3 bucket policy broadened | **HIGH** — public access risk, encryption check, logging validation |
| Lambda memory increase | **LOW** — cost direction up, no availability impact |
| No-op plan (zero changes) | Confirms no changes, suggests drift detection + state validation |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  Context: env=prod, service=payments-api, risk_tolerance=low       │
│                                                                    │
│  Plan: SG opens 443 to 0.0.0.0/0 + RDS replacement                │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ SUMMARIZER ──────────────────────────────────────────────────────┐
│                                                                    │
│  Executive Summary                                                 │
│  ─────────────────                                                 │
│  Overall risk: CRITICAL                                            │
│  Net changes: +0 ~1 -1 (replaces: 1)                              │
│  Downtime: expected (DB replacement)                               │
│                                                                    │
│  Top concerns:                                                     │
│  1) RDS replacement → outage + complex rollback                    │
│  2) SG exposes 443 to 0.0.0.0/0                                   │
│  3) Low risk tolerance requires explicit approvals                 │
│                                                                    │
│  Pre-Flight Checks:                                                │
│  ☐ DB snapshot exists and restore tested                           │
│  ☐ Cutover plan attached (maintenance window)                      │
│  ☐ SG change intentional? WAF/ALB controls confirmed?              │
│  ☐ tfsec/checkov passed                                            │
│  ☐ Monitoring alerts for DB connectivity + 5xx                     │
│                                                                    │
│  PR Comment: "High risk for prod: replaces RDS (downtime) +       │
│  opens 443 to internet. Attach cutover plan + confirm backups."    │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Add context for better results.**
A bare plan gets you a solid summary. Adding `env: prod` and `risk_tolerance: low` gets you a report calibrated to your actual risk posture.

**Use it in CI.**
Pipe `terraform plan` output into a prompt call. Post the summary as a PR comment. Reviewers read the summary, not the raw plan.

**Combine with policy tools.**
Run tfsec/checkov alongside. The summarizer flags operational risk; policy scanners flag compliance. Together, they cover the full picture.

**Large plans? Still works.**
Plans with 100+ resources get categorized and ranked. Top 10 highest-risk changes get full detail; the rest are counted and grouped.

**JSON plans are supported.**
`terraform show -json plan.out` gives the summarizer more data to work with. Use it when available.

<br>

---

<br>

## File Structure

```
terraform-plan-impact-summarizer/
├── terraform-plan-impact-summarizer.md   # The prompt (paste this into AI)
├── README.md                             # You are here
├── POST.md                               # LinkedIn post
└── SPEC.md                               # Full specification
```

<br>

## Contributing

1. Fork the repository
2. Extend detection patterns (new resource types, risk signals)
3. Test with real-world plans across AWS/GCP/Azure
4. Verify reports are actionable — would you approve a PR based on this summary?
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Terraform Plan Impact Summarizer**

Stop skimming plans. Start reviewing impact.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

*Powered by Vox — VDD: Voice Driven Development*

</div>
