# re-frame-pair-improver

`re-frame-pair-improver` is a Claude skill that reviews a user's session with [`re-frame-pair`](https://github.com/day8/re-frame-pair) and turns their experience into concrete improvement proposals.

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

Beta. The repo contains the packaged skill and minimal validation wiring.

## Install

> Not yet published to npm. There is no package install path for this skill yet.

To use it now, install it straight from a clone of this repo.

### Install the skill in Claude Code

Both distributions (Agent Skill and Claude Code Plugin) ship from the same repo. Until there is a published package, the Agent Skill path is the simplest option.

#### Global — for you, across any repo

Clone the repo somewhere stable, then symlink it into your user Claude config:

```bash
git clone https://github.com/day8/re-frame-pair-improver.git ~/src/re-frame-pair-improver
mkdir -p ~/.claude/skills
ln -s ~/src/re-frame-pair-improver ~/.claude/skills/re-frame-pair-improver
```

Best when you want the skill available everywhere and are happy to `git pull` updates in one place.

#### Project-local — for your whole team via the repo

Install into the project's own `.claude/skills/re-frame-pair-improver/` directory and commit it. Teammates who clone the repo and open Claude Code there get the same pinned version.

Because there is no npm package yet, do this by vendoring the repo contents or adding it as a submodule under `.claude/skills/re-frame-pair-improver/`.

For the plugin variant, check in the packaged files from this repo and reference the local plugin from the project's Claude configuration rather than a published package name.

#### Which to choose

- **Global** if you're the only person using Claude Code here, or you want one install shared across repos.
- **Project-local** if your team wants one pinned, shared version.
- **Both** is fine — the project-local install takes precedence when both are present.
