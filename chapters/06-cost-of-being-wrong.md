# 6. The Cost of Being Wrong

<p class="chapter-subtitle">Match evidence thresholds to asymmetric error costs and intervention severity.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part II</span><span>Decision: when confidence is enough</span></div>

A detector does not decide whether its score is sufficient. A decision policy does.

The same 0.70 risk estimate might justify recording additional telemetry, reducing a request rate, delaying a payout, or doing nothing. It should rarely justify every action on the intervention ladder.

## Confusion matrices hide the consequential choice

False positive and false negative are properties relative to a label and threshold. Platform decisions add an action:

```text
expected cost(action, threshold)
  = P(false positive) * cost(false positive, action)
  + P(false negative) * cost(false negative, delay)
  + cost of friction and investigation
  + cost of operating the control
```

The costs depend on context. Wrongly delaying a low-value post differs from freezing a seller's payroll. Missing one spam message differs from allowing an irreversible fraudulent withdrawal. The actors bearing each cost may also differ from the team selecting the threshold.

## Base rates defeat impressive accuracy

Suppose one in a thousand transactions is abusive. A detector catches 90% of abuse and incorrectly flags 1% of legitimate transactions. Among one million transactions:

```text
abusive:       1,000 -> 900 flagged
legitimate:  999,000 -> 9,990 flagged

precision = 900 / 10,890 ~= 8.3%
```

The detector can be more than 98% accurate overall while most flagged transactions are legitimate. This does not make it useless. It may be excellent for routing evidence collection and terrible for automatic permanent enforcement.

Report precision and recall at the operational base rate, calibration by population and time, and the action attached to each threshold. ROC curves alone hide the workload and harm created by false alerts in rare-event settings.

## Evidence standards should rise with consequence

Evaluate an intervention along at least five axes:

| Axis | Lower consequence | Higher consequence |
|---|---|---|
| Scope | One request | Linked accounts, household, organization |
| Severity | Observe or slow | Remove assets or access |
| Duration | Seconds | Permanent |
| Reversibility | Automatic expiry | Irrecoverable loss |
| Collateral effect | Actor only | Customers, teammates, employees, family |

As consequence rises, demand stronger and more independent evidence, better attribution, a clearer policy basis, more review, and more robust recourse.

This creates **action-specific thresholds**:

```text
low confidence     -> observe, sample, or request low-cost verification
moderate confidence -> rate limit, delay value exit, narrow capability
high confidence     -> temporary restriction or reward removal
very high confidence + severe harm + review -> durable identity-wide action
```

These are not universal numeric bands. They illustrate that the score-to-action mapping is the core governance decision.

## A useful signal can be unsafe for direct enforcement

The Abuse Sharing Economy study found that cross-service IP intelligence could identify some abusive traffic, while direct blacklisting produced untenable false positives. The lesson applies to device reputation, graph neighbors, payment reuse, and anomaly scores: predictive value is not enforcement sufficiency.

Combine evidence according to how it fails. Ten features derived from the same IP address are not ten independent observations. An account's graph neighbors may all inherit the same mistaken entity-resolution edge.

## Unknown is a valid decision state

Systems often force a binary because a database column expects `allow` or `ban`. Add explicit states:

```text
allow
allow_with_limits
pending_more_evidence
temporary_hold
reject_action
restrict_capability
escalate_review
```

Uncertainty can be managed through reversible controls and time. The value of waiting is the expected error reduction from additional evidence minus harm accumulated during the delay. Chapter 16 develops this latency budget.

## Appeals reveal mistakes imperfectly

Appeal overturns are important but selected. Users must notice the action, understand the route, retain access, have time and language capability, and believe review is worthwhile. Non-appeal is not proof of correctness.

Still, reversals must repair more than account state. They should update linked restrictions, funds, rewards, labels, reviewer guidance, policy interpretation, and—after careful validation—model evaluation. The DSA's requirement for reasons and complaint handling reinforces that decision provenance is part of the system.

## Evaluate the whole decision system

NIST's [AI Risk Management Framework](https://doi.org/10.6028/NIST.AI.100-1) treats trustworthiness as contextual and multidimensional. Validity, reliability, safety, transparency, privacy, explainability, and fairness involve tradeoffs; optimizing one characteristic does not make the whole system trustworthy.

For integrity systems, test:

- signal and label provenance;
- performance at actual base rates;
- calibration across time, surface, and population;
- policy-to-label consistency;
- action-specific user and ecosystem outcomes;
- reviewer workload and disagreement;
- appeal access and repair completeness;
- attacker adaptation and metric manipulation;
- shutdown, rollback, and expiry behavior.

## The decision procedure

1. Define the label and time horizon behind the risk estimate.
2. Measure base rate and calibration in the actual decision population.
3. Price false positives, false negatives, delay, friction, and operation by affected party.
4. Grade interventions by scope, severity, duration, reversibility, and collateral effect.
5. Set action-specific evidence standards; do not attach one threshold directly to `BAN`.
6. Preserve an uncertainty state and use time or narrow controls to gather information.
7. Measure errors beyond appeals and propagate corrections through the system.

## Research trail

- [Abuse-sharing economy note](../research/fraud/2016-thomas-abuse-sharing-economy.md)
- [NIST AI RMF note](../research/ml/2023-nist-ai-risk-management-framework.md)
- [Digital Services Act note](../research/legal/2022-eu-digital-services-act.md)
- [GDPR Article 22 note](../research/legal/2016-eu-gdpr-article-22.md)

## Review questions

1. Which action does your model threshold trigger, and why is that consequence justified?
2. What is precision at the actual operational base rate?
3. Which users cannot or will not appear in your appeal-overturn metric?
