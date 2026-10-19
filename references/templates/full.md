# Template: full (deep / repair / opportunity)

Tables over paragraphs, one line per source. Omit rows that don't apply rather than padding them.

```markdown
# FINDHOLE Report — <target>

- **As of:** YYYY-MM-DD · **Mode:** deep|repair|opportunity · **Version:** <build/version/date> · **Audience:** <who>
- **Budget used:** E/<max> evidence + S/3 solution-check searches, F/<max> fetches (explain any overrun)
- **Decision:** ACT / PILOT / ADOPT EXISTING / WATCH / NO CLEAR GAP
- **Bottom line:** 1–3 plain sentences answering "Is there a meaningful unfilled hole worth acting on?"

## 1. Scope and coverage
- **Assumptions:** ...
- **Promised / expected / actual:** ...
- **Channels searched (as of <date>):** ...
- **Couldn't reach:** ... (blocked sites, 403s, private sources)
- **Counterevidence sought:** ...

## 2. Hole ledger
| ID | Hole · who's affected | Evidence | Checked against | Cause conf. | Existing remedy | Status | Impact 1–5 | Next check |
|---|---|---|---|---|---|---|---|---|
| H-01 | ... | [src](url) | official: ... · 3rd-party: ... | L/M/H | ... | SOLVED/PARTIAL/STALE/OPEN/UNKNOWN (unchecked) | ... | ... |

## 3. Already filled, so don't rebuild
Bullets: what's solved, by whom, how current, and what it doesn't cover.

## 4. Best remaining opportunities (max 3)
### H-xx — <name>
- **Pain:** ...
- **Evidence for / against:** ...
- **Cause hypothesis · falsified if:** ...
- **What exists · why it falls short:** (must cite the official and third-party checks)
- **Recommendation:** adopt / configure / extend / fork / build / watch, with why
- **Scores:** Impact _ · Evidence _ · Unmet need _ · Feasibility _ · Risk _ (one-line reason each)
- **Smallest experiment:** steps, effort (estimate)
- **Acceptance / kill:** baseline → target, metric, stop condition
- **Rollback · licensing · safety:** ...

## 5. Ranked actions
| # | Action | First experiment | Success threshold | Effort (est.) | Status |
|---|---|---|---|---|---|

## 6. What could make this wrong
Keep only the ones that apply: sampling bias · version drift or a coming fix · missed solution · wrong cause · demand without willingness to pay or use · access or regulatory blocker.

## 7. Sources
| Source | URL | Checked | Supports/contradicts | Limits |
|---|---|---|---|---|

## 8. Next step
The single smallest next action. If implementation wasn't authorized, stop at the plan.
```

ACT, PILOT or build is allowed only for a hole checked in both the official and the third-party channel. Otherwise the strongest allowed decision is WATCH.
