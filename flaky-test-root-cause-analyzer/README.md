<div align="center">

# Flaky Test Root Cause Analyzer

### Stop chasing phantom failures — instant root cause classification for every flaky test.

<br>

![Domain](https://img.shields.io/badge/QA%20Automation-blue?style=for-the-badge)
![SDLC](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
Test failure in  →  Root cause + confidence + fix  →  Triage decision out
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips)

</div>

<br>

---

<br>

## Overview

"Is it real or flaky?"

Five words. Forty-five minutes of investigation. The answer is usually "flaky." Google found that 84% of test-to-failure transitions were caused by flakiness, not actual regressions. Microsoft estimates flaky tests cost $1.14 million annually in developer time. The problem isn't fixing flaky tests — it's knowing which failures deserve investigation.

**Flaky Test Root Cause Analyzer** takes raw test failure data — error messages, stack traces, execution history, environment context — and classifies every failure into an actionable root cause category with confidence scoring, specific remediation code, and a deployment triage decision.

> You don't investigate the failure. You paste it. The analyzer tells you what it is, why it happened, and exactly how to fix it.

<br>

### Without vs. With

| Without the Analyzer | With the Analyzer |
|---|---|
| 45 minutes investigating a failure that turns out to be timing | 2-minute triage with clear root cause and fix |
| "Is this real or flaky?" debate in Slack | Decisive classification with confidence score |
| Developers ignore test failures because "probably flaky" | Every failure gets actionable owner routing |
| Same flaky test wastes 10 hours/month across the team | One-time root cause fix eliminates the pattern |
| QA blamed for "unreliable tests" with no diagnostic data | Evidence-backed analysis shifts conversation to solutions |

<br>

---

<br>

## How It Works

<div align="center">

```
┌─────────────────┐     ┌─────────────────────────┐     ┌──────────────────────┐
│  FAILURE INPUT  │     │   ROOT CAUSE ANALYZER   │     │    TRIAGE OUTPUT     │
│                 │     │                         │     │                      │
│ • Error message │────▶│ 1. Parse failure type   │────▶│ • Category + %conf   │
│ • Stack trace   │     │ 2. Match known patterns │     │ • Evidence summary   │
│ • Exec history  │     │ 3. Analyze history      │     │ • Remediation code   │
│ • Environment   │     │ 4. Correlate failures   │     │ • Block deployment?  │
│ • Related fails │     │ 5. Score confidence     │     │ • Owner + Priority   │
└─────────────────┘     └─────────────────────────┘     └──────────────────────┘
```

</div>

<br>

**The analysis pipeline:**

| Step | What Happens |
|------|-------------|
| **1. Parse** | Extract error type, message, stack trace, framework, timing data from raw CI output |
| **2. Classify** | Match error signature against 50+ known flakiness patterns (timeouts, state errors, resource exhaustion) |
| **3. Analyze** | Calculate pass/fail ratio, detect intermittency, identify time and environment correlations |
| **4. Correlate** | Cross-reference related failures in the same run to distinguish systemic vs. isolated issues |
| **5. Score** | Weight all evidence to produce calibrated confidence — never claims high confidence without sufficient data |
| **6. Remediate** | Generate framework-specific fix with code examples, not generic advice |
| **7. Triage** | Output deployment decision, owner routing, and priority |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`flaky-test-root-cause-analyzer.md`](./flaky-test-root-cause-analyzer.md) into a new Claude or ChatGPT conversation.

### 2. Paste your failure

```
TEST: test_checkout_flow_completes_successfully

FAILURE OUTPUT:
TimeoutError: locator.click: Timeout 30000ms exceeded.
Call log:
  - waiting for locator('[data-testid="submit-order-btn"]')
  - element is not enabled - waiting...

EXECUTION HISTORY:
- Run #142: PASSED (34.2s)
- Run #141: FAILED (timeout)
- Run #140: PASSED (31.8s)
- Run #139: PASSED (33.1s)
- Run #138: FAILED (timeout)

ENVIRONMENT:
- CI: GitHub Actions, 4 parallel workers
- Browser: Chromium 121.0
```

### 3. Get your answer

A structured analysis report with root cause category, confidence score, evidence, remediation code, and triage decision.

<br>

