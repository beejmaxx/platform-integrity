# 2. Why Does the Platform Care?

<p class="chapter-subtitle">Translate “abuse” into observable ecosystem harm before choosing enforcement.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part I</span><span>Decision: what to protect</span></div>

Suppose an automated buyer acquires every available unit of a scarce product. What exactly went wrong?

- The seller may have earned the intended revenue.
- The transactions may be valid and paid.
- The service may have remained available.
- No account may have been compromised.

Yet ordinary buyers may conclude the allocation was unfair, resellers may extract the scarcity premium, support volume may rise, and trust in future launches may fall. “We detected automation” is not the explanation. The platform is responding to an allocation and ecosystem-design failure.

## Harm is an outcome, not a synonym for violation

Three ideas need to remain separate:

```text
Policy violation: behavior contradicts a rule the platform adopted
Harm:             an actor or ecosystem is made materially worse off
Risk:             uncertainty about future harm, including magnitude and likelihood
```

A rule can be violated without measurable harm. Harm can occur before a rule exists. A platform can also adopt a rule for operational simplicity even when individual violations are harmless. Enforcement systems become brittle when these categories are treated as interchangeable.

The Stanford Trust and Safety manuscript recommends prioritizing by the severity of harm, its prevalence, and the product's responsibility for enabling it. It also warns that user reports are incomplete and selected. [The manuscript](https://tsbook.org/ch1-introduction/) is centered on online safety, but the reasoning generalizes: count neither reports nor removed accounts as the harm itself.

## Build a causal harm chain

A useful harm statement connects conduct to affected parties through a mechanism:

```text
actor and conduct
    -> platform mechanism or market response
    -> exposure or changed allocation
    -> immediate effect
    -> downstream ecosystem effect
```

For scarce-inventory capture:

```text
coordinated buyers defeat per-customer limits
    -> inventory concentrates before ordinary customers can transact
    -> access shifts toward a resale market
    -> buyers pay more or abandon the purchase
    -> perceived fairness and future participation decline
```

Each arrow is a research question. Perhaps concentration was caused by ordinary demand rather than circumvention. Perhaps resale improves allocation to those who value the product most while violating the seller's fairness objective. Perhaps a queue would fail differently. The chain prevents moral vocabulary from substituting for evidence.

## A platform harm register

Record harms by affected party and system property:

| Harm family | Direct effect | Possible ecosystem effect |
|---|---|---|
| Security | Account or asset compromise | Users reduce participation or increase defensive burden |
| Economic | Theft, fraud, distorted price, reward extraction | Adverse selection; legitimate supply exits |
| Allocation | Scarce resource captured unfairly | Secondary markets and loss of procedural trust |
| Authenticity | Fake engagement, reviews, identity, or judgment | Signals stop informing decisions |
| Experience | Spam, harassment, ruined matches, unwanted contact | Retention and community composition change |
| Infrastructure | Resource exhaustion and support load | Higher prices, degraded service, constrained product design |
| Institutional | Legal exposure or unenforceable promises | Restrictions, litigation, regulator intervention |
| Defensive | Surveillance, friction, or erroneous enforcement | Accessibility loss, exclusion, distrust, chilling effects |

The last row matters. A defense is part of the ecosystem and can itself cause harm.

## Measure prevalence, exposure, severity, and responsibility

Raw event count favors easy-to-count activity. Instead describe at least four dimensions:

```text
prevalence:      how much violating or risky activity exists?
exposure:        how many affected parties encounter it, and how often?
severity:        what is the distribution of consequences, including the tail?
responsibility:  how much does this product create, amplify, monetize, or control the pathway?
```

Add **recoverability** and **velocity**. A fraudulent transfer that can be reversed tomorrow differs from a competitive match ruined now; an account network that grows slowly permits a different evidence strategy than real-time payment theft.

Avoid collapsing the dimensions into one impressive number too early. Ten million blocked attempts may reflect ten million independent threats, one looping script, or an instrumentation change. A decline in detected abuse may mean improvement, displacement, or detector blindness.

## The distribution matters more than the average

Harm and defensive burden are rarely uniform. A global false-positive rate can conceal concentrated exclusion of users behind shared networks. Median financial loss can conceal a destructive upper tail. Report rate can underrepresent people who do not know a violation occurred or cannot navigate the reporting flow.

For every harm measure, ask:

- What is the unit: request, account, person, victim, incident, campaign, or dollar?
- Who is absent from the data?
- Is the measurement before or after current defenses?
- Can attackers manipulate the metric?
- Which population bears the worst outcome?
- What counterfactual supports the claim that the platform caused or prevented it?

## Product success can create integrity failure

Ross Anderson's economic analysis observes that security problems arise when the party able to prevent harm does not bear its cost. The same pattern appears in platforms. Growth metrics can reward engagement generated by fake accounts. A marketplace can earn fees on transactions whose externalities fall on buyers or sellers. A support organization can optimize ticket closure while leaving recurring campaigns intact.

This is not necessarily bad intent. It is organizational optimization. If integrity outcomes are absent from planning and review, teams rationally optimize what is visible and rewarded.

## The decision procedure

Before funding an abuse control:

1. **Name affected parties**, including legitimate actors burdened by the defense.
2. **Write the causal chain** from conduct to harm and label uncertain links.
3. **Choose outcome measures**, not only detection or enforcement counts.
4. **Describe the distribution** by severity, population, time, and ecosystem surface.
5. **Estimate platform responsibility and control.** Could product design remove the pathway?
6. **Define the counterfactual.** What would likely happen without this intervention or with an alternative?
7. **Set guardrails.** Which defensive harms make the intervention unacceptable?

The output is not “bots are bad.” It is a prioritized, falsifiable claim about what the platform is protecting.

## Research trail

- [Stanford Trust and Safety manuscript note](../research/social-platforms/2025-stamos-grossman-pfefferkorn-forever-war.md)
- [Security economics note](../research/fraud/2001-anderson-information-security-economics.md)
- [FTC ticket-market case note](../research/marketplaces/2021-ftc-bots-act-enforcement.md)

## Review questions

1. Which integrity metric in your system is merely a detector-output count?
2. What harm does your current enforcement impose, and on whom?
3. Which link in your most important harm chain has the weakest evidence?
