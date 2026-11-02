# Compliance & Security Pass

Runs alongside the Phase 5 adversarial checks whenever the product collects user data — which is almost always. In CONCEPT mode, limit it to Parts A and B against the spec/policy text. This pass is a **flag-raiser, not legal advice**: it tells the builder which regulations plausibly apply and where the product visibly diverges from its own promises or from baseline security practice, with enough evidence that a lawyer or security engineer can act. Say that framing in the report.

Personas tell you whether users *would* trust the product. This pass tells you whether they *should*.

## Part A — Data-regulation applicability scan

First build the **data inventory** from code, policies, and onboarding flows — never from the marketing copy alone:

- What is collected: identifiers (name/email/phone), government IDs, precise location/home address, financial/payment data, documents and photos, health data, biometrics, children's data, behavioral/analytics data
- Where it flows: first-party servers, cloud storage (S3 etc.), analytics SDKs, ad networks, AI vendors (chat features almost always ship user content to a third-party model API — check the SDKs), payment processors, email providers
- Who the users are and where: consumer vs. business, jurisdictions served, any possibility of minors

Then map inventory → plausibly applicable regimes. Flag, don't adjudicate:

| Trigger in the inventory | Regimes to flag |
|---|---|
| Any EU/UK users possible | GDPR / UK GDPR: lawful basis, DSR rights (access, deletion, **portability — an export feature, not an email address**), breach notification, DPAs with processors |
| California / US-state users | CCPA/CPRA and the growing state-law patchwork (VA, CO, CT, TX…): notice at collection, opt-outs, "do not sell/share" |
| Canadian users | PIPEDA consent and access rights |
| Any realistic use by under-13s (family/household products: check!) | COPPA — parental consent, or an enforced age gate |
| Health-adjacent data | HIPAA (if covered entities touch it) or state consumer-health laws (e.g. Washington MHMDA) |
| Payments | PCI DSS scope (usually delegated to Stripe/RevenueCat etc. — verify card data never touches first-party code) |
| Marketing email (waitlists count) | CAN-SPAM / CASL: functioning unsubscribe, identified sender, "no spam ever" claims are enforceable promises |
| Mobile distribution | Apple privacy nutrition labels & App Tracking Transparency; Google Play Data Safety — these must match the actual SDK behavior, and mismatches are a rejection/removal risk |
| Consumer-facing UI | ADA/WCAG exposure (US), European Accessibility Act (in force June 2025) — connect to the accessibility-overlay persona findings |
| AI chat/advice features | EU AI Act transparency (users must know they're talking to AI), FTC Section 5 on AI claims, and disclosure of which vendors receive user content |

## Part B — Policy-vs-product diff (the compliance Refuter)

Diff every promise in the privacy policy, ToS, and in-app microcopy against what the code actually does. This is the same discipline as the message–market audit, applied to legal surface — and it routinely finds the worst findings in the whole run:

1. **Rights claimed vs. implemented.** Policy says users can delete/export their data → find the endpoint and the UI. "Email us to exercise rights" where GDPR/CPRA applies is a flag; a deletion flow that leaves orphaned data in S3 or analytics is a bigger one.
2. **Absolute promises vs. actual flows.** "Never shared," "no spam ever," "only you have access" — grep for them, then list every third party the data actually reaches (processors, analytics, AI vendors). Absolutes contradicted anywhere = FALSE claim, severity high: these are FTC-actionable and they're also the exact lines users remember.
3. **Collection vs. minimization.** What does onboarding demand versus what the core feature needs? Required fields that serve no shipped feature are both a conversion cost (personas will have found this) and a regulatory smell.
4. **Consent timing.** Is data collected before the user saw any notice? Are analytics/tracking SDKs firing before consent where consent is required?
5. **Retention & breach.** Does the policy state retention periods? Is there any evidence of a breach-response plan? Absence is a flag at severity-info, not a verdict-driver.
6. **AI disclosure.** If user content reaches LLM APIs, is that stated? Is chat clearly labeled as AI?

## Part C — Security baseline

**Delegate first.** Check whether a dedicated security skill or tool is available in the environment, and if so run it and fold its confirmed findings into this pass rather than duplicating it:

- **Cloudflare's `security-audit` skill** (github.com/cloudflare/security-audit-skill) — preferred when installed: its finder/verifier separation matches this skill's Refuter philosophy, and its confirmed findings can be ingested directly. Install: `npx skills add https://github.com/cloudflare/security-audit-skill --skill security-audit`.
- Claude Code's built-in **`/security-review`** — good for branch-scoped review of pending changes.
- Security MCP tools (Semgrep, Snyk, etc.) if connected.

**Fallback checklist** (one agent, evidence-cited, when no dedicated tool is available — breadth over depth, flag-and-cite rather than exploit):

- Secrets committed to the repo (API keys, service-account JSON, `.env` files — check the tree, not just `.gitignore`)
- AuthN/AuthZ: every user-data endpoint verifies identity; queries scoped server-side (user ID from the token, never from the request body); IDOR smell on `/:id` routes
- Transport & storage: HTTPS everywhere, tokens stored appropriately on mobile (Keychain/Keystore vs. plain shared preferences), sensitive data in logs
- Input handling: upload endpoints (type/size validation, where files land), injection surface (raw SQL vs. ORM), SSRF on URL-fetching features
- Third-party exposure: dependency red flags, debug endpoints left on, verbose error responses, admin surfaces unauthenticated
- Mobile-specific: certificate pinning claims vs. reality, WebView settings, deep-link validation

## Severity & verdict wiring

Each finding: **regime or vulnerability class · evidence citation (file/line/policy clause) · severity · who is exposed (user, company, both) · remediation sketch.**

- **CRITICAL** — active legal exposure or plausibly exploitable vulnerability (secrets in repo, unauthenticated user data, false absolute privacy claims under GDPR/FTC scope, COPPA gap with real child users). A CRITICAL finding **blocks a VALIDATED verdict** regardless of scores and **caps Trust & Net Benefit at 40**.
- **HIGH** — divergence between promise and behavior, missing DSR implementation in covered markets, store-label mismatch. Feeds Trust & Net Benefit scoring directly.
- **MEDIUM/INFO** — missing statements, hygiene gaps, things a diligence process will ask about. Listed in the report, no gate effect.

The report gets a dedicated **Compliance & Security** section: the data inventory in one paragraph, the flagged regimes table, findings by severity, what was delegated to which tool, and the standing caveat — *this is an engineering-grade flag pass, not counsel; treat CRITICAL/HIGH items as "ask a professional now" markers.*
