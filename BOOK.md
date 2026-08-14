# Book synthesis

This file is the book's live argument map. Claims graduate here from reviewed research and concept notes before they become polished chapter prose.

## Governing claim

**Bot mitigation is a decision problem under uncertainty, not merely a detection problem.**

A platform governs behavior through a chain:

```text
ecosystem -> actors -> incentives -> harm -> policy -> observability
          -> inference -> confidence -> urgency -> intervention
          -> error handling -> recourse -> measurement -> adaptation
```

Each arrow is a possible failure point. A highly accurate detector can still produce harmful governance when the prohibited behavior is vague, attribution is weak, the intervention is disproportionate, or recourse is absent.

## The book's promised contribution

The book will teach an engineer, product leader, investigator, or policy partner how to decide:

1. what outcome actually threatens a platform ecosystem;
2. which automation should be permitted, limited, or prohibited;
3. what evidence the platform can responsibly collect;
4. how strongly that evidence supports identity, coordination, or harmful intent;
5. how quickly a decision is required;
6. which intervention is proportionate and reversible;
7. how to measure mistakes, support appeal, and learn from adaptation.

## The Adversarial Platform Canvas

Every chapter and case study should answer the same fourteen questions:

| Dimension | Governing question |
|---|---|
| Ecosystem | What system, exchange, or community are we protecting? |
| Actors | Who participates directly and indirectly? |
| Incentives | What does each actor gain, lose, or avoid? |
| Harm | Which observable outcomes damage the ecosystem, and for whom? |
| Policy | Which behavior is allowed, limited, restricted, or prohibited? |
| Observability | Which evidence can and should the platform collect? |
| Detection | How can harmful behavior be inferred from that evidence? |
| Confidence | How uncertain, manipulable, and context-dependent is the inference? |
| Urgency | What is the detection and decision latency budget? |
| Intervention | Which action is proportionate, targeted, and reversible? |
| Error costs | What happens after a false positive or false negative? |
| Recourse | Can an affected user understand, contest, and repair the decision? |
| Economics | Does defense reduce harm or merely move attacker cost? |
| Adaptation | What will attackers learn and change next? |

## Decision doctrine under development

These are hypotheses to research, challenge, and refine:

- Govern harmful behavior, not the metaphysical category “bot.”
- Separate evidence collection from inference and inference from enforcement authority.
- Treat attribution as probabilistic across request, session, device, account, person, and organization.
- Use the least severe intervention that controls expected harm within the latency budget.
- Require stronger evidence for interventions that are severe, broad, durable, or hard to reverse.
- Treat false positives and false negatives as asymmetric, ecosystem-specific costs.
- Design appeals, evidence packages, audit trails, and rollback into the enforcement system.
- Measure prevented harm and legitimate-user burden, not detector accuracy alone.
- Expect every observable defense to alter attacker incentives and behavior.

## Part map

### Part I — Define the problem before solving it

Challenge “bot” as a sufficient category, establish harm analysis, and model the economics of abuse and defense.

### Part II — Decide what the platform should permit

Build an automation policy, connect it to legal and contractual authority, and quantify the asymmetric cost of mistakes.

### Part III — Observe the platform

Inventory telemetry, attacker interaction surfaces, and the limits of identity and attribution.

### Part IV — Detect

Compare rules, behavioral signals, statistical learning, graph methods, and client integrity as evidence-producing mechanisms.

### Part V — Respond

Design a graduated intervention system, time-to-decision policy, appeals, review tooling, and bounded transparency.

### Part VI — Operate an adversarial system

Choose outcome metrics, run an adaptive defense program, and establish organizational decision rights.

### Part VII — Case studies

Apply one canvas to gaming, dating, commerce, and financial markets so the legitimacy of automation is seen as ecosystem-dependent.

## Open synthesis questions

- Can proportionality be formalized well enough to guide system design without pretending costs are objective?
- When should an intervention target behavior, capability, account, device, network, payment instrument, or organization?
- How should a platform measure displaced harm that moves to a new account or channel?
- Which transparency improves legitimacy without creating a cheap attacker feedback oracle?
- What evidence standard is appropriate at each rung of the intervention ladder?
- How should privacy and data minimization constrain graph detection and long-lived attribution?
- When does defensive friction become a product failure or discriminatory burden?

## Evidence ledger

No major claim should become chapter prose until it has at least one linked research note, known limitations, affected ecosystems, and a falsification question.

| Working claim | Evidence state | Manuscript location | Important limitation |
|---|---|---|---|
| “Bot” is a mechanism label, not a sufficient governance category | Supported by contrasting standards, contracts, and policies | Chapters 1 and 4 | Some ecosystems deliberately adopt broad mechanism bans |
| Harm should be measured separately from violations and enforcement volume | Supported by T&S practice and economic reasoning | Chapter 2 | Causal harm measurement remains ecosystem-specific |
| Abuse defense changes a production economy, not merely a success rate | Supported by security economics and measured account markets | Chapter 3 | Historical underground-market measurements are not current prices |
| Signals useful for risk can be unsafe for direct enforcement | Supported by cross-service abuse measurement | Chapters 3 and 6 | One Google study does not quantify every modern signal |
| Higher-impact actions require stronger evidence and recourse | Normative synthesis supported by NIST risk guidance and EU safeguards | Chapters 5 and 6 | Legal requirements vary by jurisdiction and workflow |
| Agent governance needs delegated authority plus behavioral controls | Plausible framework; practitioner support only so far | Chapters 1 and 4 | Requires stronger standards and deployment evidence |
| Observations, entity links, inferences, and decisions require separate provenance | Supported by NIST risk frameworks and identity models; engineering synthesis | Chapters 7 and 9 | Exact evidence architecture remains platform-specific |
| IP address, device estimate, account, person, and organization are not interchangeable | Supported by network standards, digital identity guidance, and abuse measurements | Chapter 9 | Combined signals can still support strong attribution in context |
| Automation mechanism does not determine legitimacy | Supported by standardized testing automation and contrasting platform policies | Chapters 4 and 8 | Some ecosystems intentionally prohibit mechanisms to protect fairness |
