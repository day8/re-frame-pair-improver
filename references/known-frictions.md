# Known recurring frictions

Use this file as a pattern-check, not as a substitute for session evidence.

If the current session resembles one of these classes, mention that it may be part of a recurring product gap rather than a one-off.

## Common classes

### Runtime discovery and attachment brittleness

Signals:
- repeated attach attempts
- discovery works on one platform or shell but not another
- the user has to bypass the documented path and connect manually
- the tool can reach the runtime indirectly, but the documented helper fails

Typical improvements:
- platform-aware discovery logic
- explicit fallback behavior
- stronger structured errors naming the next best action
- regression coverage for platform-specific connection paths

### Docs and behavior drift

Signals:
- the documented command exists but behaves differently
- the recipe is conceptually right but the exact method, flag, or expectation is wrong
- the user follows docs and still gets misleading results

Typical improvements:
- tighten contracts between docs and code
- add smoke checks for documented commands and result shapes
- promote volatile facts into generated or verified references

### Weak trust signals

Signals:
- the user cannot tell whether the result is fresh, partial, stale, or inferred
- the tool succeeds structurally but returns too little information to trust
- the user has to manually verify whether the action really landed

Typical improvements:
- add explicit freshness, completeness, or warning fields
- distinguish "worked but partial" from "fully landed"
- add better default summaries around retries, misses, and fallback paths

### Hidden prerequisite burden

Signals:
- too much expert knowledge is needed before the happy path works
- the user has to know environment quirks, shell behavior, fixture setup, or instrumentation assumptions
- a missing prerequisite is only discovered late

Typical improvements:
- earlier prerequisite checks
- clearer discovery output
- safer defaults
- stronger recipes for environment setup and recovery

### Missing first-class workflows

Signals:
- the user repeatedly falls back to raw commands or ad hoc reasoning
- the same multi-step workaround appears in more than one session
- the tool has the necessary low-level primitives but not the right composed recipe

Typical improvements:
- add a new structured op
- add a higher-level recipe to the skill
- reshape result fields so downstream reasoning is less manual

### Validation and fixture gaps

Signals:
- a regression clearly could have been caught by a smoke test, fixture, or cross-platform check
- confidence in the tool depends on manual dogfooding
- behavior is documented as supported but not actually exercised in CI

Typical improvements:
- add fixture coverage
- add targeted regression tests
- narrow the documented contract until tests exist
