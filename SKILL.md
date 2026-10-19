---
name: findhole
description: "Evidence-led hole finding for games, software, products, services, industries, and processes. Diagnose unmet expectations, identify root causes, check existing fixes and competitors, find truly underserved gaps, and create testable action plans. Invoke with /findhole and a target."
argument-hint: "<target> [scan|deep|repair|opportunity|verify] [budget:N] [constraints]"
disable-model-invocation: true
---

# FINDHOLE — Evidence → Unfilled gap → Actionable solution

**Investigation target and any user constraints:** $ARGUMENTS

## Mission

Answer four questions with evidence, not intuition: (1) Where does reality fall short of reasonable expectations? (2) What actually causes that shortfall? (3) Who has already solved it, partially solved it, or tried and failed? (4) What is the smallest defensible action that would close a meaningful remaining gap?

Targets can be games, software, physical products, business processes, industrial systems, services, projects or markets. **Repairing an existing experience** and **finding something to build** are equally valid outcomes. Prefer an adequate existing solution over reinventing it, and always keep **do nothing / watch** on the table.

## Modes and research budget

**The default mode is `scan`.** Run any other mode only when its exact word (`deep`, `repair`, `opportunity`, `verify`) appears in the arguments. Never upgrade a run on your own because the target looks interesting or the evidence is thin. If a scan finds holes worth more research, end by recommending `/findhole <target> deep` and stop.

**Before your first search**, write this run header as the first line of your reply, so the mode and limits are visible and checkable:

`FINDHOLE · mode: <mode> (<default|requested>) · budget: <E> evidence + <S> solution-check searches, <F> fetches`

| Mode | Purpose | Evidence searches | Solution-check searches (reserved) | Page fetches | Report template |
|---|---|---|---|---|---|
| **scan** *(default)* | Fast triage, 3–5 highest-value holes | ≤ 3 | 2 | ≤ 2 | `templates/scan.md` |
| **deep** | Cross-source investigation, ranked roadmap | ≤ 8 | 3 | ≤ 6 | `templates/full.md` |
| **repair** | Diagnose one failing experience/system, rank fixes | ≤ 6 | 3 | ≤ 5 | `templates/full.md` |
| **opportunity** | Underserved demand; build/buy/fork | ≤ 8 | 3 | ≤ 6 | `templates/full.md` |
| **verify** | Re-check a prior FINDHOLE report | ≤ 3 | 2 | ≤ 3 | `templates/verify.md` |

Budgets are ceilings, not targets: stop early once the evidence is sufficient. `budget:N` changes the evidence-search ceiling only. The reserved solution-check searches always stay.

**Keep a running tally** of searches and fetches used, and put the final count in the report's `Budget used` line. If you go over, say by how much and why. Never hide it.

Cost rules:
- Use the cheapest search mode first; use deeper/extended/premium search only when a cheaper result is thin, stale or off-target.
- Batch independent searches in one step. Prefer search-result snippets over fetching full pages; fetch only primary sources or pages whose detail changes a conclusion.
- A failed or blocked fetch counts against the budget — do not retry the same URL; note it as a limit and move on.
- If the budget runs out with holes still UNKNOWN, report them as UNKNOWN and list the next searches to run. Never stretch thin evidence to fill gaps.
- If no web access is available, say so, work from local files and clearly dated prior knowledge, and label affected holes UNKNOWN.

## Investigation protocol

### 0. Pin the target (1 search max)
If the target name is ambiguous (a game vs. a film vs. a company), spend at most one search identifying it (it counts as an evidence search). State the interpretation as a labeled assumption and continue; ask the user only if two readings are equally likely and would lead to different research.

### 1. Define the comparison
- Identify target, version/date, domain, target user, use case, region if relevant, and the *expected outcome*.
- Separate **promised behavior**, **reasonable user expectation**, **observed behavior** and **personal preference**. An unpopular design choice is not automatically a defect — check whether the maker announced it as a deliberate tradeoff.
- Decide the goal: *fix the existing thing*, *improve a workflow*, *create a competing offering* or *discover opportunities*. Record constraints (budget, skills, licenses, time, compatibility, safety).
- **Local files:** inspect only the current working project and files the user points to. Never recursively search home directories or unrelated folders. No claims about internals without evidence.

### 2. Collect contradictory as well as supporting evidence
- Primary sources first: official docs, changelogs/patch notes, known-issues pages, specs, repositories and issue trackers, support channels.
- Then user evidence: reviews, forums, discussions, defect reports, competitors, research. Weight recency and relevance; count distinct independent reports rather than repeated claims.
- Sample positive reviews and counterexamples so the loudest complaints don't become universal truths. Note sampling limits, small samples, brigading, selection bias, version drift.
- Commonly blocked sources (Reddit, Discord, X, paywalled reviews, sites returning 403): note the gap and fall back to the domain playbook's alternatives. Do not fabricate quotes, statistics, user counts, dates, features or links.
- Keep a compact evidence register as you go: claim · source · date · version · observed vs inferred · confidence.

### 3. Convert noise into real holes
- Cluster reports into unique problems; separate symptoms, root-cause hypotheses, desired outcomes and affected audiences.
- Classify: **defect**, **usability friction**, **missing capability**, **simulation/model imbalance**, **workflow failure**, **performance**, **accessibility**, **cost**, **integration**, **trust/compliance**, **underserved demand**.
- Assess frequency, severity, recurrence, impact, workaround burden and time sensitivity.
- Use 5 Whys for a causal chain; fishbone/fault-tree thinking for interacting causes. Root causes stay hypotheses until tested. Ask what would disprove each major claim and flag contradictions.

