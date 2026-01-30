<div align="center">

# Python Script Generator

### AI-powered scripts that run in CI, not just on your laptop.

Describe what you need. Get a production-ready Python script with a clean CLI, safe defaults, and explicit error handling.

<br>

![SDLC](https://img.shields.io/badge/SDLC%20Automation-blue?style=for-the-badge)
![DevOps](https://img.shields.io/badge/DevOps-purple?style=for-the-badge)
![AI](https://img.shields.io/badge/AI%20Powered-orange?style=for-the-badge)
![MIT](https://img.shields.io/badge/MIT-green?style=for-the-badge)

<br>

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

```
idea in  →  production-ready script out
```

<br>

[Overview](#overview) · [How It Works](#how-it-works) · [Quick Start](#quick-start) · [What You Get](#what-you-get) · [Examples](#examples) · [Pro Tips](#pro-tips)

</div>

<br>

---

<br>

## Overview

Most AI code generators write scripts that **work on your machine**. This one writes scripts that **work everywhere**.

The problem: you describe a quick automation task, and the AI hands you a script with hard-coded paths, bare `except:` blocks, no CLI, no validation, and no exit codes. It runs once. Then a teammate tries it, CI runs it, or a path changes — and it silently fails or corrupts data.

**Python Script Generator** builds scripts the way a senior engineer writes internal tooling: validated inputs, explicit exit codes, safe file operations, clean `argparse` CLIs, and deterministic behavior.

<br>

| Without Python Script Generator | With Python Script Generator |
|---|---|
| Hard-coded paths and magic values | `argparse` CLI with `--help` and typed arguments |
| Bare `except:` swallows errors | Specific exceptions with actionable messages |
| Overwrites files without warning | `--force` flag required for destructive ops |
| No exit codes — CI can't tell if it failed | Explicit `sys.exit(0/2/3)` contracts |
| Runs once, breaks on second machine | `pathlib`, env-aware, cross-platform defaults |
| No logging — `print()` everywhere | `logging` module with `--verbose` / `--quiet` |

<br>

---

<br>

## How It Works

<div align="center">

```

┌────────────────────────────────────────────────────────────┐
│                PYTHON SCRIPT GENERATOR                      │
│                                                            │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │ Extract  │→ │ Design   │→ │ Implement│→ │ Harden   │  │
│  │ Reqs     │  │ CLI      │  │ Logic    │  │ & Ship   │  │
│  │          │  │          │  │          │  │          │  │
│  │ goal     │  │ argparse │  │ pure fns │  │ validate │  │
│  │ inputs   │  │ flags    │  │ separate │  │ logging  │  │
│  │ outputs  │  │ exit     │  │ I/O from │  │ errors   │  │
│  │ risks    │  │ codes    │  │ compute  │  │ safety   │  │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘  │
│                                                            │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Add examples · Note assumptions · Include tests    │   │
│  └─────────────────────────────────────────────────────┘   │
└────────────────────────────┬───────────────────────────────┘
                             ▼
                  ┌────────────────────┐
                  │  Complete Script   │
                  │  + Documentation   │
                  │  ✓ Clean CLI       │
                  │  ✓ Input validation│
                  │  ✓ Safe defaults   │
                  │  ✓ Exit codes      │
                  │  ✓ Error handling  │
                  │  ✓ Usage examples  │
                  └────────────────────┘
```

</div>

<br>

| Step | What Happens |
|------|-------------|
| **Extract Reqs** | Parses your description for goal, inputs, outputs, constraints, and operational risks |
| **Design CLI** | Builds `argparse` with typed args, `--help`, exit codes, subcommands if needed |
| **Implement Logic** | Small pure functions, I/O separated from computation, `pathlib` for paths |
| **Harden & Ship** | Input validation, `logging`, specific exception handling, safe file ops, `--force` for destructive actions |
| **Document** | Usage block, real examples, assumptions, limitations, suggested improvements |
| **Test** | Optional pytest suite for core functions + sample CI snippet |

<br>

---

<br>

## Quick Start

**1.** Copy [`PROMPT.md`](./PROMPT.md) into a new AI conversation.

**2.** Describe the script you need — what it does, what it takes as input, what it produces.

**3.** Get a complete, runnable script. Copy it into your project and run it.

<br>

---

<br>

## What You Get

```
┌──────────────────────────────────────────────────────────┐
│  GENERATED OUTPUT                                        │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  ■ Summary                                               │
│    What was built and key design choices                 │
│                                                          │
│  ■ Usage                                                 │
│    CLI invocation with all flags documented              │
│                                                          │
│  ■ Code                                                  │
│    Imports → Constants → Argparse → Validation           │
│    → Core Logic → Main Entrypoint                        │
│                                                          │
│  ■ Examples                                              │
│    2-3 real invocations with expected output             │
│                                                          │
│  ■ Notes                                                 │
│    Assumptions, limitations, next improvements           │
│                                                          │
│  ■ Tests (if requested)                                  │
│    pytest suite + CI snippet                             │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Domains

| Use Case | What You Describe | What You Get |
|----------|------------------|-------------|
| **Backup / Archive** | "zip a folder with manifest" | Script with rotation, exclusions, SHA-256 manifest |
| **Log Analysis** | "scan logs, output CSV summary" | Script with pattern matching, timestamp extraction, streaming |
| **File Processing** | "convert JSON files to CSV" | Script with schema validation, atomic writes, error recovery |
| **CI Utilities** | "check for stale branches" | Script with Git operations, dry-run mode, JSON output |
| **Data Migration** | "move records from SQLite to CSV" | Script with batching, progress logging, rollback on failure |
| **Environment Setup** | "verify dev machine dependencies" | Script with version checks, actionable error messages |

<br>

---

<br>

## Examples

| Describe This | Get a Script That |
|--------------|------------------|
| "Scan .log files and output CSV" | Walks directories, counts errors/warnings, extracts timestamps, writes CSV |
| "Back up a folder to .zip" | Creates dated archives, rotates old backups, includes SHA-256 manifest |
| "Validate JSON configs against schema" | Reads schema, validates each file, reports errors with line numbers |
| "Clean up Docker images older than 30 days" | Lists images, applies age filter, requires `--force` to delete, dry-run default |
| "Watch a folder and run linting on changes" | Uses polling (stdlib), debounces, runs subprocess safely, logs results |

<br>

### Live Example

```
┌─ YOU ──────────────────────────────────────────────────────┐
│                                                            │
│  Create a script that scans .log files and outputs a CSV   │
│  summary: filename, lines, errors, warnings, timestamps.   │
│  Support --pattern and --recursive. Python 3.10, stdlib.   │
│                                                            │
└────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─ PYTHON SCRIPT GENERATOR ─────────────────────────────────┐
│                                                            │
│  Summary                                                   │
│    Built log_summarizer.py — scans log files, counts       │
│    errors/warnings, extracts timestamps, writes CSV.       │
│                                                            │
│  Usage                                                     │
│    python log_summarizer.py --src ./logs --out report.csv  │
│                                                            │
│  Code                                                      │
│    ✓ argparse with --pattern, --recursive, --verbose       │
│    ✓ pathlib for file discovery                            │
│    ✓ Streaming line-by-line (no full-file loads)           │
│    ✓ Configurable timestamp regex with fallback            │
│    ✓ csv.DictWriter output                                 │
│    ✓ Exit codes: 0 success, 2 bad input, 3 runtime error  │
│                                                            │
│  Examples                                                  │
│    $ python log_summarizer.py --src ./logs --out r.csv     │
│    $ python log_summarizer.py --src . --recursive          │
│                                                            │
│  Notes                                                     │
│    Timestamp extraction uses best-effort regex.            │
│    Falls back to empty string if no match found.           │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

<br>

---

<br>

## Pro Tips

**Be specific about exit codes.** Say "exit 0 on success, 2 on validation error, 3 on runtime failure" — you'll get a script that CI can rely on.

**Mention your Python version.** "Python 3.10, stdlib only" produces cleaner output than leaving it open. The generator adjusts syntax and available modules accordingly.

**Ask for tests.** Add "include pytest tests for core functions" and you'll get a test suite that covers the logic without testing argparse wiring.

**Describe the destructive case.** If your script deletes or overwrites, say so — the generator adds `--force` / `--dry-run` flags automatically. But if you describe it, you'll get better safety behavior.

**Provide a sample invocation.** Even a rough `script.py --src ./data --out report.csv` gives the generator a concrete CLI to design around.

<br>

---

<br>

## File Structure

```
python-script-generator/
├── SPEC.md      # Design document — the blueprint
├── PROMPT.md    # The finished prompt — paste and use
├── README.md    # You are here
└── POST.md      # LinkedIn post announcing this tool
```

<br>

## Contributing

1. Fork the repository
2. Add new script patterns or safety checks
3. Test with 3-5 real automation scenarios
4. Verify generated scripts are runnable
5. Open a Pull Request

<br>

## License

MIT License — see [LICENSE](../../../LICENSE) for details.

<br>

---

<div align="center">

<br>

**Python Script Generator**

Scripts that survive CI, teammates, and time.

**Author:** Tim Wolfe — [GitHub](https://github.com/rtwolfe) | [Telegram](https://t.me/timwolfe)

<br>

Powered by Vox - VDD: Voice Driven Development

</div>
