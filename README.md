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

Validated against 6 real enterprise deployments (2017–2025): Klarna, McDonald's, Air Canada, NYC MyCity, JPMorgan COIN, and Moderna — spanning Replace-mode failures, an Augment-mode success, and partial passes.

## Install

### Claude Code (user-level skill)

```bash
mkdir -p ~/.claude/skills
cp -r ai-initiative-diagnostic ~/.claude/skills/
```

The skill activates automatically on triggers like "evaluate this AI pilot," "should we build this AI feature," or "diagnose this initiative."

### Claude Code (project-level skill)

```bash
mkdir -p .claude/skills
cp -r ai-initiative-diagnostic .claude/skills/
```

### Verify

Paste a known case (e.g., the Klarna pitch language from `cases/klarna.md`). The output should land at Replace mode, fail the reliability test, and flag a measurement gap.

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
├── README.md           ← this file
├── SKILL.md            ← skill definition (frontmatter + four-role prompt)
└── cases/              ← reference diagnoses with sources
    ├── klarna.md
    ├── mcdonalds.md
    ├── air-canada.md
    ├── nyc-mycity.md
    ├── jpmorgan-coin.md
    └── moderna.md
```

## License

MIT.
