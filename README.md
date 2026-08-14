<div class="book-hero">

<p class="book-kicker">A FIELD GUIDE FOR ADVERSARIAL SYSTEMS</p>

# Platform Integrity

<p class="book-deck">Engineering Detection, Decisions, and Enforcement Against Bots, Fraud, and Abuse</p>

<p class="book-thesis">Bot mitigation is not primarily a detection problem. It is a decision problem under uncertainty.</p>

<p class="book-byline">A living book by <a href="https://github.com/beejmaxx">Bijan</a></p>

</div>

Digital platforms are not simply attacked by “bots.” They are contested ecosystems in which people, scripts, account farms, compromised devices, commercial automation, and AI agents pursue conflicting goals.

The consequential question is rarely *Is this a bot?* It is:

> **What behavior threatens the ecosystem, what evidence do we have, and what intervention is justified?**

*Platform Integrity* is a practical decision framework for answering that question. It connects security engineering, trust and safety, fraud and risk, data systems, product policy, economics, privacy, legal authority, and operational response—because production integrity failures cross all of those boundaries.

<div class="front-matter-grid">

<div>

### The problem

Detection teams can produce excellent scores and still damage the platform. Policy may be ambiguous. Identity links may be weak. A correct signal may trigger a disproportionate action. Appeals may be unable to repair a false attribution. Attackers may adapt faster than the organization learns.

</div>

<div>

### The promise

Readers learn how to define harm, set automation policy, design evidence pipelines, reason about uncertain attribution, select detection methods, match confidence to intervention, build recourse, and operate an adaptive integrity program.

</div>

</div>

## The operating model

The book treats platform defense as a governed chain of decisions:

```text
ecosystem -> actors -> incentives -> harm -> policy -> observability
          -> inference -> confidence -> urgency -> intervention
          -> error handling -> recourse -> measurement -> adaptation
```

Every arrow is a possible failure point. A detector is only one evidence-producing component inside this system.

The recurring tool is the **[Adversarial Platform Canvas](concepts/adversarial-platform-canvas.md)**—fourteen questions that force a team to connect what it protects, who benefits, what it can know, how quickly it must act, what mistakes cost, and how the attacker will respond.

## What is inside

| Part | The decision it helps you make | Topics |
|---|---|---|
| **I. Define** | What exactly are we protecting against? | Automation taxonomy, ecosystem harm, attacker and defender economics |
| **II. Permit** | What should the platform allow? | Acceptable automation, contracts, law, proportionality, asymmetric error cost |
| **III. Observe** | What can the platform responsibly know? | Telemetry, evidence lineage, client trust boundaries, identity and attribution |
| **IV. Detect** | Which methods fit this harm and evidence? | Rules, behavior, statistics, machine learning, graphs, client integrity |
| **V. Respond** | What action is justified, and when? | Friction, challenges, restrictions, suspensions, latency, human review, appeals |
| **VI. Operate** | How does the defense survive contact with reality? | Outcome metrics, feedback loops, attacker adaptation, organizational ownership |
| **VII. Apply** | How does the framework change by ecosystem? | Gaming, dating, marketplaces, and financial markets |

## The core decisions

By the end, a reader should be able to answer:

1. Which measurable outcome—not merely which rule violation—is harming the ecosystem?
2. Is automation the problem, or is it only the mechanism producing the behavior?
3. Which events are direct observations, and which claims are features, links, or inferences?
4. Does the evidence identify a request, session, device, account, person, or organization?
5. What evidence standard is proportionate to the severity, breadth, duration, and reversibility of the action?
6. Does the platform need a millisecond decision, a delayed campaign analysis, or both?
7. How will an innocent or compromised user understand, contest, and recover from the decision?
8. Did the intervention prevent harm, displace it, or merely teach the attacker?

## What makes the approach different

Most treatments begin with classifiers, CAPTCHAs, fingerprints, or anti-cheat technology. This book begins one level earlier—with institutional authority and engineering judgment.

Its working doctrine is:

- Govern harmful behavior rather than the metaphysical category “bot.”
- Separate collection from inference, and inference from authority to act.
- Treat attribution as probabilistic, temporal, and purpose-specific.
- Use the least severe intervention that controls expected harm within the latency budget.
- Require stronger evidence for actions that are severe, broad, durable, or difficult to reverse.
- Treat privacy, accessibility, legitimate automation, and recourse as system requirements.
- Measure prevented harm and legitimate-user burden, not detector accuracy alone.
- Assume every visible defense changes attacker incentives.

## Built to withstand scrutiny

This is a living research book, not a bundle of unsupported prescriptions. Claims move through a visible pipeline:

```text
primary source -> structured research note -> concept -> synthesis -> chapter
```

The public [research library](research/README.md) preserves what each source says, its evidence, assumptions, weaknesses, disagreements, and implications. The [living synthesis](BOOK.md) keeps an evidence ledger for the book's major claims. Sources currently include NIST risk and identity frameworks, IETF and W3C standards, peer-reviewed abuse-market measurements, legislation and enforcement actions, platform contracts, and trust-and-safety scholarship.

That discipline is part of the product: readers can inspect not only the conclusion, but why it should be believed and where it might fail.

## Who this is for

*Platform Integrity* is written for staff and principal engineers, engineering managers, security and fraud leaders, trust-and-safety practitioners, data scientists, investigators, product and policy leaders, and founders building systems in which abuse can distort access, money, attention, safety, or trust.

It is also a working framework for teams that need to:

- design or review an abuse-prevention architecture;
- turn an ambiguous “bot problem” into a defensible program;
- connect policy, telemetry, models, investigations, and enforcement;
- reduce false positives without surrendering to fraud;
- prepare evidence and decision systems for new forms of delegated AI automation;
- establish ownership, metrics, and review mechanisms across functions.

## Read next

Begin with **[What Is a Bot?](chapters/01-what-is-a-bot.md)** for the category problem, or jump to the **[Adversarial Platform Canvas](concepts/adversarial-platform-canvas.md)** to apply the framework to a live system.

Parts I–III are in first-draft review. Parts IV–VI are structured briefs being expanded in public. The manuscript will continue to evolve as research, cases, and practitioner review challenge its claims.

<div class="front-cta">

### Building or reviewing an integrity system?

Use this book as a common decision language for engineering, product, policy, operations, and executive review. Follow the project—or contact [Bijan on GitHub](https://github.com/beejmaxx)—to discuss the manuscript, advisory work, architecture reviews, or platform-integrity engagements.

</div>
