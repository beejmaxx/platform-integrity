# Platform Integrity

*Engineering Detection, Decisions, and Enforcement Against Bots, Fraud, and Abuse*

This repository is a living research and writing system for a book about governing adversarial automation on digital platforms. Bot detection is one input to that system, not the organizing principle.

> Platforms should not ask “Is this a bot?” first. They should ask “What behavior threatens the ecosystem, what evidence do we have, and what intervention is justified?”

## Core thesis

Bot mitigation is not primarily a detection problem. It is a decision problem under uncertainty. The platform must connect ecosystem harm, policy, available evidence, decision confidence, urgency, proportional intervention, error cost, recourse, economics, and attacker adaptation.

## Repository workflow

```text
source -> research note -> concept note -> BOOK.md synthesis -> chapter
```

- `BOOK.md` is the continuously improving argument map. It is not polished prose yet.
- `chapters/` contains chapter briefs and eventually manuscript drafts.
- `research/` contains one structured note per source.
- `concepts/` develops reusable decision tools that affect several chapters.
- `case-studies/` applies the same framework to contrasting ecosystems.
- `sources/` contains source indexes, not duplicated research notes.
- `ideas/inbox.md` captures unsorted questions without polluting the synthesis.
- `templates/` defines the required structure for new material.

## Working rules

1. Begin with harm and policy, not a detector or vendor.
2. Distinguish observation, inference, decision, and intervention.
3. Put a scope, time horizon, and uncertainty statement around every claim.
4. Preserve disagreement and limitations in research notes.
5. Match intervention severity and reversibility to evidence and harm.
6. Treat legitimate automation, accessibility, privacy, and appeal as design constraints.
7. Prefer primary evidence; label practitioner judgment and inference.
8. Do not publish operational detail that would materially enable abuse without a clear defensive benefit.

## Preview

```sh
mdbook serve --open
```

The mdBook navigation exposes the synthesis, framework, chapter briefs, concepts, and case-study briefs. Research notes remain in the repository until they are ready to cite.

## Current phase

The repository is intentionally at **architecture and research-design** stage. Chapter files are decision briefs, not generated textbook prose. The next milestone is a sourced research corpus for Parts I and II, followed by a reviewed synthesis in `BOOK.md`.
