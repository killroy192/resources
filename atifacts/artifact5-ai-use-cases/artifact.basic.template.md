# <Service / Repo> AI Use Case Playbook

**Measurements (source of truth):** [`{name}-SDLC.json`]({name}-SDLC.json)

> Link the input measurements file. Every number in this doc must trace back to it. Empty metric in JSON = "not measured" here, never a guess.

**Metrics window:** `{YYYY-MM-DD → YYYY-MM-DD (~Nd)}` · pulled `{YYYY-MM-DD}`

> Copy from JSON generalInformation.metricsWindow + metricsPulledAt.

**Ratings:** **H** = High · **M** = Medium · **L** = Low — applied to **Impact · Risk · Effort**.

---

## How to read this

> Keep the three-layer logic explicit so a grader/reviewer can follow measurement → diagnosis → prescription. 

1. **Measurements** — the physical feedback path + what the last window actually measured (from the JSON `states[]`).
2. **Findings** — what is *true* about the path today (diagnosis, coded to a station).
3. **Use cases** — before → after + how we would *prove* it (prescription).

> **Findings ≠ use cases.** A Finding = what's true. A Use case = the change + the evidence that it worked.

---

## 1. Findings

> Derive each Finding from measured signals in the JSON: high negativeFeedbackFrequency, flagged: true activities,
> 0-precision / 0-processingTime gates, "reason: Manual" transitions, dominantFailureMode, etc.
> A Finding is a fact + its consequence, coded to ONE station on the map. Aim for 3–6 crisp Findings.

| # | Finding (short) | Station (from JSON `states[]`) | Evidence (metric from JSON) | Use case |
|---|-----------------|--------------------------------|-----------------------------|----------|
| **F1** | {what's true} | {state name} | e.g. failRate 80%, PT ~2.8h, flagged gate | **UC-1** |
| **F2** | {what's true} | {state name} | {metric} | **UC-2** |
| **F3** | {what's true} | {state name} | {metric} | **UC-…** |

> Then expand each Finding below. One short paragraph: the measured fact, why it matters, and the single station it lives on.
> Distinguish "healthy / leave alone" findings from "fix this" findings — not every finding needs a big use case.

### F1 — {title}

- **Measured:** {cite the exact number(s) from the JSON, e.g. "445: 15 runs, ~80% fail, dominant = Coverlet <90%"}.
- **Means:** {plain-English consequence}.
- **Coded on:** {station} · **→ UC-1**

### F2 — {title}

- **Measured:** {number(s)}.
- **Means:** {consequence — include when a metric is actually *fine* so nobody "fixes" a non-problem}.
- **Coded on:** {station} · **→ UC-2**

> Repeat per finding.

---

## 2. Use case descriptions

> One use case per fixable Finding (or per cluster of related findings). Each is a prescription with proof.
> Keep the same shape for every UC so they can be compared and prioritised.

### Use case index

| ID | Title | Finding(s) | Station / where | Impact | Risk | Effort |
|----|-------|-----------|-----------------|--------|------|--------|
| **UC-1** | {title} | F1 | {station} | H | L | L |
| **UC-2** | {title} | F2 | {station} | M | L | M |
| **UC-…** | {title} | F… | {station} | | | |

> For each UC use the block below. Delete guidance comments in the real doc.

### UC-1 — {title}

- **Where:** {station from JSON}
- **Finding:** {F1}
- **Title means:** {one sentence — remove ambiguity so two people read it the same way}

**Problem:** {the measured pain this attacks — restate the Finding's metric}.

| Before | After |
|--------|-------|
| {current behaviour} | {target behaviour} |

**Recommended AI workflow pattern:**

- e.g. chained skills w/ human gates
- read-only verifier subagent
- rule-enforced command order
- log-triage subagent
- diff advisory

> Name the pattern; describe the concrete steps or command chain if useful. Keep humans in the loop where risk is real.

**Required context**

| Tier | Sources |
|------|---------|
| Hot | {files/data the agent must have} |
| Warm | {rules, conventions, prior examples} |
| Cold | {explicitly out of scope / ignore} |

**Verification approach:**

- {e.g. every must-have AC maps to a test name or manual step}
- {e.g. metric X moves from {baseline in JSON} to {target}}
- {human sign-off / gate that stays mandatory}

**Ratings:**

- Impact **H/M/L**
- Risk **H/M/L** (why)
- Effort **H/M/L** (what exists already)

> Repeat the UC block for UC-2 … UC-N.

---

## 3. Prioritisation

> Turn Impact/Risk/Effort into an ordered plan. High Impact + Low Effort + Low Risk goes first.
> Sequence dependencies explicitly (e.g. "raise coverage BEFORE requiring the gate, or you freeze merges").

### Ranked backlog

| P | Do | UC | Rationale (Impact · Risk · Effort) | Done when… |
|---|----|----|-----------------------------------|------------|
| P0 | {highest-leverage, low-risk action} | UC-1 | H · L · L | {measurable exit criterion} |
| P0 | {another quick win} | UC-3 | H · L · L | {criterion} |
| P1 | {valuable, moderate effort} | UC-2 | M · L · M | {criterion} |
| P2 | {bigger / dependent effort} | UC-4 | H · M · M | {criterion — note prerequisite} |

> Optional: split multi-phase use cases so prerequisites are visible in the order.

---

## Traceability checklist

- [ ] Every Finding cites a metric that exists in the JSON (no invented numbers).
- [ ] Every Finding maps to exactly one station and at least one use case.
- [ ] Every use case has Impact · Risk · Effort and a verifiable "Done when".
- [ ] Prioritisation respects dependencies (no gate enabled before its prerequisite).
- [ ] Empty / unmeasured metrics are labelled "not measured", never guessed.
