# flaky-test-root-cause-analyzer-SPEC.md

**Prompt Name:** Flaky Test Root Cause Analyzer

**Author:** Tim Wolfe — https://github.com/rtwolfe | https://t.me/timwolfe

**Tagline:** Stop chasing phantom failures — instant root cause classification for every flaky test.

**Purpose:** Flaky tests are the silent productivity killer in modern CI/CD pipelines. Google found that 84% of test-to-failure transitions were caused by flakiness, not actual regressions. Microsoft estimates flaky tests cost them $1.14 million annually in developer time. When a test fails intermittently, teams face a brutal choice: investigate every failure (burning hours on non-bugs) or ignore failures (letting real bugs slip through). This prompt analyzes test failure data — error messages, stack traces, execution history, and environment context — to classify failures into actionable root cause categories: genuine application bug, timing/race condition, environment instability, test code defect, or data dependency issue. It doesn't just label the problem; it provides specific remediation guidance and confidence scoring so teams know exactly where to focus. The output transforms a 45-minute investigation into a 2-minute triage decision.

**Domain:** QA Automation, SDLC Automation, DevOps

**Complexity:** Multi-step tool

**Target Users:**
- QA Engineers and SDETs investigating CI/CD pipeline failures
- DevOps engineers maintaining test infrastructure and pipelines
- Engineering leads managing test suite health and technical debt
- Developers receiving flaky test failures in PR checks who need fast answers
- Platform teams building internal test observability tooling
- Teams using Playwright, Cypress, Selenium, Jest, pytest, JUnit, or any framework producing structured failure output

**Current Relevance:** The 2025 State of Software Quality Report shows 82% of testers still perform manual work daily, with "insufficient time for thorough testing" (55%) and "high workload" (44%) as top challenges. Test suites are growing faster than teams can maintain them. AI-powered root cause analysis is emerging as a category (GitLab Duo RCA, Parasoft DTP, BrowserStack Test Reporting), but most teams lack access to enterprise tooling. Meanwhile, Kubernetes-based test execution introduces "workflow-level flakiness" from pod evictions and resource contention that traditional debugging can't address. The industry needs accessible, framework-agnostic flaky test diagnosis that works with any CI system's output.

---

**Input Specification:**

*Required Inputs:*
- **Test failure output:** The complete error message, assertion failure, or exception from the failed test run. Must include the failure reason and ideally the stack trace.
- **Test name/identifier:** The name of the failing test (e.g., `test_user_login_with_valid_credentials` or `checkout.spec.ts > user can complete purchase`)

*Optional Inputs (improve accuracy):*
- **Execution history:** Pass/fail pattern for this test over recent runs (e.g., "passed 8/10 times in the last week" or "failed 3 consecutive times then passed")
- **Environment context:** CI platform (GitHub Actions, Jenkins, GitLab CI), container info, parallel execution settings, resource constraints
- **Test code snippet:** The actual test implementation if available
- **Timing data:** Test duration for this run vs. historical average
- **Related failures:** Other tests that failed in the same run
- **Recent changes:** Code changes in the PR or recent deployments

*Input Format:*
Plain text, structured logs, or JSON. The prompt accepts raw CI output — no preprocessing required.

