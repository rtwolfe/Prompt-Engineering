<div align="center">

# Human Behavior Meeting Analyst

### Surface the real dynamics behind every meeting.

Meeting transcripts in. Forensic behavioral intelligence out.

<br>

![Domain](https://img.shields.io/badge/Behavioral%20Intelligence-blue?style=for-the-badge)
![SDLC Automation](https://img.shields.io/badge/SDLC%20Automation-purple?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
Meeting Transcript + Context  →  Behavioral Intelligence Report
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

Meeting summaries tell you what was said. They don't tell you **who actually holds power, whether alignment is real or performative, or where decisions will silently fall apart**.

**Human Behavior Meeting Analyst** is the forensic intelligence layer. Give it a meeting transcript and it produces an **evidence-backed behavioral analysis** — with power maps, credibility signals, alignment integrity checks, decision audits, and organizational risk forecasts.

> You don't read transcripts and guess. You provide the data. The Analyst surfaces reality.

<br>

### Why This Exists

| Without the Analyst | With the Analyst |
|---|---|
| Read the transcript, assume alignment | Power map showing who actually drives decisions |
| "Everyone agreed" (silence = consent) | Alignment audit distinguishing explicit agreement from disengagement |
| No idea who's confident vs. credible | Credibility-confidence gap analysis with evidence |
| Problems surface weeks later | Risk forecast identifying failure modes before they compound |
| Facilitator gut feel | Evidence-grounded coaching recommendations |
| Meeting notes capture words | Behavioral profiles capture dynamics |

<br>

---

<br>

## How It Works

<div align="center">

```
                      ┌───────────────────────────────────┐
                      │                                   │
                      │   HUMAN BEHAVIOR                  │
                      │   MEETING ANALYST                 │
                      │                                   │
                      │   ┌───────────────────────────┐   │
 ┌──────────────┐     │   │  1. Data sufficiency gate  │   │     ┌──────────────────┐
 │  Transcript  │────▶│   │  2. Room mapping           │   │────▶│ Behavioral Intel │
 │  + Context   │     │   │  3. Power & influence      │   │     │                  │
 │              │     │   │  4. Linguistic signals      │   │     │ ■ Power map     │
 │ "sprint      │     │   │  5. Credibility check      │   │     │ ■ Profiles      │
 │  retro,      │     │   │  6. Alignment audit        │   │     │ ■ Risk forecast │
 │  5 people"   │     │   │  7. Risk forecast          │   │     │ ■ Coaching recs │
 └──────────────┘     │   └───────────────────────────┘   │     └──────────────────┘
                      │                                   │
                      └───────────────────────────────────┘
```

</div>

<br>

**The workflow:**

| Step | What You Do | What You Get |
|------|------------|--------------|
| **1. Provide inputs** | Meeting transcript + participant roles + meeting type | — |
| **2. Run the Analyst** | Paste the prompt. Provide your transcript. | A complete behavioral intelligence report. |
| **3. Act** | Hand the analysis to leadership or use it to improve facilitation. | Evidence-backed decisions about team dynamics. |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`human-behavior-meeting-analyst.md`](./human-behavior-meeting-analyst.md) into a Claude or ChatGPT conversation.

### 2. Provide your inputs

```
Here's the transcript from our sprint retrospective.
5 participants, 30 minutes.
Meeting type: Retrospective
I want to know who's actually driving decisions and whether
the team is genuinely aligned.

[paste transcript]
```

### 3. Receive your analysis

A 9-section behavioral intelligence report — power map, participant profiles, credibility signals, alignment audit, decision integrity check, risk forecast, and coaching recommendations.

### 4. Act

Use the power map to rebalance facilitation. Follow up on flagged non-decisions. Address marginalized participants before disengagement becomes attrition.

<br>

---

<br>

## What You Get

```
┌────────────────────────────────────────────────────────────┐
│  BEHAVIORAL INTELLIGENCE REPORT                             │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ■ Executive Snapshot     What's actually happening        │
│  ■ Room-Level Power Map   Who holds real influence         │
│  ■ Participant Profiles   Behavioral signals per person    │
│                                                            │
│  ■ Credibility Signals    Where claims exceed evidence     │
│  ■ Alignment Analysis     Real vs performative agreement   │
│  ■ Decision Integrity     Made, deferred, or phantom       │
│                                                            │
│  ■ Risk Forecast          Downstream failure modes         │
│  ■ Coaching Recs          Evidence-grounded next steps     │
│  ■ Confidence & Limits    What we could and couldn't see   │
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
                    │  BEHAVIORAL       │
                    │  INTELLIGENCE     │
                    │  (primary)        │
                    │                   │
                    └────────┬──────────┘
                             │
             ┌───────────────┼───────────────┐
             │               │               │
      ┌──────▼──────┐ ┌─────▼──────┐ ┌──────▼─────┐
      │             │ │            │ │            │
      │  Forensic   │ │  Org       │ │  Meeting   │
      │  Linguistics│ │  Behavior  │ │  Ops       │
      │             │ │            │ │            │
      └─────────────┘ └────────────┘ └────────────┘
```

</div>

<br>

| Domain | What the Analyst Covers |
|--------|------------------------|
| **Behavioral Intelligence** | Power dynamics, influence mapping, credibility-confidence gaps, marginalization detection |
| **Forensic Linguistics** | Hedging markers, self-correction events, filler clustering, response latency analysis |
| **Organizational Behavior** | Alignment integrity, decision audit, risk forecasting, team health signals |
| **Meeting Operations** | Facilitation coaching, room rebalancing, follow-up prioritization |

<br>

---

<br>

## Examples

### What You Can Analyze

| Meeting Type | Key Signals Surfaced | Key Risk Identified |
|-------------|---------------------|-------------------|
| Sprint retrospective | Power imbalance, silent disengagement | Implied decisions with no real alignment |
| Incident review | Narrative instability, hedging clusters | Accountability gaps masked by confident language |
| Executive planning | Formal vs. effective influence divergence | Strategic decisions driven by one voice, rubber-stamped by room |
| Hiring debrief | Credibility-confidence gaps in assessments | Groupthink — early strong opinion anchoring all subsequent feedback |
| Scrum standup | Topic avoidance, consistent over-reporting | Risk hiding — status language disconnected from delivery signals |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  Sprint retrospective transcript                                   │
│  5 participants, 30 minutes                                        │
│  "Who's driving decisions? Is alignment real?"                     │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ ANALYST ────────────────────────────────────────────────────────┐
│                                                                    │
│  Power Map:                                                        │
│  1. Marcus (Tech Lead)  — initiates 4/6 topics, addressed for     │
│     decisions, interrupts without yield                            │
│  2. Sarah (Scrum Master) — formal facilitator, yields topic       │
│     control on technical items                                     │
│  3. Devon (Senior Dev)   — supports Marcus, adds specificity      │
│  4. Priya (Dev)          — 3 turns total, all reactive            │
│  5. Jake (Dev)           — 1 turn, prompted, hedged               │
│                                                                    │
│  Decision Audit:                                                   │
│  ✓ Explicit: "Two-week sprints" — proposed Marcus, confirmed Sarah│
│  ⚠ Implied: "New testing approach" — silence treated as consent   │
│  ✗ Deferred: Code review process — raised, no resolution          │
│                                                                    │
│  Risk: 2 participants below 8% speaking time.                     │
│  Disengagement pattern suggests alignment is performative.         │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Provide audio markers if you have them.**
Pauses, filler words, and speech rate dramatically increase analysis confidence. Without them, the Analyst works with text-only signals and explicitly reduces confidence levels.

**Include participant roles.**
Formal role vs. effective influence is one of the most valuable signals. Without knowing who *should* have authority, the Analyst can only map who *does*.

**Ask specific behavioral questions.**
"Was someone bullshitting?" becomes a forensic analysis of hedging density, narrative stability, and confidence-evidence gaps. The sharper your question, the sharper the analysis.

**Use it for longitudinal tracking.**
Run the Analyst on consecutive meetings with the same team. Power dynamics and engagement patterns that are invisible in a single meeting become obvious across three.

**Trust the limitations section.**
The Analyst tells you what it *couldn't* assess. That section is as valuable as the findings — it tells you where you need better data.

<br>

---

<br>

## File Structure

```
prompts/examples/human-behavior-meeting-analyst/
├── human-behavior-meeting-analyst.md  # The prompt (paste this into AI)
├── README.md     # You are here
├── POST.md       # LinkedIn post
└── SPEC.md       # Original build specification
```

<br>

## Contributing

1. Fork the repository
2. Add support for new meeting types or behavioral signal categories
3. Test with 3-5 different meeting transcripts across formality levels
4. Verify analysis outputs are complete — all 9 sections present
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Human Behavior Meeting Analyst**

Meeting summaries tell you what was said. This tells you what actually happened.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
