# Analysis lenses

Use this file when the session has enough detail that a loose summary is not enough.

## Friction signals

Look for:

- repeated retries or "try again" loops
- repeated explanation of the same context
- fallback from a high-level workflow to low-level commands
- missing or empty outputs where the user expected an answer
- stale outputs that required manual verification
- unclear contracts between docs and actual behavior
- hidden prerequisites or environment assumptions
- long waits with weak progress signals
- workarounds that the tool should have encoded
- user uncertainty about whether to trust the result

Also notice:

- hidden capabilities that should have been discoverable
- expert-only knowledge that should have been embodied in the tool
- places where the workflow nearly worked but failed late
- places where the user had to choose between speed and safety

## Root-cause categories

Map each finding to one primary cause:

- `docs/discoverability` — the feature or prerequisite existed, but the user could not find or trust it
- `workflow-gap` — the instructions or recipes did not guide the user through a common task
- `missing-op` — the workflow needed a first-class operation that does not exist
- `unreliable-op` — an existing operation was too brittle or ambiguous
- `default/fallback` — the default behavior was wrong, silent, or unsafe
- `platform-bug` — the workflow behaved differently on a specific OS, shell, or browser setup
- `validation-gap` — the bug shipped because the repo lacks the right smoke test, fixture, or warning
- `upstream-gap` — the best fix belongs in `re-frame`, `re-frame-10x`, `re-com`, or `shadow-cljs`
- `out-of-scope` — the user wanted something `re-frame-pair` should probably not own

## Improvement patterns

Prefer proposals that remove repeated effort:

- tighten `SKILL.md` wording or add a recipe
- add a stronger warning or a more explicit failure mode
- add a structured result field instead of forcing manual interpretation
- add a runtime/script op for a repeated manual step
- make a platform-specific fallback automatic
- add a fixture or regression test for the observed failure mode
- add an upstream issue when the repo is working around the wrong abstraction boundary

## Prioritization

Prioritize improvements that score well on most of these:

- common: likely to help many sessions
- leverage: removes a whole class of manual effort
- specific: easy to describe and implement
- trustworthy: improves confidence in results
- local-first: can be fixed in `re-frame-pair` without waiting on upstream

If many ideas surface, return the top 2-5 and demote the rest to "other possibilities".
