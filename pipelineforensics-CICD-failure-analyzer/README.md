<div align="center">

# PipelineForensics

### Turn raw CI/CD failure logs into structured root cause diagnoses with classified fixes and flakiness scores.

<br>

![Domain](https://img.shields.io/badge/DevOps%20%2F%20QA-blue?style=for-the-badge)
![SDLC](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
CI/CD Failure Log  →  Structured forensic report (root cause + fix + flakiness score)
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

Every CI/CD pipeline failure triggers the same costly ritual: an engineer stops feature work, opens a log viewer, scrolls through hundreds of lines of noisy output, cross-references diffs and environment configs, and eventually — 30 to 90 minutes later — identifies why the build broke. Multiply that by multiple-times-daily frequency, and the waste is staggering.

**PipelineForensics** eliminates the manual log archaeology phase entirely. Paste a failure log, get back a structured forensic report: classified root cause with evidence, confidence-scored flakiness assessment, actionable fix with implementation specifics, and blast radius analysis showing downstream impact.

> You don't scroll through 2,000 log lines. You paste the failure. It tells you what broke, why, and exactly how to fix it.

<br>

### Why This Exists

| Without PipelineForensics | With PipelineForensics |
|---|---|
| Scroll 2,000 log lines hunting for the real error | Structured forensic report with root cause in seconds |
| "Is this flaky or did I break something?" — guess and rerun | Flakiness score (0–10) with evidence-backed justification |
| Generic advice: "check your dependencies" | Specific fix: exact file, exact line, exact code change |
| Failures block the team while one person investigates | Blast radius analysis so unblocked work continues |
| Same failure class recurs next month | Targeted prevention measures for this specific failure pattern |

<br>

---

<br>

## How It Works

<div align="center">

```
┌──────────────────────┐     ┌──────────────────────────┐     ┌──────────────────────────────┐
│   FAILURE LOG        │     │   PipelineForensics      │     │   FORENSIC REPORT            │
│   (raw CI output)    │────>│                          │────>│                              │
│                      │     │   Parse → Classify →     │     │   Root Cause + Evidence      │
│   + Code Diff        │────>│   Correlate → Score →    │────>│   Flakiness Score            │
│   (optional)         │     │   Fix → Prevent          │     │   Actionable Fix (code)      │
│                      │     │                          │     │   Blast Radius               │
│   + Env Metadata     │────>│                          │────>│   Prevention Measures         │
│   (optional)         │     │                          │     │                              │
└──────────────────────┘     └──────────────────────────┘     └──────────────────────────────┘
```

</div>

<br>

**The pipeline:**

| Step | Input | Output |
|------|-------|--------|
| **1. Parse & Triage** | Raw failure log | Error boundary, stack traces, exit codes (noise filtered) |
| **2. Classify** | Error signals + root cause taxonomy | Category + confidence level + evidence chain |
| **3. Correlate** | Classification + diff + env metadata | Causal chain from code changes to failure |
| **4. Score** | Failure characteristics | Flakiness score (0–10) with indicators |
| **5. Fix** | Root cause + correlation | Specific code/config/command remediation |
| **6. Assess** | Fix + pipeline structure | Blast radius + prevention measures |

<br>

---

<br>

## Quick Start

### Option A: Form-first (recommended)

1. Open [`QUICKSTART.html`](./QUICKSTART.html) in your browser
2. Fill in your pipeline platform, paste your failure log, add optional context
3. Click **Generate Prompt** to assemble the configured prompt
4. Copy to clipboard and paste into a new Claude conversation
5. Receive your forensic report

### Option B: Direct prompt

1. Copy [`pipelineforensics-CICD-failure-analyzer.md`](./pipelineforensics-CICD-failure-analyzer.md) into a new Claude conversation
2. Paste your failure log with the platform name
3. Optionally include the code diff, environment metadata, and pipeline config
4. Receive your forensic report

<br>

---

<br>

## What You Get

<div align="center">

```
┌──────────────────────────────────────────────────────────┐
│  FAILURE FORENSIC REPORT                                  │
├──────────────────────────────────────────────────────────┤
│                                                           │
│  ■ Failure Summary      What failed, when, at what       │
│                         pipeline stage                    │
│                                                           │
│  ■ Root Cause           Classified against 12-category   │
│    Classification       taxonomy with confidence level   │
│                         and verbatim log evidence         │
│                                                           │
│  ■ Flakiness            Score (0-10) with specific       │
│    Assessment           indicators: timing, concurrency, │
│                         shared state, network calls       │
│                                                           │
│  ■ Actionable Fix       Exact code change, command, or   │
│                         config edit with file + line.     │
│                         Priority + effort estimate        │
│                                                           │
│  ■ Blast Radius         What's blocked, what proceeds,   │
│                         who's affected, urgency level     │
│                                                           │
│  ■ Prevention           1-3 targeted measures for this   │
│                         specific failure pattern          │
│                                                           │
└──────────────────────────────────────────────────────────┘
```

</div>

<br>

---

<br>

## Domains

| Domain | What Gets Diagnosed |
|--------|-------------------|
| **GitHub Actions** | Workflow failures, action errors, matrix job failures, OIDC/permissions issues |
| **GitLab CI/CD** | Pipeline stage failures, runner issues, artifact problems, DAG dependency errors |
| **Jenkins** | Freestyle and Pipeline job failures, Groovy errors, plugin conflicts, agent issues |
| **CircleCI** | Workflow failures, orb errors, resource class limits, caching failures |
| **Azure DevOps** | Pipeline task failures, agent pool issues, service connection errors |
| **Bitrise / Buildkite / Travis CI / TeamCity** | Platform-specific failures parsed with generic + platform-aware heuristics |

<br>

---

<br>

## Examples

### What You Can Diagnose

| Feed It | Get Back |
|---------|---------|
| Next.js build failure with API migration diff | Code Error: response shape mismatch, exact fix with null-safe fallback |
| Flaky E2E test that passes on retry | Flakiness Score 8/10: port conflict + shared state, isolation fix |
| `SIGKILL` with no stack trace | Infrastructure/Resource (Medium confidence): recommend verbose logging + memory limit check |
| 20-file diff with unrelated test failure | Explicit statement: diff not causally related, pre-existing environment issue |
| Jenkins pipeline timeout after 45 minutes | Timeout: specific step identified, resource adjustment + timeout config fix |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  PLATFORM: GitHub Actions                                         │
│                                                                    │
│  FAILURE LOG:                                                     │
│  2025-01-28T14:34:55Z TypeError: Cannot read properties of       │
│      undefined (reading 'map')                                    │
│    at getStaticPaths (src/pages/blog/[slug].tsx:24:38)            │
│                                                                    │
│  DIFF: getAllPosts() changed from /posts to /v2/posts,            │
│        return data -> return data.results                         │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ PIPELINEFORENSICS ──────────────────────────────────────────────┐
│                                                                    │
│  ROOT CAUSE: Code Error (High confidence)                         │
│  API response shape changed — data.results is undefined           │
│                                                                    │
│  FLAKINESS: 1/10 — deterministic TypeError, no env sensitivity    │
│                                                                    │
│  FIX: return data.results ?? []  // src/lib/api.ts:15             │
│  Priority: Immediate | Effort: Quick fix (<30 min)                │
│                                                                    │
│  BLAST RADIUS: All main branch deploys + all PR builds blocked    │
│                                                                    │
│  PREVENTION: Type guard in getStaticPaths, contract test for      │
│  /v2/posts response shape, header-based API versioning            │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Include the diff.**
The failure log alone gives you a root cause. Adding the code diff gives you the causal chain — which exact change triggered the break. Diff correlation is the difference between "this line failed" and "this line failed because you changed this function."

**Paste the full log, not a snippet.**
Truncated logs work, but full logs enable higher confidence scores and better noise filtering. The parser identifies the failure boundary automatically — you don't need to pre-trim.

**Add environment metadata for infrastructure failures.**
Runner OS, runtime versions, memory limits, Docker image tags. For "works on my machine" failures, environment context is the key diagnostic input.

**Use historical context for flakiness.**
"This test passed on the last 5 runs" or "this job has been flaky for two weeks" dramatically improves flakiness scoring accuracy. The prompt can distinguish a new regression from a recurring pattern.

**Run it on success logs to verify.**
If you paste a success log, PipelineForensics will tell you no failure was detected. Useful for confirming a fix actually resolved the issue rather than getting lucky with a flaky pass.

<br>

---

<br>

## File Structure

```
INTAKE/
├── SPEC.md                      # Prompt specification (source of truth)
├── pipelineforensics-CICD-failure-analyzer.md  # The prompt — paste into AI
├── README.md                    # You are here
├── POST.md                      # LinkedIn post
└── QUICKSTART.html              # Interactive intake form
```

<br>

## Contributing

1. Fork the repository
2. Add support for additional CI platforms or failure categories
3. Test with 3-5 real pipeline failure logs across platforms
4. Verify forensic reports are accurate and fixes are implementable
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**PipelineForensics**

One log. Six-section diagnosis. Back to building.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
