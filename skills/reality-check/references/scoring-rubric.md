# Scoring Rubric

Six dimensions, 0–100 each, anchored so that a re-run after changes is comparable to the last run. Scores are computed at synthesis from surviving evidence only — never averaged from persona self-reports alone, and never from findings the Refuter struck.

**Why anchors matter:** without them, scores drift with the mood of the run and re-runs can't be compared. Score against the anchor descriptions, not against your overall impression. When a score falls between anchors, interpolate and say why.

## 1. Problem–Solution Fit — *is the problem real, and does this solve it?*

Evidence: Phase 3 Mom Test severity scores (past behavior only), external research (real complaints, existing spend), whether the success behavior actually addresses the interviewed pain.

- **90+** Target personas have paid or burned hours on this; the product's success behavior directly kills that pain.
- **70** Problem is real for most targets; solution addresses it partially or indirectly.
- **50** Problem is real but mild — complaints without action. Solution works but relieves little.
- **30** Only early-adopter targets show real pain; mainstream targets shrug.
- **10** Nobody interviewed has ever acted on this problem. The product solves a hypothesis.

## 2. Usability — *can each persona complete their job?*

Evidence: task outcomes, friction logs with citations, heuristic-tagged patterns, overlay-persona results. **Note the fidelity mode** — usability scored in CODE mode is an estimate and must be labeled as one; in CONCEPT mode, don't score this dimension at all (mark N/A).

- **90+** All target + adjacent personas complete their jobs inside their patience budgets; overlays succeed; friction is cosmetic.
- **70** Targets complete with recoverable friction; at least one adjacent or overlay persona struggles seriously.
- **50** Targets complete but burn most of their patience; abandonment points exist on the main path.
- **30** Some target personas abandon before the success behavior.
- **10** The core job cannot be completed by most personas.

## 3. Time-to-Value — *how fast does a new user reach the point?*

Evidence: screens/fields/decisions counted between arrival and the success behavior; where first real value appeared; whether signup is demanded before any value is shown.

- **90+** Value visible before any commitment; success behavior reachable in the first session with minutes to spare on every patience budget.
- **70** Success behavior reached first session, but a signup/setup wall stands before any demonstrated value.
- **50** Reaching value requires setup effort that only motivated targets survived.
- **30** Most personas' patience budgets expired before first value.
- **10** Value requires multi-session investment with nothing shown up front.

## 4. Switching Case — *beats the incumbent, including "do nothing"?*

Evidence: Skeptic persona verdicts, JTBD forces (push + pull vs anxiety + habit), concrete switching costs named, external research on free alternatives.

- **90+** Skeptics said they'd migrate — and named what they'd abandon to do it.
- **70** Skeptics see clear superiority but balk at a nameable switching cost (data migration, team buy-in). Fixable.
- **50** "Neat, but my spreadsheet is fine." Better, not better *enough*.
- **30** Parity with the incumbent at a higher cost in habit change.
- **10** The incumbent is better, or free does the same job.

## 5. Trust & Net Benefit — *does it earn what it asks, and give more than it takes?*

Evidence: trust-ladder answers (email → payment → data), price probes, anti-persona net-benefit reports, greedy-permissions findings, privacy-defensive overlay results.

- **90+** Personas volunteer trust at the level the product asks; anti-personas exit cleanly and unburdened; price lands in the believable range.
- **70** Trust granted, but with hesitation findings (asks for data before explaining why; unclear pricing).
- **50** The product asks for more trust than it has earned at the point it asks; some personas balked there.
- **30** Anti-personas report net harm (noise, dark patterns, effort) — or targets wouldn't give it a payment method at any price tested.
- **10** The product's demands (data, money, attention) exceed its delivered value for most personas.

## 6. Message–Market Fit — *does the promise match the delivery?*

Evidence: 5-second test results per category, Phase 5 promise-vs-experience diff, unaware-persona comprehension, discoverability assessment.

- **90+** Targets pass the 5-second test; the experience delivers what the copy promises; anti-personas correctly self-select out.
- **70** Targets understand it, but the copy over- or under-promises relative to Phase 4 experience in specific, quotable ways.
- **50** Targets need exploration to understand what this is; the unaware stand no chance.
- **30** Personas who should be in think it's not for them — or vice versa.
- **10** The 5-second test fails across categories; promise and product describe different things.

## Composite & verdict gates

Report all six (with N/A where fidelity mode forbids scoring) plus a weighted composite: **Problem–Solution Fit ×2** (nothing else matters if it fails), all others ×1.

Compliance & security wiring: CRITICAL findings from the compliance & security pass (see `references/compliance-security.md`) cap Trust & Net Benefit at 40 and block VALIDATED outright; HIGH findings are scored evidence inside Trust & Net Benefit.

Gates, applied after the Kill Agent survives review:

| Verdict | Requirement |
|---|---|
| **VALIDATED** | Composite ≥ 70 **and** Problem–Solution Fit ≥ 70 **and** no dimension < 40 |
| **WEAK SIGNAL** | Problem–Solution Fit ≥ 60 but another dimension < 40 — real problem, leaking product |
| **NOT VALIDATED** | Problem–Solution Fit < 50, or composite < 45 |
| **PIVOT SIGNAL** | Headline thesis fails a gate, but a persona/feature/problem subset scored ≥ 75 — name it |

Record scores in the report's score table with the run date, so the next run diffs against this one.