---

<br>

## What You Get

```
┌──────────────────────────────────────────────────────┐
│  ROOT CAUSE ANALYSIS REPORT                          │
├──────────────────────────────────────────────────────┤
│                                                      │
│  ■ Classification     Category + confidence %        │
│  ■ Evidence           Specific citations from input  │
│  ■ Explanation        WHY this classification        │
│  ■ Remediation        Code examples + config fixes   │
│  ■ Triage             Block deploy? Owner? Priority? │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**Seven root cause categories:**

| Category | What It Means |
|---|---|
| `GENUINE_BUG` | Real application defect — consistent failure on business logic |
| `TIMING_RACE_CONDITION` | Async operation completes inconsistently — needs explicit waits |
| `ENVIRONMENT_INSTABILITY` | CI resource contention, container issues, network flakiness |
| `TEST_CODE_DEFECT` | Stale locators, bad isolation, hardcoded waits, missing setup/teardown |
| `DATA_DEPENDENCY` | Test relies on specific data state, fixture issues, order sensitivity |
| `EXTERNAL_SERVICE` | Third-party API timeout, network-dependent operation |
| `INFRASTRUCTURE` | Pod eviction, OOM kill, disk pressure, scheduler issues |

<br>

---

<br>

## Domains

| Domain | How This Helps |
|---|---|
| **QA Automation** | Instant root cause classification for any test framework — Playwright, Cypress, Selenium, Jest, pytest, JUnit |
| **SDLC Automation** | Transforms CI/CD pipeline noise into actionable signals with owner routing |
| **DevOps** | Separates infrastructure failures from test failures — routes to the right team |
| **Platform Engineering** | Data-driven flakiness management with confidence scoring and priority |

<br>

---

<br>

## Examples

### Timing Race Condition

```
┌─ INPUT ──────────────────────────────────────────────────────────┐
│                                                                   │
│  TEST: test_user_can_apply_discount_code                         │
│  ERROR: Element not found — discount confirmation not visible     │
│  HISTORY: 7/10 passed, 3 timeouts, no code changes              │
│  ENV: GitHub Actions, Playwright 1.40, 2 parallel workers        │
│                                                                   │
└──────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ OUTPUT ─────────────────────────────────────────────────────────┐
│                                                                   │
│  Category: TIMING_RACE_CONDITION — 85% confidence                │
│                                                                   │
│  Evidence: Intermittent pattern (70% pass rate), timeout          │
│  signatures on prior failures, element missing vs. wrong          │
│  content, no related failures                                     │
│                                                                   │
│  Fix: Replace implicit wait with explicit element-targeted wait   │
│                                                                   │
│    await expect(page.locator('.discount-confirmation'))           │
│      .toContainText('Your discount:', { timeout: 15000 });       │
│                                                                   │
│  Triage: Don't block deployment. QA owns. P3-Medium.             │
│                                                                   │
└──────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**More context = higher confidence.**
Error message alone caps at 60% confidence. Add execution history, environment details, and related failures to unlock high-confidence classification.

**Paste raw CI output.**
No formatting needed. The analyzer parses GitHub Actions logs, Jenkins output, pytest traces, and JUnit XML directly.

**Include related failures.**
If three tests failed in the same run, that's a systemic signal. A single failure in isolation might be flakiness; three failures with the same error type points to infrastructure.

**Use for triage, not just diagnosis.**
The deployment blocking decision and owner routing turns this from a debugging tool into a pipeline automation component.

**Build a flakiness playbook.**
Run your top 10 flaky tests through the analyzer. The remediation patterns will reveal systemic issues in your test architecture — not just individual fixes.

<br>

---

<br>

## File Structure

```
flaky-test-root-cause-analyzer/
├── flaky-test-root-cause-analyzer.md   # The prompt (paste this into AI)
├── README.md    # You are here
├── SPEC.md      # Full specification
```

<br>

## Contributing

1. Fork the repository
2. Add new flakiness pattern signatures to the classification step
3. Test with real CI failure output from your framework
4. Verify the analyzer produces actionable, specific remediation
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Flaky Test Root Cause Analyzer**

Stop chasing phantom failures. Start fixing root causes.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by **Vox** — VDD: Voice Driven Development

</div>