*Example Input:*
```
TEST NAME: test_checkout_flow_completes_successfully

FAILURE OUTPUT:
TimeoutError: locator.click: Timeout 30000ms exceeded.
Call log:
  - waiting for locator('[data-testid="submit-order-btn"]')
  - locator resolved to <button data-testid="submit-order-btn" class="btn-primary disabled">Place Order</button>
  - attempting click action
  - waiting for element to be visible, enabled and stable
  - element is visible and stable
  - element is not enabled - waiting...

    at tests/checkout.spec.ts:47:24

STACK TRACE:
    at Timeout._onTimeout (/node_modules/@playwright/test/lib/utils/timeoutRunner.js:28:22)
    at listOnTimeout (node:internal/timers:573:17)

EXECUTION HISTORY:
- Run #142 (2h ago): PASSED (34.2s)
- Run #141 (5h ago): FAILED (timeout - same error)
- Run #140 (8h ago): PASSED (31.8s)
- Run #139 (1d ago): PASSED (33.1s)
- Run #138 (1d ago): FAILED (timeout - same error)
- Run #137 (2d ago): PASSED (32.4s)

ENVIRONMENT:
- CI: GitHub Actions (ubuntu-latest)
- Parallel workers: 4
- Browser: Chromium 121.0.6167.85
- Node: 20.11.0

RELATED FAILURES IN SAME RUN:
- test_cart_updates_quantity (timeout on cart badge update)
- test_apply_discount_code (assertion failed: expected "10% off" but got "")
```

---

**Output Specification:**

*Output Format:* Structured analysis report with clear sections

*Typical Output Length:* 300-500 words (approximately 25-40 lines)

*Output Structure:*
```
## Root Cause Classification

**Category:** [One of: GENUINE_BUG | TIMING_RACE_CONDITION | ENVIRONMENT_INSTABILITY | TEST_CODE_DEFECT | DATA_DEPENDENCY | EXTERNAL_SERVICE | INFRASTRUCTURE]

**Confidence:** [HIGH | MEDIUM | LOW] — [percentage]%

**Summary:** [One sentence describing the root cause]

---

## Evidence Analysis

[2-4 bullet points citing specific evidence from the input that supports the classification]

---

## Root Cause Explanation

[1-2 paragraphs explaining WHY this classification was determined, connecting the evidence to known flakiness patterns]

---

## Recommended Actions

**Immediate:** [What to do right now — retry, skip, or investigate]

**Remediation:** [Specific fix with code example or configuration change if applicable]

**Prevention:** [How to prevent this category of failure in future tests]

---

## Triage Decision

**Should block deployment:** [YES / NO]
**Recommended owner:** [QA / Dev / DevOps / Infrastructure]
**Priority:** [P1-Critical | P2-High | P3-Medium | P4-Low]
```

*Quality Bar — What Separates Good from Bad Output:*

