# FINDHOLE

**Evidence → unfilled gap → actionable solution.** A Claude Code skill that investigates a game, product, service, process or market, finds where it falls short, checks whether someone has already fixed it, and hands you the smallest action worth taking — including "do nothing" when the gap isn't real.

```
/findhole Wardogs
/findhole "Notion offline mode" scan
/findhole our-checkout-flow repair budget:6
/findhole "budget 3D printers for schools" opportunity
```

## Why use it

Most "find me an opportunity" prompts produce confident lists of ideas that already exist. FINDHOLE is built to avoid that:

- **Mandatory "already solved?" check.** Every hole is labelled SOLVED / PARTIAL / STALE / OPEN / UNKNOWN, and UNKNOWN is never upgraded to "nobody has done this."
- **Counterevidence by design.** It samples positive reviews and developer intent, so deliberate tradeoffs and loud minorities don't become fake holes.
- **Owner-only holes flagged.** Problems only the vendor can fix (server logic, anti-cheat, firmware) are separated from ones you can act on.
- **Kill/watch is a real outcome.** Recommendations come with acceptance tests and stop conditions.
- **Bounded cost.** Each mode has a research budget, and a stopping rule ends the solution search once credible fixes are found.

## Install

FINDHOLE is a standard [Claude Code skill](https://code.claude.com/docs/en/skills).

**For all your projects (personal skill):**

```bash
git clone https://github.com/AVIX-afk/findhole ~/.claude/skills/findhole
```

On Windows, `~` is `C:\Users\<you>`, so the skill lands in `C:\Users\<you>\.claude\skills\findhole`.

**For one project (shared with your team via the repo):**

```bash
git clone https://github.com/AVIX-afk/findhole .claude/skills/findhole
```

Restart Claude Code (or start a new session), then type `/findhole`.

**Update:** `git -C ~/.claude/skills/findhole pull`

## Usage

```
/findhole <target> [mode] [budget:N] [constraints]
```

| Mode | Use it for | Web searches | Page fetches | Output |
|---|---|---|---|---|
| `scan` | Quick triage — is this worth a closer look? | ≤ 4 | ≤ 2 | Short table |
| `deep` *(default)* | Full investigation and ranked roadmap | ≤ 10 | ≤ 6 | Full report |
| `repair` | One specific thing that's broken | ≤ 8 | ≤ 5 | Full report, fix-focused |
| `opportunity` | Underserved demand; build / buy / fork | ≤ 10 | ≤ 6 | Full report |
| `verify` | Re-check an earlier FINDHOLE report | ≤ 5 | ≤ 3 | What changed |

Budgets are ceilings. `budget:N` overrides the search limit. Add constraints in plain words: `"no coding, under $200, must work on Mac"`.

The skill only runs when you type `/findhole` (`disable-model-invocation: true`), so it never starts a research run on its own.

## What you get

A short verdict in chat, plus a report saved to `reports/findhole/<target>-YYYY-MM-DD.md` in your current project (never overwritten — reruns get `-r2`, `-r3`). See [examples/wardogs-2026-10-19.md](examples/wardogs-2026-10-19.md).

Report sections (deep mode): decision and bottom line · scope and what couldn't be reached · hole ledger · already solved (don't rebuild) · up to three opportunities with scores, experiment and kill criteria · ranked actions · what could make this wrong · sources · next step.

## Cost

Measured on one deep run (the example report): **9 web searches, 5 page fetches, about 46k tokens of conversation.** That was before the budgets above were added, so a deep run should now be similar or lower, and `scan` much lower. Your total session usage will be higher by whatever your own setup loads (tool definitions, MCP servers, other skills); that overhead is not from FINDHOLE. This is a single measurement, not a benchmark.

## Requirements

- Claude Code with a web search tool. Without web access the skill still runs on local files and dated knowledge, and labels affected holes UNKNOWN.
- A page-fetch tool helps but is optional.
- Sites like Reddit, Discord and some review sites are often blocked to agents. The playbooks list fallbacks, and the report says what couldn't be reached.

## Guardrails

Research only by default: it won't install mods, patch software, change production systems, buy anything or publish anything unless you explicitly ask. It won't recommend bypassing anti-cheat, DRM or access controls. Industrial, medical and safety-critical findings are framed as hypotheses that need qualified review.

## Limitations

- Findings are a snapshot; rerun with `verify` as products change.
- A finite search can't prove something doesn't exist. Reports say where and when they searched.
- Review scores and complaint volumes from secondary sources are often inconsistent; the skill reports ranges, not single numbers.
- Tested with Claude Code. Uploading to claude.ai as a skill is untested — `$ARGUMENTS` and `disable-model-invocation` are Claude Code features.

## Layout

```
findhole/
├── SKILL.md                     # the skill (loaded on /findhole)
├── references/
│   ├── report-template.md       # full / short / delta report forms
│   ├── playbooks/               # one file per domain; only one is read per run
│   │   ├── games.md  software.md  hardware.md
│   │   └── industrial.md  markets.md  repositories.md
│   └── inspiration.md           # prior art and licenses
└── examples/
    └── wardogs-2026-10-19.md
```

## Contributing

Issues and PRs welcome — especially new domain playbooks, better fallbacks for blocked sources, and example reports with their search/fetch counts. Keep `SKILL.md` lean: every line in it is loaded on every run.

## Credits and license

MIT — see [LICENSE](LICENSE). Methodology draws on several public skills, credited with their licenses in [references/inspiration.md](references/inspiration.md).
