---
name: reality-check
description: >-
  Product validation and demographic testing. Spawns parallel persona agents that
  interview like The Mom Test, walk your app's UI as real users across target,
  adjacent, anti-persona, skeptic, and unaware demographics, then adversarially
  synthesize a scored verdict on whether what you're building is actually useful.
  Use when the user asks to validate a product/app/idea, test it against users or
  demographics, check product-market fit, run a reality check, or asks "is this
  actually useful?" Works on live URLs, local apps, screenshots, or just a spec.
---

# Reality Check — Product Validation & Demographic Testing

You are about to answer the question every builder avoids: **is this thing actually useful, and for whom?**

Your job is NOT to make the builder feel good. Compliments are worthless data (The Mom Test, rule #1). Your job is to find the truth about this product before the market does — cheaply, in minutes, using parallel persona agents instead of weeks of user interviews.

**Anti-sycophancy contract:** Every phase below has an adversarial counterweight. If your findings are all positive, you have failed — not because every product is bad, but because every product has friction, and a validation run that finds none wasn't looking. A "validated" verdict must survive the Kill Agent (Phase 5) to be issued.

## Reference files (read as needed, not all upfront)

- `references/persona-library.md` — the 5 demographic categories, archetype templates, context/accessibility overlays
- `references/interview-methods.md` — The Mom Test rules, Sean Ellis test, JTBD interview script, 5-second test
- `references/scoring-rubric.md` — the 6 scored dimensions with anchored 0–100 scales
- `references/adversarial-prompts.md` — Kill Agent, Refuter pass, message–market fit audit
- `references/report-template.md` — final verdict report format

## Phase 0 — Detect what you can test (fidelity mode)

Determine the highest-fidelity input available, in this order:

1. **LIVE** — A URL the user gave you, or a local app you can run (check for dev-server scripts, then start it). If browser automation tools are available (Claude in Chrome, Playwright MCP, agent-browser), personas will actually operate the UI.
2. **VISUAL** — Screenshots, Figma frames, or recordings provided or discoverable in the repo. Personas evaluate real pixels but can't interact.
3. **CODE** — A codebase with UI code. Personas reconstruct the experience from routes, components, copy strings, and onboarding flow code.
4. **CONCEPT** — Only a spec, README, or idea description. This is **pre-build validation** — the cheapest kind. Personas validate the problem and the proposed solution; UI findings are out of scope.

Tell the user which mode you're in and what that limits. Never silently pretend CODE mode findings are usability-tested. In LIVE mode, confirm with the user before testing anything that costs money, sends real emails/messages, or mutates production data — prefer a staging/local instance.

## Phase 1 — Extract the product thesis

You cannot validate against goals that were never stated. Produce a **Product Thesis** and show it to the user before testing:

- **Problem:** What pain does this solve? (One sentence, no solution words in it.)
- **For whom:** The intended user, specifically. "Everyone" is a red flag — note it as one.
- **Today's alternative:** What do those people do right now instead? (The real competitor is usually a spreadsheet, a group chat, or doing nothing.)
- **Core promise:** What the landing page / README / app store copy actually claims.
- **Success behavior:** The one observable UI behavior that proves value, e.g. "a first-time user books a slot in under 2 minutes." If the user hasn't defined this, propose one and confirm.
- **Riskiest assumption:** The single belief that, if wrong, kills the product. Test this first and hardest.

Source it from the README, landing copy, onboarding screens, and the user's own words. Where the sources disagree with each other, that contradiction is already **Finding #1**.

If the user is present, confirm the thesis in one quick exchange. If running autonomously, state your derived thesis and assumptions explicitly in the report.

While talking to the user, quietly gauge **builder confidence** (do they acknowledge risk, or is every answer upside?). This calibrates the final report's tone — never its evidence or scores. See `references/interview-methods.md`.

## Phase 2 — Build the persona matrix

Read `references/persona-library.md`. Instantiate personas across all five categories — the spread is the point; testing only fans is how products die surprised:

| Category | Question they answer | Quick mode | Deep mode |
|---|---|---|---|
| **Target** | Does it serve the people it's for? | 2 | 3–4 |
| **Adjacent** | How far does fit extend past the bullseye? | 1 | 2–3 |
| **Anti-persona** | Does it waste or harm the people it's NOT for? | 1 | 2 |
| **Skeptic** | Is it better *enough* to beat their current workaround? | 1 | 2–3 |
| **Unaware** | Would someone with the problem even recognize this as the solution? | 1 | 2 |

Default to **quick mode (6 personas)**; use **deep mode (12–15)** when the user asks for thorough/comprehensive validation. Apply at least two **overlays** from the library per run (e.g. screen-reader user, non-native English speaker, mobile-on-commute, low bandwidth) — accessibility and context are demographics, not edge cases.

Each persona gets a self-contained brief: name, demographics, tech comfort, device + context of use, their version of the problem (or lack of it), what they do today, patience budget (e.g. "90 seconds before closing the tab"), and their task.

## Phase 3 — Mom Test interviews (problem validation, product hidden)

Read `references/interview-methods.md`. **Before any persona sees the product**, run each through a Mom Test–style interview about their life. This separates "is the problem real?" from "does the app work?" — products fail on both, independently, and conflating them produces useless findings.

Each persona agent answers, in character, grounded in realistic specifics:

1. When did you last encounter [the problem]? Walk me through exactly what happened.
2. What did it cost you (time, money, embarrassment)?
3. What did you do about it? What have you tried before? What happened to those attempts?
4. Have you ever paid — in money or setup effort — to solve this?

**Mom Test rules for interpreting answers:** past behavior is evidence; hypotheticals ("I would totally use that") are worthless; "that's cool" is worthless; someone who has never attempted to solve the problem does not have the problem, whatever they claim. Score each persona's problem severity 0–10 from *evidence of past behavior only*.

If target personas average below 4 here, the riskiest assumption just failed — the rest of the run is measuring the usability of a solution to a problem people don't have. Continue, but say so plainly.

## Phase 4 — Embodied UI testing (parallel)

Launch persona agents **in parallel** (batch the Task/Agent tool calls in a single message; if subagents are unavailable, run personas sequentially yourself, fully in character, one at a time). Each agent receives: its persona brief, the product thesis, the fidelity mode and how to access the product, and this protocol:

1. **5-second test.** Look at the first screen only. What is this? Who is it for? What would you do first? (Unaware personas: would you ever have found this page at all?)
2. **Attempt your task** under your constraints and patience budget. In LIVE mode, actually operate the UI. Narrate honestly — confusion, hesitation, delight, the moment you'd give up. When your patience budget runs out, *say you abandoned and where*; finishing the task anyway is a protocol violation.
3. **Log friction with evidence.** Every finding must cite a specific screen, element, or copy string — "the signup wall appears before any value is shown" — never vibes. A finding without a UI citation gets discarded in synthesis.
4. **Measure time-to-value.** Count screens, fields, and decisions between arrival and the thesis's success behavior. Note the exact point of first real value.
5. **Exit interview** (answer in character, honestly):
   - **Sean Ellis:** How would you feel if you could never use this again — very disappointed / somewhat / not disappointed? Why?
   - **Switching:** What do you do today, and is this better *enough* to change? What would switching cost you?
   - **Trust ladder:** Would you give this your email? Payment details? Your data? Where does yes become no?
   - **Price probe:** At what price does this become a no? (Disbelieve your own "I'd pay anything.")
   - **Retention:** It's next Tuesday. What would actually make you open this again? ("Nothing would" is a valid, important answer.)
   - **Net benefit** (anti-personas especially): Did this app solve more than it cost you — or did it add challenges it then charged you attention to manage?

Each agent returns a structured result: persona id, task outcome (completed / abandoned-at-X / blocked), friction log with citations, time-to-value, exit-interview answers, and dimension scores per `references/scoring-rubric.md`.

## Phase 5 — Adversarial pass

Read `references/adversarial-prompts.md`. First, if web search is available, run the **external evidence research** from `references/interview-methods.md` (3–8 searches: competitors/alternatives, real user sentiment on Reddit/forums, demand and timing signals) — simulated personas are a proxy for user research, and real-market evidence both grounds the Skeptic verdicts and arms the Kill Agent. If search is unavailable, note that in the report.

Then run three checks (in parallel where possible):

1. **The Kill Agent.** One agent argues this product should not exist: the problem is fake or mild, the alternative is good enough, this is a feature not a product, the demographics who'd pay don't overlap the demographics it serves. It must steelman — attack the strongest version of the thesis using the Phase 3–4 evidence.
2. **The Refuter.** Audits the persona findings for sycophancy and theater: findings without UI citations, personas who completed tasks past their stated patience budget, suspiciously uniform positivity, Mom Test answers that are hypotheticals dressed as evidence. Refuted findings are struck.
3. **Message–market fit audit.** Diff the core promise (Phase 1) against what personas actually experienced (Phase 4). Every gap between promise and delivery is a churn generator, even when the product is good.
4. **Compliance & security pass** (read `references/compliance-security.md`) — run whenever the product collects user data, which is almost always. Three parts: a data-regulation applicability scan (build the data inventory from code, then flag plausibly applicable regimes — GDPR/CCPA/COPPA/PCI, app-store data labels, AI-disclosure rules); a policy-vs-product diff (every "never shared"/"you can delete" promise checked against the actual code); and a security baseline. For the security baseline, **delegate when possible**: if Cloudflare's `security-audit` skill, Claude Code's `/security-review`, or a security MCP tool is available in the environment, run that and fold its confirmed findings in; otherwise run the built-in fallback checklist. Frame all output as an engineering-grade flag pass, not legal advice. A CRITICAL finding here blocks a VALIDATED verdict and caps Trust & Net Benefit at 40.

## Phase 6 — Synthesis & verdict

Score the six rubric dimensions from surviving evidence only, then issue exactly one verdict per `references/report-template.md`:

- **VALIDATED** — real problem, target personas succeed and would return; survived the Kill Agent. (Rare. Be suspicious of yourself if you issue it.)
- **WEAK SIGNAL** — problem is real but the product leaks value: friction, time-to-value, or switching costs are eating it. List the fixes, prioritized by (personas affected × severity).
- **NOT VALIDATED** — problem or solution failed on the evidence. Say which, and show the evidence.
- **PIVOT SIGNAL** — the strongest signal came from somewhere unexpected: an adjacent persona, a different problem, one feature that outperformed the whole. Name the pivot concretely.

The report must include the persona-fit matrix, the Kill Agent's strongest surviving argument (even under VALIDATED), the **Assumption Graveyard** (load-bearing beliefs still unproven, each with its cheapest real-world test), a **Fix List** (≤6 items: weakness → concrete action → success signal), and the scored rubric — scores make re-runs comparable, so after the user ships fixes they can run `/reality-check` again and watch the numbers move instead of re-arguing vibes.

**Deliverable format.** Always present the full report in the conversation. When an artifact or web-page rendering tool is available (e.g. Claude Code's Artifact tool), ALSO render the report as a single shareable page: a verdict banner with the composite score, the scorecard with gate thresholds visible, the persona-fit matrix, evidence-cited findings — and a **Solutions section** that expands every Fix List row into an implementation-ready remediation: the diagnosis, the prescribed change at the file/screen/copy level, who it unblocks, and the success signal. Findings diagnose; solutions prescribe — the artifact must contain both, so a teammate who never saw the run can act on it. No rendering tool → write the same page to a local HTML/markdown file and tell the user where it is.

End with the single highest-leverage next action. One. Not a list of twenty.
