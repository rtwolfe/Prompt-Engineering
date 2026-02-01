<div align="center">

# SynthForge — Synthetic Test Data Generator

### Schema-aware synthetic datasets with referential integrity, on demand.

Generate privacy-safe, production-realistic test data from any database schema, API contract, or data model description — with configurable volume, edge cases, and domain-specific patterns.

<br>

![Domain](https://img.shields.io/badge/SDLC_Automation-2B5797?style=for-the-badge)
![SDLC](https://img.shields.io/badge/QA_%7C_DevOps-1A7F37?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI_Powered-FF6F00?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

</div>

<br>

---

<br>

```
  schema in  ──▶  SynthForge  ──▶  synthetic dataset out
```

<br>

---

<br>

<div align="center">

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [Output Format](#output-format) · [Examples](#examples) · [Supported Domains](#supported-domains) · [Pro Tips](#pro-tips) · [File Structure](#file-structure) · [Contributing](#contributing) · [License](#license)

</div>

<br>

---

<br>

## Overview

Test data provisioning is one of the most persistent bottlenecks in modern software delivery. SynthForge eliminates it.

| Without SynthForge | With SynthForge |
|---|---|
| Testers spend 30-50% of their time hand-building test data in spreadsheets | Schema in, production-realistic dataset out, in seconds |
| Cloning production data risks GDPR/CCPA violations and $5.88B+ in cumulative fines | Every record is synthetic — zero PII, zero liability |
| Manual datasets miss edge cases; bugs escape to production | Configurable edge case injection with constraint-safe boundary testing |
| Foreign key mismatches cause INSERT failures and broken test environments | Referential integrity enforced across every parent-child relationship |
| Data provisioning delays stall CI/CD pipelines for days or weeks | On-demand generation fits into any pipeline stage |

<br>

---

<br>

## How It Works

```
┌──────────────────┐    ┌──────────────┐    ┌─────────────────────┐
│ Schema / DDL /   │───▶│  SynthForge  │───▶│ Synthetic Dataset   │
│ API Contract     │    │              │    │ (JSON/CSV/SQL)      │
└──────────────────┘    │  ┌────────┐  │    └─────────────────────┘
┌──────────────────┐    │  │Analyze │  │    ┌─────────────────────┐
│ Config: volume,  │───▶│  │Plan    │  │───▶│ Validation Report   │
│ edges, domain,   │    │  │Generate│  │    │ (integrity proof)   │
│ locale, seed     │    │  │Validate│  │    └─────────────────────┘
└──────────────────┘    │  └────────┘  │
                        └──────────────┘
```

<br>

| Stage | What Happens |
|---|---|
| **Analyze** | Parses the schema, extracts tables, columns, types, constraints, foreign keys, and relationships. Maps dependencies into a directed acyclic graph. Flags ambiguities and states assumptions. |
| **Plan** | Declares exact record counts, cardinality distributions, edge case injection targets, domain patterns, and seed constraint fulfillment strategy. Published for user review before generation. |
| **Generate** | Produces records in dependency order (parents first). Enforces referential integrity, constraint compliance, domain-contextual realism, and privacy safety for every field of every record. |
| **Validate** | Self-audits the output: verifies record counts, foreign key resolution, CHECK/UNIQUE/NOT NULL compliance, seed constraint fulfillment, and edge case presence. Reports all findings. |

<br>

---

<br>

## Quick Start

**1. Fastest: Use the Quickstart Form**

Open `QUICKSTART.html` in your browser. Fill in the form with your schema and configuration options. Click generate. Copy the assembled prompt and paste it into any LLM conversation.

**2. Manual: Copy the Prompt**

Copy the contents of `synthetic-test-data-generator.md` into any LLM conversation (ChatGPT, Claude, Gemini, etc.). Provide your schema and configuration directly in the chat:

```
Schema:
<paste your SQL DDL, JSON Schema, OpenAPI contract, or plain-English description>

Output format: SQL INSERT
Volume: 10 customers, 30 orders
Domain: e-commerce
Edge case profile: moderate
Locale: en-US
Seed constraints: Include at least one cancelled order with a refund.
```

<br>

---

<br>

## Output Format

SynthForge returns a structured four-section package:

```
┌─────────────────────────────────────────────┐
│  1. Schema Analysis                         │
│     Tables, columns, types, constraints,    │
│     relationships, assumptions              │
├─────────────────────────────────────────────┤
│  2. Generation Plan                         │
│     Record counts, cardinalities, edge      │
│     case targets, seed constraint strategy  │
├─────────────────────────────────────────────┤
│  3. Generated Data                          │
│     Complete synthetic dataset in your      │
│     chosen format (JSON / CSV / SQL INSERT) │
├─────────────────────────────────────────────┤
│  4. Validation Summary                      │
│     Record counts, FK integrity, constraint │
│     compliance, edge case log, seed proof   │
└─────────────────────────────────────────────┘
```

Supported output formats: **JSON**, **CSV**, and **SQL INSERT**. All outputs are copy-paste ready — SQL executes as-is, JSON parses without errors, CSV imports cleanly into standard tools.

<br>

---

<br>

## Examples

| Input Type | What SynthForge Produces |
|---|---|
| SQL DDL (CREATE TABLE statements) | Fully typed records with constraint compliance, FK resolution, and inline edge case annotations |
| JSON Schema (with $ref relationships) | Nested or flat JSON arrays with proper null/boolean/number types and `_metadata` on edge case records |
| OpenAPI / Swagger contract | Request/response payloads populated with realistic, schema-valid synthetic values |
| Plain-English data model | Inferred schema presented for confirmation, then full dataset generation with stated assumptions |
| MongoDB collection schema | BSON-typed documents with embedded sub-documents and array fields |

<br>

**Live Example:**

```
┌─────────────────────────────┐        ┌──────────────────────────────────────┐
│ INPUT                       │        │ OUTPUT                               │
│                             │        │                                      │
│ CREATE TABLE customers (    │        │ INSERT INTO customers VALUES         │
│   customer_id UUID PK,     │        │   ('a1b2...', 'jane@testmail.synth', │
│   email VARCHAR UNIQUE,    │───▶    │    'Jane Moreno', '1988-03-14',      │
│   membership_tier ...       │        │    'gold', NOW(), true);             │
│ );                          │        │                                      │
│                             │        │ -- edge: NULL date_of_birth          │
│ Volume: 8 customers         │        │ INSERT INTO customers VALUES         │
│ Edge cases: moderate        │        │   ('c3d4...', 'karl@example.com',   │
│ Domain: e-commerce          │        │    'Karl Svensson', NULL, ...);      │
└─────────────────────────────┘        └──────────────────────────────────────┘
```

<br>

---

<br>

## Supported Domains

| Domain | What It Produces |
|---|---|
| **Financial** | Realistic transaction amounts, proper currency formatting, temporal clustering around business hours, synthetic account numbers |
| **Healthcare** | Synthetic patient demographics, valid-format diagnosis codes, clinically plausible date ranges, privacy-safe medical records |
| **E-commerce** | Realistic product names, right-skewed price distributions, order status funnel progression, shipping address patterns |
| **SaaS** | User accounts, subscription tiers, usage metrics, billing cycles, feature flag states, API key formats |
| **Logistics** | Shipment tracking numbers, warehouse codes, route data, delivery timestamps, carrier assignments |
| **Education** | Student records, course enrollments, grade distributions, academic calendars, transcript data |
| **General** | Domain inferred from schema field names; sensible defaults applied with realistic variance across all fields |

<br>

---

<br>

## Pro Tips

**Start with your real schema.** Paste your actual CREATE TABLE statements or JSON Schema directly. The more constraints SynthForge can see (CHECK, UNIQUE, NOT NULL, FOREIGN KEY), the more accurate and useful the output.

**Use seed constraints for specific test scenarios.** Need to test a refund flow? Add `"Include at least one cancelled order with a refund."` SynthForge will plan around your constraints and verify fulfillment in the validation summary.

**Set the edge case profile to match your test phase.** Use `minimal` for happy-path smoke tests, `moderate` for regression suites, and `aggressive` for hardening and penetration prep. Each level stays within schema constraints — edge cases never break validity.

**Specify volume ratios for realistic cardinalities.** Instead of flat counts, use ratios like `"1 customer : 5 orders : 15 line items"` to get realistic parent-child distributions that mirror production patterns.

**Use deterministic seeds for reproducible test runs.** Set `seed: 42` (or any integer) to get identical output across repeated runs — essential for CI/CD pipelines where test stability matters.

**Leverage the Generation Plan as a review checkpoint.** Section 2 publishes the full strategy before any data is produced. Use it to catch misunderstandings early — you can adjust the plan before committing to generation.

<br>

---

<br>

## File Structure

```
synthforge/
├── SPEC.md                                        # Prompt specification document
├── synthetic-test-data-generator.md    # The prompt (copy into any LLM)
├── README.md                                      # This file
├── POST.md                                        # Social media post copy
└── QUICKSTART.html                                # Interactive form for assembling the prompt
```

<br>

---

<br>

## Contributing

Contributions are welcome. To get started:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/your-feature`)
3. **Commit** your changes (`git commit -m "Add your feature"`)
4. **Push** to the branch (`git push origin feature/your-feature`)
5. **Open** a Pull Request

<br>

---

<br>

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

<br>

---

<br>

<div align="center">

# SynthForge

**Schema-aware synthetic datasets with referential integrity, on demand.**

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

*Powered by Vox - VDD: Voice Driven Development*

</div>
