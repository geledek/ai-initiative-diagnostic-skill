---
name: ai-initiative-diagnostic
description: Use whenever evaluating an AI initiative, AI investment thesis, AI pilot proposal, or proposed AI deployment. Diagnoses using a four-role framework — Investigator, Devil's Advocate, Long-term Strategist, Senior Advisor — built around three questions: Real Friction, Right Solution Mode, Value Accumulates. Trigger this skill any time someone is considering whether to build, buy, fund, or kill an AI initiative, even if they don't explicitly ask for a diagnostic.
---

# AI Initiative Diagnostic

Diagnose AI initiatives in four sequential roles. Maintain all prior reasoning as state — each role builds on the previous role's output.

After each role, output a clearly labeled section, then proceed to the next role. Do not stop until all four are complete.

## Role 1: Investigator (Q1 — Real Friction?)

NAME WHO FEELS THE PAIN. Who specifically experiences the problem? What does it cost them — in time, money, quality, or risk?

CLASSIFY THE STARTING POINT.
- Friction-first: "Our customers / teams struggle with [specific thing]"
- Tech-first: "We should use AI for [task]"

State which — and quote the language that signals it.

FRICTION STATEMENT. If friction-first: state the pain in one sentence. If tech-first: flag this as a warning sign and identify the real friction before proceeding.

Output:
WHO FEELS THE PAIN | WHAT IT COSTS | FRICTION-FIRST OR TECH-FIRST | PAIN STATEMENT

## Role 2: Devil's Advocate (Q2 — Right Solution Mode?)

Your job is to find where this breaks, not where it succeeds.

RELIABILITY TEST. "Would I be comfortable if this output reached the end consequence — the customer, the regulator, the judge — without human review?" Yes or no. Name the consequence of an error.

OPERATIONAL-MODE CHECK. Strip out the human-in-loop language from the pitch. In the moment the output reaches the end party, is a human actually between the AI and them? If no, the initiative is operationally Replace regardless of how it is described.

ERROR LOOP.
- No one catches errors → Replace mode. Name the risk.
- Human in loop by design → Augment mode. Name their role.
- AI enables what structurally couldn't exist before → Create mode.

MODE VERDICT. State: Replace / Augment / Create. State the single condition that must hold. Flag if it is not yet met.

Output:
RELIABILITY TEST | OPERATIONAL MODE | ERROR LOOP | MODE | CRITICAL CONDITION | FAILURE RISK

## Role 3: Long-term Strategist (Q3 — Value Accumulates?)

WHAT ACCUMULATES?
(a) Productivity tool — costs down, volume up. Real value, no compounding.
(b) Improving solution — model gets more accurate through operation.
(c) Moat — proprietary asset competitor cannot replicate on day one.

Name which. Specify what accumulates and why it is hard to reconstruct.

MEASUREMENT CHECK — THE KLARNA WARNING.
Name three metrics that prove this is working. Are these the metrics that would naturally get tracked? Flag any gap between what matters and what is easy to measure.

BLAST-RADIUS CHECK. If this fails on day one, who sees it — internal users, paying customers, regulators, or the public? Pick the worst plausible. Adjust the reliability bar accordingly.

Output:
WHAT ACCUMULATES | THREE METRICS | MEASUREMENT GAP | BLAST RADIUS

## Role 4: Senior Advisor (Synthesis)

Write for a board audience. Be direct.

VERDICT: [Fund / Fund-with-condition / Reframe / Kill]
MODE: [Replace / Augment / Create]

Q1 — REAL FRICTION? (2 sentences)
Q2 — RIGHT SOLUTION MODE? (2 sentences)
Q3 — VALUE ACCUMULATES? (2 sentences)

STRONGEST LINK: Where this idea is most solid.
WEAKEST LINK: Where this idea is most at risk of failing silently.
ONE CHANGE: Specific action — not a general recommendation.

CLOSEST REFERENCE CASE: Match against the cases in `cases/` and name the parallel explicitly.

## Reference Cases

See `cases/` for diagnosed examples. When diagnosing a new initiative, compare against the closest reference case and note the parallel explicitly.
