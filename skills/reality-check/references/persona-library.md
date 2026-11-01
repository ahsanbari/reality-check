# Persona Library

Personas are instruments, not characters. Each one exists to answer a specific validation question. Instantiate them *for this product* — the templates below are scaffolding, and every field must be filled with product-specific detail before an agent is launched.

## The five categories and what each one measures

### 1. Target — "Does it serve the people it's for?"

The intended user from the product thesis, taken literally. If the thesis says "freelance designers who lose track of invoices," the target persona is a freelance designer with specific unpaid invoices, not "a creative professional."

- Give them the **real job-to-be-done**, not a demo task: "get your March invoice paid," not "explore the invoicing feature."
- Vary within the category: one early-adopter-ish target (forgiving, curious) and one mainstream target (busy, zero patience for setup). Products often validate with the first and die with the second.

### 2. Adjacent — "How far does fit extend past the bullseye?"

One attribute deliberately off from the target: a decade older, less technical, on a different device, in a different country, doing the job for someone else (the assistant, the spouse, the employee told to use it).

- Measures whether the product's assumptions are load-bearing. If moving one attribute breaks the experience, the addressable market is the bullseye only.
- Good defaults: the **delegated user** (didn't choose the tool, must use it) and the **older/less-technical neighbor** of the target.

### 3. Anti-persona — "Does it waste or harm the people it's NOT for?"

Someone the product is explicitly not for, who will still encounter it — through an app store search, a shared link, a team rollout.

- The question is **net benefit**: does the app cost them more than it gives? Did it add notifications, accounts, steps, or anxiety it then charged them attention to manage?
- Also catches **mis-marketing**: if anti-personas keep thinking the product IS for them, the messaging is recruiting users who will churn and leave one-star reviews.

### 4. Skeptic — "Is it better *enough* to beat the current workaround?"

Has the problem, badly — and already solves it with something: a competitor, a spreadsheet, a group chat, a notebook, a habit. The most valuable and hardest persona.

- Their test is never "is this good?" It's "is this so much better that I'll pay the switching cost — re-entering my data, breaking my habit, trusting a new thing?"
- Make the incumbent concrete and give it credit: the spreadsheet is free, already set up, and has never surprised them. "Do nothing" is the market leader in almost every category.
- A skeptic who says "neat, but my spreadsheet is fine" is not a failed test. It is the single most common true answer in product validation, and the report must be able to say it.

### 5. Unaware — "Would someone with the problem even recognize this as the solution?"

Has the problem but has never named it, never searched for a tool, and doesn't know this category exists.

- Tests **discoverability and comprehension**, not usability: shown the landing screen cold, can they say what this is and that it's for *them*? Would any channel ever have put this in front of them?
- A product can be perfectly usable and still invisible to its market. This persona is how you find that out before the launch does.

## Overlays (apply ≥2 per run, stacked onto any persona)

Overlays are contexts and capabilities, not separate people. They routinely expose structural problems every user hits in milder form.

| Overlay | What it changes | What it catches |
|---|---|---|
| **Screen reader / keyboard-only** | No mouse, linear navigation, relies on labels & landmarks | Unlabeled buttons, focus traps, div-soup UIs |
| **Color-blind (deuteranopia)** | Red/green indistinguishable | Status conveyed by color alone |
| **Mobile on a commute** | One thumb, small screen, interruptions every 30s, flaky signal | Dense layouts, long forms, lost state |
| **Low bandwidth / old device** | Slow loads, no autoplaying anything | Heavy bundles, spinner-driven despair |
| **Non-native English speaker** | Reads slowly, idioms and cleverness don't land | Cute copy that obscures function |
| **Low tech literacy** | No mental model of accounts, OAuth, tabs | Unexplained jargon, silent failure states |
| **Privacy-defensive** | Assumes data will be misused until shown otherwise | Greedy signup forms, vague permissions |
| **Time-starved parent / caregiver** | 90-second sessions, constant interruption | Anything that can't be finished in one minute or resumed later |

## Persona brief template (fill every field)

```
PERSONA: [name], [age], [occupation], [location]
CATEGORY: target | adjacent | anti-persona | skeptic | unaware
OVERLAYS: [0–2 from the table]
TECH COMFORT: [1–5, with one concrete anchor, e.g. "3 — uses Excel daily, has never installed a browser extension"]
DEVICE & CONTEXT: [e.g. "iPhone 12, standing on a train, 15 minutes"]
THE PROBLEM, FOR THEM: [their specific version, or "does not have it" / "has it but has never named it"]
WHAT THEY DO TODAY: [the concrete incumbent: named competitor, spreadsheet, group chat, nothing]
LAST TIME IT HAPPENED: [a specific recent incident — feeds the Mom Test interview]
PATIENCE BUDGET: [e.g. "90 seconds to see the point, 5 minutes total, then gone"]
TASK: [the real job-to-be-done, phrased as an outcome they want, never as a feature tour]
WHAT WOULD DELIGHT THEM: [one sentence — so delight is recognizable, not just friction]
```

## Rules for persona agents

1. **Stay in character the whole run.** You are not an AI evaluating an app; you are this person trying to get something done on a train.
2. **Spend your patience budget honestly.** When it runs out, abandon and say exactly where. Completing the task anyway is the single most common way simulated testing lies.
3. **You don't know what the builder intended.** If the UI doesn't explain it, you don't know it.
4. **Compliments are not findings.** Report what you *did* and where you *stalled*, with the screen/element/copy cited.
5. **Delight counts too.** If something genuinely lands — say so, with the same evidence standard. This is a truth instrument, not a demolition derby.
