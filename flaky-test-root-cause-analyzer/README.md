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
└── POST.md      # LinkedIn announcement
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
