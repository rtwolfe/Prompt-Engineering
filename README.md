<div align="center">

# Terraform CI/CD Pipeline Architect

### Design secure Terraform pipelines that plan, apply, and govern infrastructure changes safely.

Stop treating `terraform apply` like a script. Start treating it like a release.

<br>

![DevOps](https://img.shields.io/badge/DevOps-blue?style=for-the-badge)
![SDLC](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![MIT](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
context in  →  production-grade pipeline blueprint out
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips)

</div>

<br>

---

<br>

## Overview

Most Terraform pipelines are **plan/apply scripts** bolted onto CI. They work until they don't — then someone auto-applies to prod at 4pm on a Friday.

The problem: teams copy generic workflow YAML, hardcode credentials, skip approvals, share state across environments, and call it "infrastructure as code." The pipeline runs. But there's no isolation, no gating, no audit trail, and no drift detection.

**Terraform CI/CD Pipeline Architect** designs pipelines the way platform teams build them — with environment isolation, least-privilege identity, approval gates, policy-as-code, and operational runbooks.

<br>

| Without Pipeline Architect | With Pipeline Architect |
|---|---|
| Generic plan/apply YAML | CI-specific, path-filtered workflows |
| Long-lived IAM credentials | OIDC federation with scoped roles |
| Shared state across environments | Isolated state per environment per stack |
| No approval gates | Protected environment with required reviewers |
| No policy enforcement | OPA/Sentinel + tflint + checkov integrated |
| No drift detection | Nightly scheduled plan with alerting |
| "Just run apply" runbook | Operational procedures for every failure mode |

<br>

---

<br>

## How It Works

<div align="center">

```
┌────────────────┐
│  Your Infra    │
│  Context       │
└───────┬────────┘
        │
        ▼
┌────────────────────────────────────────────────────────────┐
│              TERRAFORM CI/CD PIPELINE ARCHITECT             │
│                                                            │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │ Parse    │→ │ Design   │→ │ Generate │→ │ Harden   │  │
│  │ Context  │  │ Arch.    │  │ Workflows│  │ & Gate   │  │
│  │          │  │          │  │          │  │          │  │
│  │ CI sys   │  │ state    │  │ PR plan  │  │ policy   │  │
│  │ cloud    │  │ identity │  │ merge    │  │ approval │  │
│  │ envs     │  │ isolation│  │ deploy   │  │ drift    │  │
│  │ layout   │  │ OIDC     │  │ YAML     │  │ runbook  │  │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘  │
│                                                            │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Implementation checklist · Operational runbook     │   │
│  └─────────────────────────────────────────────────────┘   │
└────────────────────────────┬───────────────────────────────┘
                             ▼
                  ┌────────────────────┐
                  │  Pipeline          │
                  │  Blueprint         │
                  │  ✓ State isolation │
                  │  ✓ OIDC identity   │
                  │  ✓ CI workflows    │
                  │  ✓ Policy checks   │
                  │  ✓ Approval gates  │
                  │  ✓ Drift detection │
                  └────────────────────┘
```

</div>

<br>

| Step | What Happens |
|------|-------------|
| **Parse Context** | Captures CI system, cloud, environments, repo layout, security requirements |
| **Design Architecture** | State isolation, least-privilege IAM, OIDC federation, environment boundaries |
| **Generate Workflows** | Complete CI YAML — PR validation, merge deploy, drift detection |
| **Harden & Gate** | Policy-as-code, security scanning, approval gates, concurrency controls |
| **Checklist** | Every resource, secret, and config needed before the pipeline works |
| **Runbook** | State lock recovery, failed apply rollback, emergency procedures |

<br>

---

<br>

## Quick Start

**1.** Copy [`PROMPT.md`](./PROMPT.md) into a new AI conversation.

**2.** Provide your infrastructure context (CI system, cloud, environments, repo layout).

**3.** Get a complete pipeline blueprint with working CI YAML. Implement it.

<br>

---

<br>

## What You Get

```
┌──────────────────────────────────────────────────────────┐
│  PIPELINE BLUEPRINT                                      │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  ■ Assumptions & Defaults                                │
│    Documented decisions for every "unsure" input         │
│                                                          │
│  ■ State & Environment Isolation                         │
│    Per-stack, per-env state with locking                 │
│                                                          │
│  ■ Identity & IAM Model                                  │
│    OIDC roles for plan (read) and apply (write)          │
│                                                          │
│  ■ CI Workflow YAML                                      │
│    PR pipeline + merge/deploy pipeline + drift cron      │
│                                                          │
│  ■ Guardrails & Policy Checks                            │
│    tflint, checkov/tfsec, OPA/Sentinel, cost gates       │
│                                                          │
│  ■ Approval & Promotion Flow                             │
│    Auto dev/stage, gated prod with audit trail           │
│                                                          │
│  ■ Drift Detection                                       │
│    Scheduled plan, alert-only, never auto-remediate      │
│                                                          │
│  ■ Operational Runbook                                   │
│    Lock recovery, rollback, emergency apply              │
│                                                          │
│  ■ Implementation Checklist                              │
│    Every resource to provision before go-live             │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Domains

| Domain | Coverage |
|--------|----------|
| **SDLC Automation** | CI/CD pipeline design, workflow generation, promotion flows |
| **DevOps** | Infrastructure delivery, environment management, drift detection |
| **QA** | Policy-as-code, security scanning, pre-apply validation |
| **Security** | OIDC federation, least-privilege IAM, secrets management |
| **Platform Engineering** | State architecture, multi-stack isolation, operational runbooks |

<br>

---

<br>

## Examples

| Describe this | Get a pipeline for |
|--------------|-------------------|
| AWS + GitHub Actions mono-repo | Path-filtered matrix workflows, OIDC roles, S3 state |
| GCP + GitLab multi-repo | Per-repo pipelines, Workload Identity, GCS state |
| Azure + Azure DevOps | Service connections, Azure Blob state, environment gates |
| Multi-cloud mono-repo | Separate identity chains per provider, shared workflow structure |
| Existing pipeline with no gates | Hardened version with policy, approvals, and drift detection |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────┐
│                                                            │
│  CI: GitHub Actions                                        │
│  Cloud: AWS                                                │
│  Envs: dev, stage, prod                                    │
│  Repo: mono-repo (networking + compute stacks)             │
│  State: S3 + DynamoDB                                      │
│  Auth: OIDC                                                │
│  Apply: auto dev/stage, gated prod                         │
│                                                            │
└────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─ PIPELINE ARCHITECT ──────────────────────────────────────┐
│                                                            │
│  State Isolation                                           │
│    ✓ tfstate-dev / tfstate-stage / tfstate-prod            │
│    ✓ per-stack keys: networking/ , compute/                 │
│    ✓ DynamoDB lock tables per environment                  │
│                                                            │
│  Identity Model                                            │
│    ✓ tf-plan-ro    — read-only, OIDC, PR branches          │
│    ✓ tf-apply-dev  — scoped write, OIDC, main branch       │
│    ✓ tf-apply-prod — scoped write, OIDC, env protection    │
│                                                            │
│  Workflows                                                 │
│    ✓ PR: fmt → validate → tflint → checkov → plan → comment│
│    ✓ Merge: plan → apply dev → apply stage                 │
│    ✓ Prod: approval gate → apply prod                      │
│    ✓ Drift: nightly plan, Slack alert on changes           │
│                                                            │
│  Checklist: 12 items to provision before go-live           │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Start with "unsure."** Don't know which state backend to use? Say so. The Architect picks the right default and explains why.

**Include your compliance requirements.** SOC 2, HIPAA, FedRAMP — mentioning them triggers stricter isolation and audit patterns.

**Bring your existing YAML.** Say "here's our current pipeline" — it identifies gaps and hardens what you have.

**One repo context at a time.** Mono-repo and multi-repo produce fundamentally different designs. Be specific.

**Read the checklist last.** The implementation checklist is your deployment punch list. Nothing should be left implicit.

<br>

---

<br>

## File Structure

```
terraform-ci-cd-pipeline-architect/
├── SPEC.md      # Design document — the blueprint
├── PROMPT.md    # The finished prompt — paste and use
├── README.md    # You are here
└── POST.md      # LinkedIn post announcing this tool
```

<br>

## Contributing

1. Fork the repository
2. Add CI system support or security patterns
3. Test with 3-5 real infrastructure contexts
4. Verify generated workflows are syntactically valid
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../../../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Terraform CI/CD Pipeline Architect**

Infrastructure delivery that's gated, auditable, and boring.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox - VDD: Voice Driven Development

</div>