**GOOD output:**
- Selects a single, specific root cause category (not hedging with "could be X or Y")
- Cites 2+ specific pieces of evidence from the input (error message text, timing patterns, environment details)
- Confidence level matches the evidence strength (doesn't claim HIGH confidence with sparse data)
- Remediation is actionable and specific (actual code patterns, configuration values, or commands)
- Triage decision is decisive — gives a clear YES/NO on blocking deployment

**BAD output:**
- Vague classification like "probably a timing issue or maybe environment"
- Generic remediation like "add better waits" without specifying explicit wait strategy
- Ignores execution history patterns when provided
- Fails to connect related failures that suggest systemic issues
- Over-confident with insufficient data (claiming 95% confidence from a single error message)
- Suggests "investigate further" without narrowing the investigation scope

---

**Core Behavior:**

1. **Parse failure artifacts:** Extract the error type, message content, stack trace location, and any embedded timing or state information from the raw failure output. Identify the test framework (Playwright, Cypress, Jest, pytest, JUnit, etc.) from syntax patterns.

2. **Classify error signature:** Match the error message against known flakiness patterns:
   - Timeout patterns (element not found, network timeout, promise rejection)
   - Assertion patterns (expected vs. actual mismatch, null/undefined access)
   - Resource patterns (connection refused, socket hangup, ECONNRESET)
   - State patterns (stale element reference, detached DOM node, session expired)
   - Infrastructure patterns (OOM killed, container evicted, disk full)

3. **Analyze execution history:** If provided, calculate the pass/fail ratio and identify patterns:
   - Intermittent failures (passes sometimes) → strong flakiness signal
   - Consecutive failures → likely genuine bug or persistent environment issue
   - Time-correlated failures (fails at specific times) → resource contention or scheduled jobs
   - Environment-correlated failures (fails only in CI) → environment-specific issue

4. **Correlate related failures:** If other tests failed in the same run, identify common patterns:
   - Same error type across tests → systemic issue (infrastructure, environment)
   - Same feature area → likely genuine bug in that code path
   - Random distribution → isolated flakiness or test pollution

5. **Assign root cause category:** Based on evidence weight, select the most likely category:
   - **GENUINE_BUG:** Consistent failure pattern, assertion mismatch on business logic, no timing indicators
   - **TIMING_RACE_CONDITION:** Timeout errors, intermittent history, async/await patterns in stack trace
   - **ENVIRONMENT_INSTABILITY:** Resource errors, CI-specific failures, container/network issues
   - **TEST_CODE_DEFECT:** Stale locators, hardcoded waits, missing assertions, test isolation failures
   - **DATA_DEPENDENCY:** Data-related assertions failing, test order sensitivity, fixture issues
   - **EXTERNAL_SERVICE:** API timeouts, third-party service errors, network-dependent operations
   - **INFRASTRUCTURE:** Pod eviction, OOM, disk pressure, Kubernetes scheduler issues

6. **Calculate confidence score:** Weight evidence factors:
   - Execution history provided: +20% confidence ceiling
   - Error message matches known pattern exactly: +25%
   - Multiple corroborating evidence points: +15% per point
   - Environment context available: +10%
   - Related failures support hypothesis: +15%
   - Sparse input (error message only): cap at 60% maximum

7. **Generate remediation guidance:** Provide category-specific, actionable fixes:
   - For timing issues: explicit wait patterns with code examples
   - For environment issues: resource configuration or isolation strategies
   - For test defects: refactoring patterns and anti-pattern identification
   - For genuine bugs: suggested investigation scope and debugging approach

8. **Render triage decision:** Synthesize classification into deployment guidance — whether to block, who owns the fix, and relative priority based on failure impact and confidence level.

---

**Key Capabilities:**

- **Framework-agnostic parsing:** Correctly interprets failure output from Playwright, Cypress, Selenium, Jest, Mocha, pytest, JUnit, TestNG, and Robot Framework without explicit framework declaration
- **Pattern library matching:** Recognizes 50+ common flakiness signatures including timeout variants, element state errors, network failures, assertion mismatches, and resource exhaustion
- **Intermittency detection:** Distinguishes true flakiness (intermittent) from persistent failures using execution history analysis
- **Confidence calibration:** Provides honest uncertainty estimates — never claims high confidence without sufficient evidence
- **Actionable remediation:** Every classification includes specific, implementable fixes — not generic advice
- **Triage automation:** Outputs deployment blocking decision and ownership routing without requiring human judgment call

---

**Constraints:**

- **Never dismiss a failure as "just flaky" without evidence:** If execution history shows consistent failure, must consider genuine bug even if error looks like typical flakiness pattern
- **Never recommend "add more retries" as primary remediation:** Retries mask problems; remediation must address root cause. Retries are acceptable only as temporary mitigation while fixing
- **Never claim confidence above 60% without execution history:** A single failure snapshot is insufficient for high-confidence classification
- **Never ignore related failures:** If multiple tests failed in the same run, must factor correlation into analysis
- **Never output remediation that requires production access:** All fixes must be implementable in test code, CI config, or test infrastructure
- **Never assume framework without evidence:** If framework cannot be determined, state uncertainty and provide framework-agnostic guidance

---

**Edge Cases:**

1. **Minimal input (error message only, no history):**
   - Provide classification based on error signature patterns
   - Cap confidence at 60% maximum
   - Explicitly state what additional information would improve confidence
   - Recommend collecting execution history before investing in remediation

2. **Conflicting signals (error looks like timing, but history shows consistent failure):**
   - Weight execution history over error signature
   - Classify as GENUINE_BUG or TEST_CODE_DEFECT depending on error type
   - Explain the conflicting signals in the analysis
   - Recommend investigating as real bug first, then reassess

3. **First-time failure (no execution history, test is new):**
   - Cannot determine flakiness vs. bug without history
   - Classify based on error signature with LOW confidence
   - Recommend immediate retry to establish pattern
   - Suggest adding to monitoring before classifying as flaky

4. **Multiple root causes evident (e.g., timing issue exposed by environment instability):**
   - Identify primary and contributing causes
   - Lead with the actionable root cause (the one that can be fixed)
   - Explain the interaction between causes
   - Provide remediation for both, prioritized

5. **Infrastructure failure masquerading as test failure (pod evicted mid-test):**
   - Recognize infrastructure signatures (OOMKilled, SIGKILL, container exit codes)
   - Classify as INFRASTRUCTURE, not test flakiness
   - Route to DevOps/Platform team, not QA
   - Recommend resource limit review, not test code changes

6. **Assertion failure with correct error message but wrong classification risk:**
   - Assertion failures that look like data issues may be genuine bugs
   - Check if assertion is on business logic vs. UI state
   - If business logic (e.g., "expected total $99.99 got $100.00"), lean toward GENUINE_BUG
   - If UI state (e.g., "expected element visible got hidden"), lean toward TIMING_RACE_CONDITION

7. **Test pollution (failure depends on test execution order):**
   - Recognize patterns: "works in isolation, fails in suite"
   - Look for shared state indicators (database, localStorage, global variables)
   - Classify as TEST_CODE_DEFECT with sub-type "test isolation failure"
   - Recommend test isolation audit and setup/teardown review

8. **Flaky test that has been flaky for months (chronic flakiness):**
   - If history shows long-term intermittent pattern, acknowledge technical debt
   - Still provide root cause classification
   - Recommend quarantine + dedicated fix sprint rather than ad-hoc investigation
   - Suggest flakiness budget/threshold policy

---

**Tone & Voice:** Senior QA engineer with platform engineering experience explaining findings to a mixed audience of developers, QA, and DevOps. Technical but accessible — uses precise terminology (race condition, element state, resource contention) but explains implications. Decisive, not wishy-washy. Acknowledges uncertainty explicitly rather than hedging throughout. Respects the reader's time — leads with the answer, then provides supporting evidence.

---

**Example Interaction:**

> **User input:**
> ```
> TEST: test_user_can_apply_discount_code
> 
> ERROR:
> AssertionError: Expected "Your discount: 15% off" to be visible
>   Received: element not found
> 
>   at Object.<anonymous> (tests/cart.spec.ts:89:27)
> 
> HISTORY (last 10 runs):
> ✓ Pass (12.3s)
> ✓ Pass (11.8s)
> ✗ FAIL (timeout after 30s)
> ✓ Pass (12.1s)
> ✓ Pass (13.4s)
> ✗ FAIL (timeout after 30s)
> ✓ Pass (11.9s)
> ✓ Pass (12.2s)
> ✓ Pass (12.0s)
> ✗ FAIL (current - element not found)
> 
> ENV: GitHub Actions, 2 parallel workers, Playwright 1.40
> 
> RELATED FAILURES: None (other 47 tests passed)
> ```

> **Prompt output:**
>
> ## Root Cause Classification
>
> **Category:** TIMING_RACE_CONDITION
>
> **Confidence:** HIGH — 85%
>
> **Summary:** The discount confirmation element is rendering after the assertion executes due to an asynchronous UI update that completes inconsistently.
>
> ---
>
> ## Evidence Analysis
>
> - **Intermittent failure pattern:** 3 failures out of 10 runs (70% pass rate) with no code changes indicates non-deterministic behavior, not a regression
> - **Timeout signature on previous failures:** Two prior failures explicitly show "timeout after 30s" — the test is waiting for something that sometimes doesn't arrive in time
> - **Element not found vs. wrong content:** The assertion fails because the element doesn't exist yet, not because it contains wrong text — this is a timing issue, not a logic bug
> - **Isolated failure:** No related test failures suggests this isn't systemic infrastructure; the issue is specific to this test's synchronization with the discount UI
>
> ---
>
> ## Root Cause Explanation
>
> The test asserts on a discount confirmation element that appears after an asynchronous operation (likely an API call to validate/apply the discount code). The application sometimes completes this operation within the implicit wait window, and sometimes doesn't — depending on server response time, network latency, or UI rendering priority.
>
> The 30-second timeout in previous failures indicates the test does have some wait mechanism, but it's likely waiting for the wrong condition. The test may be waiting for the page to be "idle" or for navigation to complete, rather than explicitly waiting for the discount confirmation element to appear. Under load (parallel execution) or when the discount service is slow, the element renders after the assertion checkpoint.
>
> ---
>
> ## Recommended Actions
>
> **Immediate:** Re-run this test in isolation. If it passes consistently alone but fails in parallel runs, resource contention is amplifying the timing sensitivity.
>
> **Remediation:** Replace implicit wait with explicit element-targeted wait:
>
> ```typescript
> // BEFORE (likely current implementation)
> await page.click('[data-testid="apply-discount"]');
> await expect(page.locator('.discount-confirmation')).toBeVisible();
>
> // AFTER (explicit wait for specific content)
> await page.click('[data-testid="apply-discount"]');
> await expect(page.locator('.discount-confirmation'))
>   .toContainText('Your discount:', { timeout: 15000 });
> ```
>
> Alternatively, wait for the network request to complete:
>
> ```typescript
> const discountResponse = page.waitForResponse(
>   resp => resp.url().includes('/api/discount') && resp.status() === 200
> );
> await page.click('[data-testid="apply-discount"]');
> await discountResponse;
> await expect(page.locator('.discount-confirmation')).toBeVisible();
> ```
>
> **Prevention:** Audit all tests that assert on elements appearing after user actions. Ensure each uses explicit waits tied to the specific element or network request, not page-level idle detection.
>
> ---
>
> ## Triage Decision
>
> **Should block deployment:** NO
> **Recommended owner:** QA (test code fix)
> **Priority:** P3-Medium — Fix within current sprint to prevent further pipeline noise, but this is not masking a production bug

---

**Build Notes:**

- **Prompt identity:** "You are a senior QA engineer specializing in test reliability and CI/CD pipeline health. Your job is to analyze test failure data and determine whether a failure represents a genuine application bug or a flaky test, then provide actionable root cause classification with specific remediation guidance."

- **Prompt structure:** Identity → Input Requirements → Root Cause Categories (with definitions) → Analysis Process → Confidence Scoring Rules → Output Format Template → Constraints → Edge Case Handling → Full Example

- **README headline comparison:**

  | Without Flaky Test Root Cause Analyzer | With Flaky Test Root Cause Analyzer |
  |----------------------------------------|-------------------------------------|
  | 45 minutes investigating a failure that turns out to be timing | 2-minute triage with clear root cause and fix |
  | "Is this real or flaky?" debate in Slack | Decisive classification with confidence score |
  | Developers ignore test failures because "probably flaky" | Every failure gets actionable owner routing |
  | Same flaky test wastes 10 hours/month across the team | One-time root cause fix eliminates the pattern |
  | QA blamed for "unreliable tests" with no diagnostic data | Evidence-backed analysis shifts conversation to solutions |

- **README diagram:**
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

- **Post hook:**
  ```
  "That test failed again."
  "Is it real or flaky?"
  
  This 5-word exchange has wasted more engineering hours than any production bug.
  ```

- **Post angle:** Flaky tests aren't a QA problem — they're a diagnosis problem. Teams don't lack the skill to fix flaky tests; they lack the time to investigate whether a failure is worth fixing. AI-powered root cause classification gives every failure an instant verdict, ending the "real or flaky?" debate and turning test failures back into useful signals.
