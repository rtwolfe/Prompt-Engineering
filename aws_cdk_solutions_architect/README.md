<div align="center">

# AWS CDK Solutions Architect

### Design, validate, and evolve AWS CDK architectures with production-grade rigor.

Architectural goals in. Well-Architected CDK designs out.

<br>

![Domain](https://img.shields.io/badge/Cloud%20Architecture-blue?style=for-the-badge)
![SDLC Automation](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
Requirements + Constraints  →  CDK Architect  →  Architecture + CDK Skeleton
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

AWS CDK makes infrastructure-as-code approachable. But approachable doesn't mean well-architected. Teams adopt CDK and immediately hit the same problems: **monolithic stacks, wildcard IAM, no deployment strategy, and constructs chosen by copy-paste instead of intent**.

**AWS CDK Solutions Architect** is the architectural review layer. Give it your requirements and constraints, and it produces a **structured, Well-Architected CDK design** — with explicit construct choices, stack decomposition, security models, deployment strategy, and cost/scalability tradeoffs.

> You don't guess at stack boundaries. You describe your system. The Architect designs your infrastructure.

<br>

### Why This Exists

| Without the Architect | With the Architect |
|---|---|
| Hand-written CloudFormation or copy-pasted CDK | Opinionated CDK architecture with construct-level justifications |
| Inconsistent stacks, no decomposition strategy | Stateful/stateless separation, minimal cross-stack references |
| Security gaps, wildcard IAM | Least-privilege by default, scoped to specific actions and resources |
| "We'll figure out deployment later" | Multi-account pipeline with stage gates from day one |
| No Well-Architected review until audit | Every design validated against all six pillars |
| CDK v1 patterns lingering in the codebase | CDK v2 only, no deprecated services or patterns |

<br>

---

<br>

## How It Works

<div align="center">

```
                      ┌───────────────────────────────────┐
                      │                                   │
                      │   AWS CDK SOLUTIONS               │
                      │   ARCHITECT                       │
                      │                                   │
                      │   ┌───────────────────────────┐   │
 ┌──────────────┐     │   │  1. Parse requirements     │   │     ┌──────────────────┐
 │ Requirements │────▶│   │  2. Map to constructs      │   │────▶│ CDK Architecture │
 │ + Constraints│     │   │  3. Decompose stacks       │   │     │                  │
 │              │     │   │  4. Design deployment      │   │     │ ■ Stack design   │
 │ "serverless  │     │   │  5. Validate Well-Arch     │   │     │ ■ IAM model     │
 │  SaaS, multi │     │   │  6. Produce skeleton       │   │     │ ■ Deploy strat  │
 │  account"    │     │   └───────────────────────────┘   │     │ ■ CDK skeleton  │
 └──────────────┘     │                                   │     └──────────────────┘
                      └───────────────────────────────────┘
```

</div>

<br>

**The workflow:**

| Step | What You Do | What You Get |
|------|------------|--------------|
| **1. Provide inputs** | Architectural goal + AWS services + constraints | — |
| **2. Run the Architect** | Paste the prompt. Provide your inputs. | A structured CDK architecture document. |
| **3. Build** | Hand the architecture to your platform team. | A Well-Architected, deployable CDK codebase. |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`aws_cdk_solutions_architect.md`](./aws_cdk_solutions_architect.md) into a Claude or ChatGPT conversation.

### 2. Provide your inputs

```
We need an AWS CDK design for a serverless SaaS backend.
- API Gateway + Lambda
- DynamoDB for tenant data
- Multi-account (dev/stage/prod)
- Must support least-privilege IAM and blue/green deployments
- CDK v2, TypeScript
```

### 3. Receive your architecture

A 8-section architecture document — stack decomposition, construct choices, security model, deployment strategy, and CDK code skeleton.

### 4. Build

Each stack deploys independently. Start with the data layer. Add compute and API on top. Wire the pipeline last.

<br>

---

<br>

## What You Get

```
┌────────────────────────────────────────────────────────────┐
│  CDK ARCHITECTURE DOCUMENT                                  │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ■ Assumptions           Defaults applied, listed upfront  │
│  ■ Architecture Overview System topology and service map   │
│                                                            │
│  ■ Stack & Construct     Decomposition, construct levels,  │
│    Design                justifications                    │
│  ■ Environment &         Accounts, stages, pipeline,       │
│    Deployment            blue/green strategy                │
│                                                            │
│  ■ Security & IAM        Least-privilege roles, resource   │
│                          policies, encryption              │
│  ■ Scalability &         Auto-scaling, failover,           │
│    Reliability           capacity planning                 │
│  ■ Cost & Operational    Pricing models, observability     │
│    Tradeoffs             requirements                      │
│                                                            │
│  ■ CDK Skeleton          TypeScript code illustrating      │
│                          stack structure and constructs     │
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
                    │  CLOUD            │
                    │  ARCHITECTURE     │
                    │  (primary)        │
                    │                   │
                    └────────┬──────────┘
                             │
             ┌───────────────┼───────────────┐
             │               │               │
      ┌──────▼──────┐ ┌─────▼──────┐ ┌──────▼─────┐
      │             │ │            │ │            │
      │  SDLC       │ │  AWS CDK   │ │  DevOps    │
      │  Automation │ │  & IaC     │ │  & Ops     │
      │             │ │            │ │            │
      └─────────────┘ └────────────┘ └────────────┘
```

</div>

<br>

| Domain | What the Architect Covers |
|--------|--------------------------|
| **Cloud Architecture** | Service selection, stack decomposition, Well-Architected validation, tradeoff analysis |
| **SDLC Automation** | CDK Pipelines, multi-account deployment, stage promotion gates, blue/green strategy |
| **AWS CDK & IaC** | Construct level selection (L1/L2/L3), cross-stack patterns, CDK v2 best practices |
| **DevOps & Ops** | Observability, CloudWatch/X-Ray integration, cost tracking, operational readiness |

<br>

---

<br>

## Examples

### What You Can Design

| Use Case | Key Stacks | Key Decision |
|----------|-----------|--------------|
| Serverless SaaS backend | DataStack, ApiStack, PipelineStack | DynamoDB on-demand + per-tenant partition keys |
| Container microservices | NetworkStack, EcsStack, ServiceStack | ECS Fargate + ALB with path-based routing |
| Event-driven pipeline | IngestStack, ProcessStack, StorageStack | EventBridge + Step Functions over direct Lambda chains |
| Static site + API | CdnStack, ApiStack, AuthStack | CloudFront + S3 origin with Cognito authorizer |
| Data lake ingestion | LandingStack, ProcessStack, CatalogStack | S3 lifecycle policies + Glue catalog over custom ETL |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  Serverless SaaS backend                                           │
│  API Gateway + Lambda + DynamoDB                                   │
│  Multi-account (dev/stage/prod)                                    │
│  Least-privilege IAM, blue/green deployments                       │
│  CDK v2, TypeScript                                                │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ CDK ARCHITECT ──────────────────────────────────────────────────┐
│                                                                    │
│  Stack Decomposition:                                              │
│  ■ DataStack      DynamoDB (stateful, independent deploy)         │
│  ■ ApiStack       API Gateway + Lambda (stateless, fast iterate)  │
│  ■ PipelineStack  CDK Pipelines, cross-account with approvals     │
│                                                                    │
│  Construct Choices:                                                │
│  ■ dynamodb.Table (L2)    — on-demand, point-in-time recovery    │
│  ■ LambdaRestApi (L3)     — API-Lambda integration pattern       │
│  ■ lambda.Function (L2)   — Node.js 20.x runtime                │
│                                                                    │
│  Security:                                                         │
│  ■ grantReadWriteData() — scoped IAM, no wildcards               │
│  ■ Cognito or IAM authorizer on API Gateway                       │
│  ■ AWS-managed encryption on DynamoDB                             │
│                                                                    │
│  Deploy: CDK Pipelines → dev → stage → [approval] → prod         │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Start with constraints, not services.**
The Architect selects constructs based on your requirements. Don't pre-decide L1 vs L2 — describe what you need and let the mapping do the work.

**Separate stateful from stateless.**
The most common CDK mistake is putting DynamoDB tables and Lambda functions in the same stack. Stateful resources have different deployment lifecycles. Separate them.

**Specify your account model.**
Single-account vs. multi-account is the highest-impact architectural decision. Without this input, the Architect uses conservative multi-account defaults that may be more structure than you need.

**Don't skip the IAM review.**
The architecture output scopes every IAM role to specific actions and resources. If you see a wildcard in your own code that contradicts the design, fix the code.

**Iterate on the design.**
The first output is a starting point. Add compliance constraints, change the deployment model, adjust cost targets. Each iteration sharpens the architecture.

<br>

---

<br>

## File Structure

```
prompts/examples/aws-cdk-solutions-architect/
├── aws_cdk_solutions_architect.md  # The prompt (paste this into AI)
├── README.md     # You are here
├── POST.md       # LinkedIn post
└── SPEC.md       # Original build specification
```

<br>

## Contributing

1. Fork the repository
2. Add support for new AWS service patterns or CDK construct recommendations
3. Test with 3-5 different architectural scenarios across complexity levels
4. Verify architecture outputs cover all 8 sections
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**AWS CDK Solutions Architect**

CDK makes infrastructure approachable. This makes it well-architected.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
