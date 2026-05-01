# re-frame-pair-improver

`re-frame-pair-improver` is a Claude skill that reviews a user's work with `re-frame-pair` and turns that session into concrete product-improvement proposals.

It is designed for retrospectives like:

- "What was frustrating about this re-frame-pair session?"
- "What took longer than it should have?"
- "Which parts of this workflow should re-frame-pair absorb?"
- "Can you draft or file an issue for the best improvement idea?"

The skill focuses on evidence from the session itself: retries, confusion, workarounds, stale or empty results, missing observability, brittle platform behavior, hidden prerequisites, and trust gaps. It then proposes improvements at the right layer: `SKILL.md`, scripts/runtime ops, warnings/results, tests/fixtures, or upstream library issues.

It never files an issue without explicit user approval.

It is intentionally diagnosis-first: the default outcome is a better understanding of what went wrong and which improvements would matter most, not pressure to contribute code or file issues.

## Repo contents

- `SKILL.md` — the skill itself
- `references/analysis-lenses.md` — friction taxonomy and prioritization prompts
- `references/known-frictions.md` — recurring classes of product friction to pattern-match against
- `references/issue-template.md` — issue drafting structure
- `.claude-plugin/plugin.json` — plugin packaging metadata
- `agents/openai.yaml` — UI metadata for skill lists and invocation

## Typical output

A good run of the skill produces:

1. the user's actual goal
2. the main friction points observed in the session
3. likely root causes
4. 2-5 high-leverage improvement ideas
5. optional issue candidates, with draft text or direct filing only after approval

## Status

Pre-alpha. The repo contains the packaged skill and minimal validation wiring.
