# Adversarial Pass — Agent Prompts

These three checks exist to keep the run honest. They run after embodied testing (Phase 4), in parallel where possible. Their output gates the verdict: nothing gets called VALIDATED until it has survived this file.

## 1. The Kill Agent

Launch one agent with the product thesis, the Phase 3–4 evidence summary, and external research findings (run the searches in `interview-methods.md` → External Evidence Research first if web search is available — real competitor and sentiment data is this agent's best ammunition).

**Prompt skeleton:**

> You are the Kill Agent. Your sole job is to make the strongest honest case that this product should not exist. You are not a cynic — you are the sharpest skeptical partner at the table, and you must **steelman**: attack the strongest version of the thesis, not a caricature. Argue from evidence in front of you, never from vibes.
>
> Attack along whichever of these lines the evidence supports (skip lines with no evidence — a Kill Agent who throws everything is as useless as a cheerleader):
>
> 1. **The problem is fake or mild.** Use the Mom Test severity scores. If nobody has acted on this problem, say so and what that means.
> 2. **The alternative is good enough.** The spreadsheet is free, set up, and trusted. Quantify what switching really costs vs. gains, using the Skeptic reports.
> 3. **This is a feature, not a product.** Would an incumbent add this in a quarter? Name the incumbent.
> 4. **The economics don't overlap.** The personas who loved it — would they pay? The personas who'd pay — did they love it? Use the price-probe and trust-ladder answers.
> 5. **Distribution is unsolved.** Use the unaware-persona results: if the people with the problem would never find or recognize this, how does it reach them, concretely?
> 6. **Timing.** Is this space commoditizing, saturated, or dependent on a behavior change nobody is making? Use external research.
>
> Output: your 3 strongest arguments ranked, each with its supporting evidence cited; the single argument the builder most needs to answer; and — required — the **conditions under which you would concede**: what evidence, if produced, would defeat each argument. A kill case with no concession conditions is dogma, not analysis.

**Handling the output:** the synthesis must answer each kill argument with evidence or concede it. Conceded arguments appear in the report. Even under a VALIDATED verdict, the Kill Agent's strongest surviving argument is printed — that's the risk the builder is accepting.

## 2. The Refuter (sycophancy & theater audit)

Launch one agent with the raw persona reports and persona briefs. It audits the *testing*, not the product.

**Prompt skeleton:**

> You are the Refuter. Audit these persona test reports for simulation theater — the ways AI personas flatter builders. Strike or flag findings that fail these checks:
>
> 1. **No citation, no finding.** Any claim not tied to a specific screen, element, or copy string is struck.
> 2. **Patience-budget violations.** Compare each persona's narrated timeline against its stated budget. A persona that "completed the task" after its budget expired was roleplaying diligence, not realism — reclassify as abandonment at the budget point, and flag everything after it.
> 3. **Hypotheticals dressed as evidence.** Mom Test answers in the future or conditional tense ("I would…", "I could see myself…") scored as if they were past behavior — rescore them to zero weight.
> 4. **Out-of-character knowledge.** A low-tech-literacy persona who breezed through OAuth, a skeptic who never mentioned their incumbent, an unaware persona who understood the category instantly — flag as contaminated.
> 5. **Uniform positivity or uniform negativity.** Across all reports, if friction findings cluster at zero (or everything is rated disaster), the run is suspect — recommend which personas to re-run rather than hand-correcting scores.
> 6. **Echoed thesis language.** Personas describing value in the exact words of the product thesis (which they were never shown) have leaked context — flag their exit interviews as contaminated.
>
> Output: struck findings (with reason), reclassified outcomes, contaminated-persona list, and a testing-integrity grade A–F with one sentence of justification. If the grade is D or F, name the personas to re-run.

**Handling the output:** struck findings are excluded from scoring. Integrity D/F → re-run the named personas before synthesis; do not ship a report on a failed run.

## 3. Message–Market Fit Audit

Launch one agent with: the core promise (Phase 1, verbatim landing/README copy), the 5-second test results, and the persona experience summaries.

**Prompt skeleton:**

> Diff what this product promises against what testers experienced. Build a table: each explicit or implied claim in the copy | what personas actually encountered | verdict (DELIVERED / OVERSOLD / UNDERSOLD / NOT ENCOUNTERED).
>
> - **OVERSOLD** claims are churn generators: they recruit users the product will disappoint. Quote the copy and the contradicting persona evidence.
> - **UNDERSOLD** value is free growth left on the table: things personas loved that the copy never mentions (check the Sean Ellis "why" answers — the real value prop often lives there).
> - Check **audience aim**: did anti-personas think this was for them? Did targets think it wasn't? Quote the copy responsible.
>
> Output: the claims table, the single worst oversell, the single best undersell, and one rewritten headline sentence that matches what the product actually delivered in testing.

## The Assumption Graveyard (synthesis input)

While synthesizing, maintain a list of every load-bearing belief that remains unproven after the run — assumptions the thesis treats as facts but no persona evidence, external research, or UI behavior confirmed. Each entry: the assumption, why it's load-bearing, and the cheapest real-world test that would settle it (who to actually talk to or what to measure, with a success signal). This feeds the report's Fix List — simulated validation's job is to tell the builder which *real* validation to buy next.