### 4. Solution check — mandatory in every mode
This step can't be skipped, shortened or traded for more evidence searches. It uses the **reserved** solution-check searches from the budget table, which can't be spent on anything else. Run it **after** you've drafted the hole list, so the searches can name the holes.

**Batch the holes so the check stays cheap.** Don't search hole by hole. Each search covers several holes at once by naming their key terms:
1. **Official channel (always):** one search for the maker's fixes, e.g. `<target> patch notes OR changelog OR roadmap <hole terms>`. It covers announced fixes, planned fixes and deliberate tradeoffs.
2. **Third-party channel (always):** one search for outside remedies, e.g. `<target> <hole terms> mod OR plugin OR tool OR workaround OR alternative` (swap in the domain's words: fork, extension, vendor, retrofit, service).
3. **Third reserved search (deep/repair/opportunity only):** use it on the highest-impact hole still OPEN or UNKNOWN, to look for competing products or abandoned and failed attempts.

Solutions that turn up in evidence searches count as well; note them as they appear. The reserved searches are still run, because a missing result has to come from a check that looked for fixes, not from evidence searches that weren't looking.

**Rules for the hole ledger:**
- Every hole gets a **Checked against** entry: the reserved search or source it was checked against.
- A hole that wasn't covered by a solution-check search **must** be UNKNOWN, written `UNKNOWN (unchecked)`. It can't be OPEN.
- A decision of ACT, PILOT or build needs its hole checked in **both** the official and the third-party channel. If that's missing, the strongest allowed decision is WATCH, plus the search that would settle it.

**Stopping rule:** once you find two credible, current, maintained solutions covering the core use case, mark the hole SOLVED or PARTIAL and don't spend more on it.

Before calling something a solution, check existence, current compatibility, maintenance, adoption, effectiveness, cost, licensing and limits — from search snippets or the solution's own page; deep testing is out of scope unless the user asks. Coverage labels, per hole:
- **SOLVED** — current, credible solution addresses the important use case.
- **PARTIAL** — meaningful remedy exists with measured shortcomings.
- **STALE** — existed, but compatibility/support/effectiveness is now doubtful.
- **OPEN** — no sufficient solution found after a documented search.
- **UNKNOWN** — evidence or access insufficient. Never convert UNKNOWN to OPEN or claim "nobody has done this."

A solution can exist and still leave an opportunity (too expensive, undiscoverable, incompatible, restricted). Name the *remaining* need precisely. Note which holes only the owner/vendor can fix (server-side logic, anti-cheat, firmware, regulated processes).

### 5. Evaluate the realistic intervention
For the most relevant OPEN/PARTIAL/STALE holes, compare: **adopt** an existing fix · **configure** without code · **extend/patch** (mod, plugin, wrapper) · **fork** (license permitting) · **build** · **abstain/watch**.

Score each on 1–5 with a one-line reason (no fake-precise market numbers): **Impact**, **Evidence strength**, **Unmet need**, **Feasibility**, **Risk**. Never average away a safety or legal blocker. Prefer the smallest effective intervention. Test for false positives: vocal minority, deliberate tradeoff, already-fixed version, non-problem for the target audience, complaint without real demand.

### 6. Hand off something executable
Recommend at most **three** primary actions plus a candid **kill/watch** option. Each recommendation needs: problem statement with sources and confidence · root-cause hypothesis and a falsification test · what already exists and why it falls short · minimal intervention and fallback · prerequisites, effort (labeled estimate), license/safety limits · implementation steps, rollback, maintenance risk · **acceptance test** (baseline, metric, success threshold, stop condition) · why it beats adopting an existing solution or doing nothing.

## Domain playbooks

Load **only** the one file that matches the target from `references/playbooks/`: `games.md`, `software.md`, `hardware.md`, `industrial.md`, `markets.md`, `repositories.md`. If none fits, use the closest one and skip the rest.

## Output

Load **only** the template for the current mode from `references/templates/` (see the budget table). Don't read the other templates. Open with a direct answer to **"Is there a meaningful unfilled hole worth acting on?"**

If file tools are available, save the report as `reports/findhole/<target-slug>-YYYY-MM-DD.md` in the current working project (add `-r2`, `-r3` rather than overwriting). Otherwise deliver it in chat. In the chat reply, give a short summary of the verdict and top actions — don't repeat the whole report.

## Guardrails

- **Research only by default.** Do not install mods, patch binaries, change production systems, place orders, publish code or make external changes unless the user explicitly authorizes implementation. Writing the report is allowed.
- Investigate lawfully; respect licenses, DRM, privacy, EULAs and access controls. Never defeat anti-cheat, DRM or access restrictions, and don't recommend workarounds that do.
- For industrial, medical, safety-critical or regulated subjects, separate hypothesis from validated process; no direct deployment before a qualified professional approves testing, compliance and change control.
- Label fixes **proposed**, **tested** or **validated in deployment**. Never present an untested fix as working.
- A finite search never proves nonexistence. Report where you searched and as of when.
- Prefer honest, practical recommendations over impressive complexity.
