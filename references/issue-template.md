# Issue template

Use this structure when drafting or filing an issue. Keep it evidence-based and concise.

## Title patterns

- `Improve <workflow> when <condition>`
- `Add <op/result/warning> for <workflow>`
- `Fix <platform> behavior in <script/op>`
- `Make <workflow> self-validating instead of manual`

## Body

```md
## Problem

Describe the workflow the user was trying to complete and the friction they hit.

## Evidence from a real session

- What happened
- What had to be retried, worked around, or manually verified
- Why the current workflow was slower or less trustworthy than it should have been

## Why re-frame-pair was not enough

Explain the missing behavior, missing data, brittle assumption, or misleading contract.

## Proposed improvement

Describe the change concretely. Name the likely layer:
- `SKILL.md`
- script/runtime op
- result/warning shape
- tests/fixture
- upstream issue

## Expected impact

Explain what effort, confusion, or risk this would remove in future sessions.

## Open questions

List any remaining uncertainty, especially if the best fix might belong upstream.
```

## Filing rules

- File only after explicit user approval.
- Redact secrets, tokens, and internal-only details.
- Prefer one issue per distinct improvement.
- Search for an existing issue first when tooling allows it.
