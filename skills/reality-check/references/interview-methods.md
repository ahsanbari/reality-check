# Interview & Verification Methods

The validated toolkit this skill is built on. Each method exists because builders systematically fool themselves in a specific way; each one blocks a specific lie.

## The Mom Test (Rob Fitzpatrick)

**The lie it blocks:** people — especially people who like you, including AI personas trying to be agreeable — will praise your idea to your face. Your mom will say your app is lovely. That data is worthless.

**The three rules:**
1. **Talk about their life, not your idea.** The product stays hidden for the entire problem interview (Phase 3). The moment a persona knows what you're building, their answers start performing for it.
2. **Ask about specifics in the past, not opinions about the future.** "When did this last happen? Walk me through it" — never "would you use something that…?" The future tense is where bad data lives.
3. **Talk less, dig more.** Every answer gets a follow-up: what did that cost you? what did you do next? why haven't you fixed it already?

**Interpreting answers — the evidence hierarchy:**

| Answer | Worth |
|---|---|
| "I built a spreadsheet / pay for a tool / have a workaround ritual" | Gold. They've already spent to solve it. |
| "Last Tuesday it cost me two hours and I missed a deadline" | Strong. Specific, recent, costly. |
| "Yeah, it's annoying sometimes" | Weak. Mild problems don't move behavior. |
| "That's really cool, I'd definitely use that" | **Zero.** Compliment + hypothetical. Discard. |
| Has never attempted to solve it | They do not have the problem, whatever they say. |

**Scoring:** problem severity 0–10 per persona, from past-behavior evidence only. Anchors: 0 = never thinks about it; 4 = complains but has never acted; 7 = has a maintained workaround; 10 = has paid money or burned real hours trying to fix it.

## Sean Ellis PMF Test

Asked in every Phase 4 exit interview: **"How would you feel if you could never use this again?"** — very disappointed / somewhat disappointed / not disappointed.

The real-world benchmark is 40%+ "very disappointed" among people who actually experienced the product's core value. Count only personas who *reached* the success behavior — a persona who abandoned at the signup wall isn't disqualified data, but they belong in the funnel finding, not the PMF denominator. Always ask **why** — the "why" behind "very disappointed" is the product's true value prop, which frequently differs from the thesis.

## Jobs-to-be-Done (JTBD)

People hire products to make progress in a situation; they don't buy features. Every persona task must be written as a job with a situation and a desired outcome:

> When [situation], I want to [motivation], so I can [outcome].
> *When a client ghosts an invoice, I want to chase it without feeling awkward, so I can get paid without damaging the relationship.*

If a persona can't state the job the product was hired for after using it, that is a finding. Also probe the **forces diagram** in exit interviews: push of the current problem, pull of the new solution, **anxiety** about the new, **habit** of the old. Products fail when anxiety + habit outweigh push + pull — which is exactly what the Skeptic persona measures.

## 5-Second Test

Persona sees the first screen for five seconds (one screenshot, no scrolling), then answers: What is this? Who is it for? What can you do here? What would you click first?

Measures comprehension, not usability. Unaware personas failing it is expected and still informative; **target personas failing it is an emergency** — the product may be good and invisible at the same time.

## Nielsen's Usability Heuristics (friction-log vocabulary)

Persona agents report friction in plain language; synthesis tags findings with the violated heuristic so patterns surface across personas: visibility of system status · match to the real world (jargon) · user control (undo, escape) · consistency · error prevention · recognition over recall · flexibility · minimalist design · good error messages · help/documentation. Three personas hitting the same heuristic on different screens is a systemic finding, not three local ones.

## Builder-Confidence Calibration

During Phase 1, gauge how certain the builder sounds: do they acknowledge risk and unknowns, or is every answer upside? Calibrate the **tone** of the final report accordingly — balanced-and-constructive for the self-aware, direct-and-firm for the mostly-sure, unsparing for the certain. The *evidence and scores never change* with tone; only how bluntly the conclusion is stated. The more confident the builder, the less they'll hear a hedge.

## External Evidence Research (grounding beyond simulation)

Simulated personas are a fast proxy for user research — not a replacement. When web search is available, ground the simulation in reality (feeds Skeptic briefs and the Kill Agent):

- **Competitors/alternatives:** `[problem space] app`, `[problem space] alternatives` — name the incumbents the Skeptic actually uses.
- **Real user sentiment:** `site:reddit.com [problem]`, forum threads — do real people describe this pain, in what words, and what do they already use?
- **Demand & timing signals:** has anything in this space been funded, shut down, or commoditized recently?

3–8 searches, stop when new searches repeat old information. Real Reddit complaints that match the thesis are strong problem validation; a crowded field of free alternatives is the Skeptic's strongest ammunition. If search is unavailable, say so in the report and mark external grounding as not performed.

## The honesty floor

Every method above exists to stop the simulation from flattering the builder. The corresponding rule for this skill: **a validation run whose findings are uniformly positive is a failed run.** Real products — including great ones — generate friction findings. If none surfaced, the personas weren't honest, the tasks weren't real, or the patience budgets weren't enforced; re-run, don't report.
