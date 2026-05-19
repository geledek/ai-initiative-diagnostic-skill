# AI Initiative Diagnostic

A Claude Code skill for evaluating AI initiatives, pilot proposals, and investment theses using a structured four-role diagnostic framework.

## What it does

Runs any AI initiative through four sequential perspectives:

1. **Investigator** — Is there real friction, or is this tech-first?
2. **Devil's Advocate** — Is the solution mode (Replace / Augment / Create) honest and safe?
3. **Long-term Strategist** — Does value accumulate, or is it a productivity tool dressed as a moat?
4. **Senior Advisor** — Synthesis with a fund / reframe / kill verdict.

The output is a board-ready diagnosis with strongest link, weakest link, and one specific change.

## Why it exists

Most AI pitches fail in predictable ways: tech-first framing, Replace-mode deployments without reliability headroom, and measurement gaps that hide failure until it's public. This skill catches those patterns at the proposal stage.

## Validation

Run against 6 real enterprise deployments (2017–2025), as if diagnosing each at launch:

| Case | Year | Mode pitched | Skill verdict | Actual outcome | Match? |
|---|---|---|---|---|---|
| Klarna AI CSR | 2024 | Replace | Fail | Reversed 2025, rehiring | ✅ |
| McDonald's + IBM drive-thru | 2021–24 | Replace | Fail | Canceled June 2024 | ✅ |
| Air Canada chatbot | pre-2022 | Augment (de facto Replace) | Partial Pass | Lost tribunal Feb 2024 | ⚠️ Risk flagged, materialized |
| NYC MyCity chatbot | 2023 | Augment (de facto Replace) | Fail | Illegal advice exposed Mar 2024 | ✅ |
| JPMorgan COIN | 2017+ | Augment | Pass | Sustained success | ✅ |
| Moderna ChatGPT Enterprise | 2024 | Augment | Partial Pass | Reported success, vendor-amplified | ⚠️ Measurement gap flagged |

See `skills/ai-initiative-diagnostic/cases/` for full diagnoses with sources.

## Install

### Option 1 — Ask Claude (fastest)

Open Claude Code and say:

> *Install the skill from https://github.com/geledek/ai-initiative-diagnostic-skill into ~/.claude/skills/*

Claude will clone and install it.

### Option 2 — Manual install (user-level)

```bash
git clone https://github.com/geledek/ai-initiative-diagnostic-skill.git
mkdir -p ~/.claude/skills
cp -r ai-initiative-diagnostic-skill/skills/ai-initiative-diagnostic ~/.claude/skills/
```

### Option 3 — Manual install (project-level)

```bash
git clone https://github.com/geledek/ai-initiative-diagnostic-skill.git
mkdir -p .claude/skills
cp -r ai-initiative-diagnostic-skill/skills/ai-initiative-diagnostic .claude/skills/
```

### Option 4 — As a Claude Code plugin

This repo is structured as a Claude Code plugin. Once added to a marketplace, it can be installed with `/plugin install ai-initiative-diagnostic@<marketplace>`.

### Verify

Paste a known case (e.g., the Klarna pitch language from `skills/ai-initiative-diagnostic/cases/klarna.md`). The output should land at Replace mode, fail the reliability test, and flag a measurement gap.

## Example prompts

**Pitch deck evaluation**

> Diagnose this AI pilot proposal: "We're deploying an AI agent to handle Tier-1 IT support tickets. It will resolve 60% of tickets without human involvement and save us $1.2M/year in support costs."

**Vendor proposal review**

> A vendor pitched us an AI underwriting tool that auto-approves loan applications under $50K. They claim 30% faster decisioning and want a 3-year contract. Run the diagnostic.

**Internal request triage**

> Our marketing team wants to use AI to write all customer emails. Run the four-role diagnostic on this idea before I respond.

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
- Push back on the diagnostic if the operational-mode check feels wrong. The Replace/Augment call is where the framework's value concentrates — get it right.
- After a verdict, ask Claude to compare against the closest case in `cases/`. Precedent makes the verdict harder to argue with.
- Treat "Fund-with-condition" verdicts as kill verdicts unless someone owns the condition and a deadline.

**Calibration notes**
- The framework is biased toward catching Replace-mode failures and measurement gaps. It is forgiving of Augment-mode initiatives.
- Verdicts depend on the diagnostician's honesty in Role 2's reliability test. A pitch written *for* the framework can game it.
- Use cases as anchors. If a new pitch matches a documented failure pattern, name the parallel explicitly.

## Repo structure

```
ai-initiative-diagnostic/
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
            └── moderna.md
```

Each case follows the same skeleton: story, four-role diagnostic, why-it-matters, sources.

## License

MIT — see `LICENSE`.
