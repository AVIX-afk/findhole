# Changelog

## 0.2.0 — 2026-10-19

- **Scan is now the default** and is enforced: other modes run only when named in the arguments, the skill never escalates on its own, and every run opens with a header line stating its mode and budget.
- **Mandatory solution check in every mode**, with reserved searches that can't be spent on evidence (2 for scan and verify, 3 for deep, repair and opportunity). Holes are batched into one official-channel search and one third-party search, so cost doesn't grow per hole.
- Every hole records what it was **checked against**. An unchecked hole is `UNKNOWN (unchecked)`, never OPEN. ACT, PILOT or build requires a check in both channels.
- Reports show a **Budget used** line with actual counts, and any overrun has to be explained.
- Budgets rebalanced: scan 4 → 5 searches (3 evidence + 2 check), deep and opportunity 10 → 11 (8 + 3), repair 8 → 9 (6 + 3), verify unchanged at 5 (3 + 2).
- Report template split into `references/templates/scan.md`, `full.md` and `verify.md`, and only the one for the current mode is loaded. A scan can now recommend at most NEEDS DEEP RUN.

## 0.1.0 — 2026-10-19 (first public release)

- Research budgets per mode (searches and page fetches), with a `budget:N` override.
- Cost rules: cheapest search first, batch searches, prefer snippets over fetches, no retries on blocked URLs.
- Step 0: pin an ambiguous target with at most one search.
- Stopping rule for the "already solved?" sweep: stop a hole after two credible, maintained solutions.
- Local file access limited to the current project and files the user names.
- Domain playbooks split into one file per domain so only one is loaded per run.
- Report template now has full, short (scan) and delta (verify) forms; source register compacted.
- Owner-only holes (server-side, anti-cheat, firmware, regulated) called out explicitly.
- Added README, LICENSE, example report.

## Pre-release

- Initial private version, tested once (WARDOGS, deep mode).
