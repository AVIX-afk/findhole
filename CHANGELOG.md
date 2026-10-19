# Changelog

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
