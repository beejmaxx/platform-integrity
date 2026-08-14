# 10. Rules and Heuristics

<p class="chapter-subtitle">Use simple evidence where it is sufficient, observable, and maintainable.</p>

<div class="chapter-meta"><span>Status: brief</span><span>Part IV</span><span>Decision: when a rule is enough</span></div>

## Reader outcome

Design, validate, version, and retire rules without confusing explainability with correctness.

## Scope

Velocity, timing constraints, repetition, navigation, session properties, impossible states, and economic activity.

## Decision questions

- Is the rule a hard invariant, risk indicator, or temporary patch?
- What legitimate populations violate it?
- How quickly will it decay or invite evasion?
- Can its trigger and downstream action be audited separately?

## Evidence needed

- Rule lifecycle and shadow-evaluation examples
- Base rates and conditional precision
- Operational costs of overlapping rules
- Attacker adaptation after observable thresholds
