# AI Initiative Diagnostic

A Claude skill for evaluating AI initiatives, pilot proposals, and investment theses using a structured five-role diagnostic framework.

## What it does

Runs any AI initiative through five sequential perspectives:

1. **Investigator** — Is there real friction, or is this tech-first?
2. **Devil's Advocate** — Is the solution mode (Replace / Augment / Create) honest and safe?
3. **Long-term Strategist** — Does value accumulate across all three dimensions, or is this a productivity tool dressed as a moat?
4. **Realist** — Does the organisation have the data and integration in place to actually execute this?
5. **Senior Advisor** — Synthesis with a Fund / Fund-with-condition / Reframe / Kill verdict.

The output is a board-ready diagnosis with strongest link, weakest link, and one specific action.

## Why it exists

Most AI initiatives fail in predictable ways: tech-first framing, Replace-mode deployments without reliability headroom, measurement gaps that hide failure until it's public, and data or integration gaps that kill execution before value is created. This skill catches those patterns at the proposal stage.

## What changed in v2

Three targeted additions to the original three-question framework:

**Q2 — Consequence Level Check.** If a single application handles queries at different levels of consequence, the most consequential type sets the mode for the whole application. Air Canada's chatbot answered both "what are your opening hours?" and "can I get a refund?" — the refund query sets the mode. Replace. The original skill could not cleanly classify this.

**Q3 — Three dimensions instead of one category.** The original framework asked you to pick one category (productivity tool / improving solution / moat). The updated framework assesses three dimensions independently: does it get better, are switching costs high, do users actively prefer it over alternatives? A gap on any one dimension produces Fund-with-condition, not Fund. Jasper and Microsoft Copilot both looked like improving solutions. Both failed on switching costs and competitive preference. Both correctly land at Fund-with-condition.

**Q4 — The Realist.** A new role sitting between Long-term Strategist and Senior Advisor. Q1–Q3 assess whether the idea is worth pursuing. Q4 asks whether the organisation can actually execute it. Two checks: is the data AI-ready and legally usable, and is there a plan to connect the AI output to real workflows? DeepMind passed Q1–Q3 cleanly. Q4 caught it — no confirmed legal right to use 1.6M patient records.

## Validation

Run against 20 real cases (2013–2025), diagnosed as if at the time of launch:

| Case | Year | Mode | Verdict | Actual outcome | Verdict accuracy |
|------|------|------|---------|----------------|-----------------|
| Jasper AI | 2022 | Augment | Fund-with-condition | Forced to pivot when ChatGPT launched within 12 months | ✅ |
| Forethought | 2022 | Augment + Replace | Fund-with-condition + Reframe | Market compressed by CRM incumbents within 18 months | ✅ |
| Artisan | 2024 | Replace | Reframe | Enterprise buyers questioned full-replacement framing | ✅ |
| Charta | 2024 | Augment | Fund | Expanding commercial traction | ✅ |
| Stability AI | 2022 | Augment | Fund-with-condition | CEO resigned; community never converted to revenue | ✅ |
| IBM Watson Oncology | 2013 | Replace | Kill | $4B+ invested; zero patients treated | ✅ |
| DeepMind / NHS Streams | 2015 | Augment | Fund-with-condition | ICO ruled data transfer unlawful | ✅ |
| Salesforce Einstein / Agentforce | 2023 | Augment + Replace | Fund + Fund-with-condition | Standard features succeeded; agents stalled at 85% of orgs | ✅ |
| Pieces Technologies | 2024 | Replace | Kill | FTC enforcement; required to disclose error rates | ✅ |
| Microsoft Copilot | 2023 | Augment | Fund-with-condition | 85%+ of orgs slowed rollouts; value delivery inconsistent | ✅ |
| Amazon AI Recruiting | 2014 | Replace | Kill | Scrapped 2018; systematic gender bias confirmed | ✅ |
| Goldman Sachs AI Coding | 2024 | Augment | Fund | 20–55% productivity gains documented | ✅ |
| Klarna Customer Service | 2022 | Replace | Reframe | Reversed 2025; CEO admitted "we went too far" | ✅ |
| Air Canada Chatbot | 2022 | Replace | Reframe | Lost tribunal; first legal precedent for chatbot liability | ✅ |
| Hospital Ambient AI Notes | 2023 | Augment | Fund | 100% health system adoption; 53% reporting high success | ✅ |
| McDonald's + IBM Drive-Thru | 2021 | Replace | Reframe | Cancelled June 2024 after persistent accuracy failures | ✅ |
| NYC MyCity Chatbot | 2023 | Replace | Reframe | Illegal advice exposed March 2024; chatbot pulled | ✅ |
| JPMorgan COIN | 2017 | Augment | Fund | Sustained success since 2017; expanded across legal ops | ✅ |
| Moderna ChatGPT Enterprise | 2024 | Augment | Fund-with-condition | Reported success; metrics vendor-amplified without baseline | ✅ |
| Singapore Egg Trader | 2022 | Create | Fund | Sustained success; 2,000 restaurant clients; data is the moat | ✅ |

