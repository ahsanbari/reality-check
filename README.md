# Reality Check

### Product validation & demographic testing for Claude Code

> You built it. But should you have? And for whom?

**Reality Check** is a Claude Code skill that answers the question every builder avoids. It spawns a panel of parallel persona agents — spanning the people your product is for, the people it isn't, and the people who'd never know it exists — interviews them [Mom Test](http://momtestbook.com/)-style about their actual lives *before* they ever see your product, then sends them into your UI to attempt real jobs under real constraints. An adversarial pass (a Kill Agent, a sycophancy Refuter, a promise-vs-delivery audit) stress-tests every finding before you see a verdict.

The output is one of four honest answers — **VALIDATED · WEAK SIGNAL · NOT VALIDATED · PIVOT SIGNAL** — backed by a scored rubric you can re-run after every change to watch the numbers move.

Most validation tools ask *you* the questions, and you answer them optimistically because you already believe. Reality Check asks your *users* — all five kinds of them — and doesn't let any of them be polite.

---

## How it works

```
Phase 0  Detect fidelity ──── live app · screenshots · code · just a spec
Phase 1  Product thesis ───── problem, for whom, today's alternative,
                              success behavior, riskiest assumption
Phase 2  Persona matrix ───── 5 demographic categories + a11y/context overlays
Phase 3  Mom Test interviews ─ problem validation, product hidden
Phase 4  Embodied UI testing ─ parallel agents walk your app in character
Phase 5  Adversarial pass ──── Kill Agent · Refuter · message–market audit
                              + external research (competitors, Reddit, signals)
Phase 6  Verdict ───────────── scored rubric, fix list, one next action
```

### The five demographics

| Who | The question they answer |
|---|---|
| 🎯 **Target** | Does it serve the people it's for? |
| 🔭 **Adjacent** | How far does fit extend past the bullseye? |
| 🚫 **Anti-persona** | Does it waste or harm the people it's *not* for? |
| 🧾 **Skeptic** | Is it better *enough* to beat the spreadsheet they already use? |
| 🌫️ **Unaware** | Would someone with the problem even recognize this as the solution? |

Plus stacked **overlays** that are demographics, not edge cases: screen-reader users, color-blind users, one thumb on a commuter train, low bandwidth, non-native English, low tech literacy, privacy-defensive, 90-second-session parents.

### The honesty machinery

Simulated users have one failure mode: they flatter you. Reality Check is built around preventing that.

- **The Mom Test, enforced** — personas are interviewed about their past behavior before the product is revealed. "I'd totally use this" scores zero. "Last Tuesday it cost me two hours" scores.
- **Patience budgets** — every persona has one ("90 seconds to see the point, then gone") and the Refuter reclassifies any persona who heroically finished a task after theirs expired.
- **No citation, no finding** — friction must name the screen, element, or copy string. Vibes are struck.
- **The Kill Agent** — one agent steelmans the case that your product shouldn't exist, and must also state what evidence would make it concede.
- **The gates** — VALIDATED requires surviving all of the above *and* clearing score thresholds. If a run comes back with zero friction findings, the run failed, not the product.

### Built-in methods

The Mom Test (Fitzpatrick) · Sean Ellis PMF test · Jobs-to-be-Done + forces of progress · 5-second test · Nielsen's usability heuristics · trust-ladder & price probes · retention ("it's next Tuesday — would you open this?") · external evidence research (competitors, Reddit sentiment, timing signals) · Assumption Graveyard with the cheapest real-world test for each unproven belief.

---

## Install

**Claude Code (recommended):**

```bash
# Personal — available in every project
git clone https://github.com/ahsanbari/reality-check.git
mkdir -p ~/.claude/skills
cp -r reality-check/skills/reality-check ~/.claude/skills/

# Or per-project
cp -r reality-check/skills/reality-check your-project/.claude/skills/
```

Then in any session:

```
/reality-check
```

…or just ask naturally: *"is this app actually useful?"*, *"validate this product"*, *"run a reality check on this"*, *"test this against different user demographics"*.

**Claude Desktop / claude.ai:** zip the `skills/reality-check` folder and upload it under Settings → Capabilities → Skills.

## Use it on

- **A live app** — personas drive the real UI via browser automation (best fidelity)
- **A local project** — Reality Check starts your dev server and tests it
- **Screenshots or Figma frames** — real pixels, no interaction
- **Just a spec or README** — pre-build validation, the cheapest kind there is

It auto-detects the best available mode and tells you what that mode can and can't claim.

## What you get

A verdict report with: the verdict and the strongest surviving case *against* your product (printed even when you pass) · a six-dimension scorecard with a "previous run" column · a persona-fit matrix · evidence-cited findings including the genuine delights · a promise-vs-delivery claims table · the Assumption Graveyard · a ≤6-item fix list with success signals · and exactly one highest-leverage next action.

Fix the top items, run it again, watch the scores move. Validation becomes a loop, not a one-time roast.

## Honest limitations

Simulated personas are a fast, cheap *proxy* for user research — not a replacement for talking to ten real humans. Reality Check is designed around that: the Mom Test structure, the Refuter, and external research keep the simulation honest, and the Assumption Graveyard explicitly tells you which beliefs still need *real-world* testing and the cheapest way to buy each answer. Use it to walk into real user conversations already knowing where the bodies are buried.

## Credits & prior art

- *The Mom Test* — Rob Fitzpatrick
- Sean Ellis PMF survey · Jobs-to-be-Done (Christensen/Moesta) · Nielsen Norman heuristics
- [shaadahmade/reality-check](https://github.com/shaadahmade/reality-check) — a kindred idea-stage validation skill whose external-research phase, fix-list format, and confidence calibration influenced this one. That skill critiques your *idea* via market research; this one tests your *built product* via demographic persona agents. They pair well.

## License

MIT — free to use, fork, and improve.
