# Verdict Report Template

The final deliverable. Write it in this order — verdict first, evidence after. Calibrate tone to builder confidence (see `interview-methods.md`): the evidence and scores never bend, only the bluntness of the prose. Keep it honest, specific, and quotable; no finding without its citation.

---

```markdown
# Reality Check: [Product Name]
*Run date: [date] · Fidelity mode: LIVE/VISUAL/CODE/CONCEPT · Personas: N (quick/deep) · External research: performed / unavailable*

## Verdict: [VALIDATED | WEAK SIGNAL | NOT VALIDATED | PIVOT SIGNAL]

[2–4 sentences. The one-line verdict rationale, the decisive evidence, and — if
WEAK SIGNAL or PIVOT — the single thing that would change the verdict.]

**The strongest surviving case against this product** (printed under every verdict):
[The Kill Agent's best argument that synthesis could not fully answer, and what
evidence would settle it.]

## Scorecard

| Dimension | Score | Previous run | One-line evidence |
|---|---|---|---|
| Problem–Solution Fit (×2) | /100 | — | |
| Usability | /100 or N/A | — | |
| Time-to-Value | /100 | — | |
| Switching Case | /100 | — | |
| Trust & Net Benefit | /100 | — | |
| Message–Market Fit | /100 | — | |
| **Weighted composite** | **/100** | — | |

*(First run: leave "Previous run" as —. Re-runs: fill it and bold movements ≥10 points.)*

## Product Thesis (as tested)

Problem · For whom · Today's alternative · Core promise · Success behavior ·
Riskiest assumption — one line each, plus any contradictions found between sources.

## Persona-Fit Matrix

| Persona | Category | Overlay | Problem severity (0–10) | Task outcome | Time-to-value | Sean Ellis | Would return? |
|---|---|---|---|---|---|---|---|
| | | | | completed / abandoned@[where] / blocked | | very/somewhat/not | yes / no / "nothing would bring me back" |

[One paragraph: the pattern this matrix shows. Where does fit end? Which
category surprised you?]

## What Actually Happened (top findings, by leverage)

Ordered by (personas affected × severity). Each: **finding → evidence (screen/
element/copy, persona(s)) → heuristic tag if applicable → why it matters.**
Include the genuine delights with the same evidence standard — the Sean Ellis
"why" answers usually live here, and they are the product's real value prop.

## Message–Market Fit

The claims table (DELIVERED / OVERSOLD / UNDERSOLD / NOT ENCOUNTERED), the worst
oversell, the best undersell, and the rewritten headline that matches what
testing actually delivered.

## Mom Test Summary (problem validation)

Per category: average severity from past-behavior evidence, the strongest single
piece of evidence the problem is real, and the strongest evidence it isn't.
State plainly if the problem failed validation and the rest is usability data.

## Compliance & Security

Data inventory in one paragraph (what's collected, where it flows, incl. AI
vendors). Flagged-regimes table. Findings by severity (CRITICAL/HIGH/MEDIUM),
each with evidence citation and remediation sketch. Name what was delegated
(e.g. Cloudflare security-audit, /security-review) vs. run via the fallback
checklist. Standing caveat: engineering-grade flag pass, not legal advice —
CRITICAL/HIGH items are "ask a professional now" markers.

## Assumption Graveyard

| Unproven assumption | Why it's load-bearing | Cheapest real-world test | Success signal |
|---|---|---|---|

## Fix List (next 30 days)

Max 6, ordered by leverage. No generic advice — name the screen, the copy, the
person to talk to.

| Weakness | Concrete action | Success signal |
|---|---|---|

## Testing Integrity

Refuter grade: [A–F]. Findings struck: N. Personas re-run: [list or none].
Fidelity caveats: [e.g. "Usability scored from CODE mode — treat as estimate
until a LIVE run."] External research: [N searches / not available this run].

---

### The one thing

[One sentence. The single highest-leverage action. Not a list. If the builder
does nothing else, this.]
```

---

## Rules for writing it

1. **Verdict first, always.** The builder will read the first three lines with their heart rate up. Don't bury the answer.
2. **Movement over absolutes on re-runs.** A 58 that was a 41 last run is a product getting better; say that before dissecting the 58.
3. **Quote personas verbatim** where their words are sharper than yours. "I closed the tab when it asked for my card before showing me anything" outperforms any paraphrase.
4. **VALIDATED is earned, not default.** If you feel pulled toward it, re-read the Kill Agent's output first. The gates in `scoring-rubric.md` are the law.
5. **Offer the re-run.** Close by telling the user: fix the top items, run `/reality-check` again, and watch the scorecard's "Previous run" column — that's the loop that makes this a practice instead of a one-time roast.
6. **Render the shareable artifact.** When an artifact/web-page tool is available, publish the report as a single self-contained page alongside the chat version. Structure it for scanning (verdict and scores before detail, severity encoded visually, gate thresholds marked on the score bars) and expand the Fix List into full **solution cards** — for each: the diagnosis (one line, cited), the prescribed change at file/screen/copy level, which persona(s) it unblocks, and the success signal that proves it worked. The chat report says what's wrong; the artifact is the handoff document a teammate fixes things from.
