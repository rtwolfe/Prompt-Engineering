<div align="center">

# PRD → Engineering-Ready Requirements Translator

### Turn ambiguous PRDs into sprint-ready engineering requirements.

Product intent in. Implementable requirements out.

<br>

![Domain](https://img.shields.io/badge/SDLC%20Automation-blue?style=for-the-badge)
![QA](https://img.shields.io/badge/QA-purple?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
PRD  →  Requirements Translator  →  Sprint-Ready Engineering Requirements
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Domains](#domains) · [Examples](#examples) · [Pro Tips](#pro-tips) · [File Structure](#file-structure)

</div>

<br>

---

<br>

## Overview

PRDs describe what the product should do. They almost never describe it precisely enough for engineers to build without a round trip back to product. The gap between "conceptually sound" and "operationally buildable" is where sprints slip, scope creeps, and rework compounds.

**PRD → Engineering-Ready Requirements Translator** closes that gap. Give it a PRD and it produces **numbered functional requirements, testable acceptance criteria, edge cases, technical considerations, and explicit scope boundaries** — everything a developer needs to start building without guesswork.

> Your PRD isn't wrong — it's just not buildable yet.

<br>

### Why This Exists

| Without the Translator | With the Translator |
|---|---|
| Vague PRDs handed to engineering | Numbered, testable functional requirements |
| Endless clarification threads in Slack | Acceptance criteria ready for QA validation |
| Edge cases discovered mid-sprint | Edge cases enumerated before planning |
| Implicit assumptions become bugs | Open questions surfaced explicitly |
| "I thought we agreed on..." | Scope boundaries documented and traceable |
| Requirements rewritten during code review | Requirements written once, built once |

<br>

---

<br>

## How It Works

<div align="center">

```
                      ┌───────────────────────────────────┐
                      │                                   │
                      │   PRD → ENGINEERING-READY         │
                      │   REQUIREMENTS TRANSLATOR         │
                      │                                   │
                      │   ┌───────────────────────────┐   │
 ┌──────────────┐     │   │  1. PRD comprehension      │   │     ┌──────────────────┐
 │     PRD      │────▶│   │  2. Requirements extraction │   │────▶│ Sprint-Ready     │
 │  + Context   │     │   │  3. Acceptance criteria     │   │     │ Requirements     │
 │              │     │   │  4. Edge case enumeration   │   │     │                  │
 │ "Saved       │     │   │  5. Technical concerns      │   │     │ ■ Functional    │
 │  Searches,   │     │   │  6. Scope enforcement       │   │     │ ■ Acceptance    │
 │  v1"         │     │   │                             │   │     │ ■ Edge cases    │
 └──────────────┘     │   └───────────────────────────┘   │     └──────────────────┘
                      │                                   │
                      └───────────────────────────────────┘
```

</div>

<br>

**The workflow:**

| Step | What You Do | What You Get |
|------|------------|--------------|
| **1. Provide inputs** | PRD or PRD section + optional platform/format context | — |
| **2. Run the Translator** | Paste the prompt. Provide your PRD. | A complete engineering requirements document. |
| **3. Act** | Drop requirements into your sprint backlog or issue tracker. | Buildable stories with testable acceptance criteria. |

<br>

---

<br>

## Quick Start

### 1. Load

Copy [`PRD-engineering-ready-requirements-translator.md`](./PRD-engineering-ready-requirements-translator.md) into a Claude or ChatGPT conversation.

### 2. Provide your PRD

```
Here's the PRD for our new Saved Searches feature.
Target platform: Web
Issue format: Jira

[paste PRD]
```

### 3. Receive your requirements

A structured engineering requirements document — overview, functional requirements, acceptance criteria, edge cases, technical considerations, scope boundaries, and open questions.

### 4. Act

Drop the requirements into your sprint backlog. Use acceptance criteria for QA. Send open questions back to product before committing scope.

<br>

---

<br>

## What You Get

```
┌────────────────────────────────────────────────────────────┐
│  ENGINEERING-READY REQUIREMENTS DOCUMENT                    │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ■ Overview               Feature purpose in eng terms     │
│  ■ Functional Reqs        Numbered, testable, traceable    │
│  ■ Acceptance Criteria    Given/When/Then, QA-ready        │
│                                                            │
│  ■ Edge Cases             Failure modes & expected behavior │
│  ■ Technical Concerns     Storage, APIs, integrations      │
│  ■ Out of Scope           Explicit boundaries              │
│                                                            │
│  ■ Open Questions         Assumptions needing confirmation  │
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
                    │  SDLC             │
                    │  AUTOMATION       │
                    │  (primary)        │
                    │                   │
                    └────────┬──────────┘
                             │
             ┌───────────────┼───────────────┐
             │               │               │
      ┌──────▼──────┐ ┌─────▼──────┐ ┌──────▼─────┐
      │             │ │            │ │            │
      │  Require-   │ │  Sprint    │ │  Quality   │
      │  ments Eng  │ │  Planning  │ │  Assurance │
      │             │ │            │ │            │
      └─────────────┘ └────────────┘ └────────────┘
```

</div>

<br>

| Domain | What the Translator Covers |
|--------|---------------------------|
| **SDLC Automation** | Converting product artifacts into engineering-ready deliverables without manual rewriting |
| **Requirements Engineering** | Functional decomposition, acceptance criteria, traceability, ambiguity elimination |
| **Sprint Planning** | Scope boundaries, story-level requirements, issue-tracker-ready formatting |
| **Quality Assurance** | Testable acceptance criteria, edge case enumeration, failure mode identification |

<br>

---

<br>

## Examples

### What You Can Translate

| PRD Type | Key Value Added | Common Gap Closed |
|----------|----------------|-------------------|
| New feature PRD | Numbered requirements with acceptance criteria | Vague goals → testable conditions |
| API specification | Endpoint contracts, error handling, auth boundaries | Missing error cases and edge conditions |
| Migration PRD | Backward-compatibility requirements, rollback criteria | Unstated assumptions about data integrity |
| Platform enhancement | Integration points, performance constraints | Implicit NFRs that surface during code review |
| V1 → V2 iteration | Scope boundaries, deferred items list | Feature creep from undefined "improvements" |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────────────┐
│                                                                    │
│  Feature: Saved Searches                                           │
│  "Users want to save search queries and rerun them later."         │
│  Non-goals: No sharing in v1                                       │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─ TRANSLATOR ────────────────────────────────────────────────────────┐
│                                                                    │
│  Functional Requirements:                                          │
│  1. System shall allow authenticated users to save a search        │
│     query with a user-defined name                                 │
│  2. System shall associate saved searches with user account        │
│  3. System shall allow single-action re-execution of saved search  │
│                                                                    │
│  Acceptance Criteria:                                              │
│  ✓ Given valid query + click "Save" → query persisted in list      │
│  ✓ Given unauthenticated user → save option not visible            │
│                                                                    │
│  Edge Cases:                                                       │
│  ⚠ Duplicate name → prompt rename or append suffix                 │
│  ⚠ Deleted underlying data → empty results with clear message      │
│                                                                    │
│  Open Questions:                                                   │
│  ? Max saved searches per user?                                    │
│  ? Capture filters/sort or query string only?                      │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Include platform and stack context.**
The more the Translator knows about your target environment, the more specific its technical considerations become. "Web, React, PostgreSQL" produces better output than no context at all.

**Feed it one feature at a time.**
Multi-feature PRDs get better results when segmented. The Translator handles multi-feature inputs, but focused input produces sharper requirements.

**Send open questions back to product immediately.**
The Translator surfaces assumptions that will become bugs if left unresolved. Treat the Open Questions section as a pre-sprint checklist, not an appendix.

**Use the acceptance criteria directly in your issue tracker.**
They're written to be copy-pasted into Jira, Linear, or GitHub Issues. No reformatting needed.

**Run it twice — before and after product review.**
First pass identifies gaps. Product fills them. Second pass produces final sprint-ready requirements with no open questions.

<br>

---

<br>

## File Structure

```
INTAKE/
├── PRD-engineering-ready-requirements-translator.md  # The prompt (paste this into AI)
├── README.md     # You are here
├── POST.md       # LinkedIn post
└── SPEC.md       # Original build specification
```

<br>

## Contributing

1. Fork the repository
2. Add support for new PRD formats or issue-tracking templates
3. Test with 3-5 different PRDs across complexity levels
4. Verify output includes all 7 sections with testable requirements
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../LICENSE) for details.

<br>

---

<div align="center">

<br>

**PRD → Engineering-Ready Requirements Translator**

Your PRD isn't wrong — it's just not buildable yet.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox — VDD: Voice Driven Development

</div>
