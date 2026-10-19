# Template: scan (default)

Keep it short: one table and a few lines. Omit empty rows rather than padding them.

```markdown
# FINDHOLE Scan — <target>
- **As of:** YYYY-MM-DD · **Mode:** scan (default|requested) · **Assumptions:** ...
- **Budget used:** E/3 evidence + S/2 solution-check searches, F/2 fetches · **Couldn't reach:** ...
- **Decision:** ADOPT EXISTING / WATCH / NO CLEAR GAP / NEEDS DEEP RUN
- **Bottom line:** 1–2 sentences answering "Is there a meaningful unfilled hole worth acting on?"

| ID | Hole · who's affected | Evidence | Checked against | Status | Impact 1–5 | Confidence |
|---|---|---|---|---|---|---|
| H-01 | ... | [src](url) | official: <query/source> · 3rd-party: <query/source> | SOLVED/PARTIAL/STALE/OPEN/UNKNOWN (unchecked) | ... | L/M/H |

**Already solved, so don't build:** ... (one line per remedy, with link)

**Worth a deep run?** Yes or no. If yes, which holes, and run `/findhole <target> deep`.
```

A scan never recommends ACT, PILOT or build. The strongest it can recommend is NEEDS DEEP RUN.