**20 of 20 correct verdicts.** Fund-with-condition cases where the risk materialised did so because the condition was not enforced — a governance failure, not a framework failure.

See `skills/ai-initiative-diagnostic/cases/` for full diagnoses with sources.

## Install

### Option 1 — Ask Claude (fastest)

Open Claude Code and say:
> *Install the skill from https://github.com/geledek/ai-initiative-diagnostic-skill into ~/.claude/skills/*

Claude will clone and install it.

### Option 2 — Manual install (user-level)

```
git clone https://github.com/geledek/ai-initiative-diagnostic-skill.git
mkdir -p ~/.claude/skills
cp -r ai-initiative-diagnostic-skill/skills/ai-initiative-diagnostic ~/.claude/skills/
```

### Option 3 — Manual install (project-level)

```
git clone https://github.com/geledek/ai-initiative-diagnostic-skill.git
mkdir -p .claude/skills
cp -r ai-initiative-diagnostic-skill/skills/ai-initiative-diagnostic .claude/skills/
```

### Verify

Paste a known case (e.g., the Klarna pitch language from `skills/ai-initiative-diagnostic/cases/klarna.md`). The output should land at Replace mode, fail the reliability test, flag a measurement gap, and produce a Reframe verdict.

## Example prompts

**Pitch deck evaluation**
> Diagnose this AI pilot proposal: "We're deploying an AI agent to handle Tier-1 IT support tickets. It will resolve 60% of tickets without human involvement and save us $1.2M/year in support costs."

**Vendor proposal review**
> A vendor pitched us an AI underwriting tool that auto-approves loan applications under $50K. They claim 30% faster decisioning and want a 3-year contract. Run the diagnostic.

**Internal request triage**
> Our marketing team wants to use AI to write all customer emails. Run the five-role diagnostic on this idea before I respond.

**Post-mortem**
> Our AI chatbot went live 6 months ago and customer complaints have risen 15%. Diagnose what went wrong using the framework.

## Best practices

**When to invoke**
- Pitch decks for AI pilots before funding decisions
- Vendor proposals from AI platform companies
- Internal "we should use AI for X" requests
- Post-mortems on AI initiatives that underperformed

**When not to invoke**
- Pure technical questions (model selection, prompt engineering)
- Existing successful deployments with no proposed change
- Non-AI initiatives — the framework is specific to AI failure modes

**Getting the most out of it**
- Paste the *original* pitch language verbatim. Paraphrasing strips the tech-first signals the Investigator role looks for.
- Push back on the Q2 mode call if it feels wrong. Replace vs Augment vs Create is where the framework's value concentrates — get it right.
- For applications that handle queries at different consequence levels, identify the most consequential query type first. That sets the mode for the whole application.
- After a verdict, ask Claude to compare against the closest case in `cases/`. Precedent makes the verdict harder to argue with.
- Treat Fund-with-condition verdicts as Kill verdicts unless someone owns the condition with a named deadline.

**Calibration notes**
- The framework is biased toward catching Replace-mode failures and measurement gaps. It is forgiving of Augment-mode initiatives with existing governance.
- The Q2 reliability test depends on the diagnostician's honesty. A pitch written *for* the framework can game it.
- Create mode is rare. Most initiatives pitched as Create are improving solutions at best. The test is strict: could this business exist at any cost without AI?

## Repo structure

```
ai-initiative-diagnostic-skill/
├── README.md
├── LICENSE
├── .claude-plugin/
│   └── plugin.json
└── skills/
    └── ai-initiative-diagnostic/
        ├── SKILL.md
        └── cases/
            ├── klarna.md
            ├── mcdonalds.md
            ├── air-canada.md
            ├── nyc-mycity.md
            ├── jpmorgan-coin.md
            ├── moderna.md
            └── egg-trader.md
```

Each case follows the same structure: initiative description, five-role diagnostic, why it matters, sources.

## License

MIT — see `LICENSE`.
