# Report template

Three forms. Use the one that matches the mode. Keep prose tight: tables over paragraphs, one line per source. Omit a section's rows rather than padding them.

---

## FULL FORM (deep / repair / opportunity)

```markdown
# FINDHOLE Report — <target>

- **As of:** YYYY-MM-DD · **Mode:** deep · **Version:** <build/version/date> · **Audience:** <who this is for>
- **Decision:** ACT / PILOT / ADOPT EXISTING / WATCH / NO CLEAR GAP
- **Bottom line:** 1–3 plain sentences answering "Is there a meaningful unfilled hole worth acting on?"

## 1. Scope and coverage
- **Assumptions:** (e.g. how the target was interpreted)
- **Promised / expected / actual:** ...
- **Searched:** N web searches, N fetches, as of <date>. Channels: ...
- **Couldn't reach:** ... (blocked sites, 403s, private sources)
- **Counterevidence sought:** ...

## 2. Hole ledger
| ID | Hole · who's affected | Evidence | Cause conf. | Existing remedy | Status | Impact 1–5 | Next check |
|---|---|---|---|---|---|---|---|
| H-01 | ... | [src](url) | L/M/H | ... | SOLVED/PARTIAL/STALE/OPEN/UNKNOWN | ... | ... |

## 3. Already filled — don't rebuild
Bullets: what's solved, by whom, how current, and what it doesn't cover.

## 4. Best remaining opportunities (max 3)
### H-xx — <name>
- **Pain:** ...
- **Evidence for / against:** ...
- **Cause hypothesis · falsified if:** ...
- **What exists · why it falls short:** ...
- **Recommendation:** adopt / configure / extend / fork / build / watch — why
- **Scores:** Impact _ · Evidence _ · Unmet need _ · Feasibility _ · Risk _ (one-line reason each)
- **Smallest experiment:** steps, effort (estimate)
- **Acceptance / kill:** baseline → target, metric, stop condition
- **Rollback · licensing · safety:** ...

## 5. Ranked actions
| # | Action | First experiment | Success threshold | Effort (est.) | Status |
|---|---|---|---|---|---|

## 6. What could make this wrong
Sampling bias · version drift / coming fix · missed solution · wrong cause · demand without willingness to pay/use · access or regulatory blocker. Keep only the ones that apply.

## 7. Sources
| Source | URL | Checked | Supports/contradicts | Limits |
|---|---|---|---|---|
One row per source, a few words per cell.

## 8. Next step
The single smallest next action. If implementation wasn't authorized, stop at the plan.
```

---

## SHORT FORM (scan)

```markdown
# FINDHOLE Scan — <target>
- **As of:** YYYY-MM-DD · **Decision:** ... · **Bottom line:** ...
- **Searched:** N searches; couldn't reach: ...

| ID | Hole | Status | Impact 1–5 | Confidence | Evidence |
|---|---|---|---|---|---|

**Worth a deep run?** Yes/no and which holes, with the searches that would settle them.
```

---

## DELTA FORM (verify)

```markdown
# FINDHOLE Verify — <target> (vs report of YYYY-MM-DD)
| ID | Was | Now | What changed | Source |
|---|---|---|---|---|

**Decision change:** none / upgraded / downgraded — why.
```
