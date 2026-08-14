# 7. What Can We Actually Know?

<p class="chapter-subtitle">Build an evidence system before building a detection system.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part III</span><span>Decision: what to observe</span></div>

A risk system reports that an account is using a “high-risk device.” What, precisely, does the platform know?

Perhaps the server received several requests with a cookie it had seen before. Perhaps client software submitted a hardware attribute. Perhaps a vendor combined an IP address, browser properties, and historical fraud labels into a device identifier. “High-risk device” compresses all of that lineage into three words. If an investigator, model, or policy engine treats those words as a fact, uncertainty disappears exactly where it matters most.

The first job of an integrity system is therefore epistemic: preserve the distance between what the platform observed and what it concluded.

## The evidence ladder

Platform evidence usually passes through six stages:

```text
event -> representation -> feature -> linkage -> inference -> decision
```

An **event** is something the platform directly received or produced: a request arrived, a transaction settled, or a server rejected an action. A **representation** is the structured record of that event. A **feature** is a transformation such as requests per minute, time since account creation, or the number of payment instruments shared with other accounts. A **linkage** asserts that records concern the same entity. An **inference** estimates a condition such as automation, compromise, coordination, or fraud. A **decision** applies policy and selects an intervention.

Each stage can introduce error. A request timestamp may be trustworthy while a client-reported interaction timestamp is fabricated. The event may be logged correctly but joined to the wrong account. A feature may use a stale window. A device link may merge a household. A calibrated risk estimate may still be insufficient for the proposed action.

This yields a practical writing and engineering rule:

> State the strongest claim the evidence supports, not the most convenient label downstream systems expect.

“Five accounts used the same public IP during one hour” is an observation. “Five accounts are controlled by one person” is an attribution claim. “They form a bot farm” adds mechanism and organization. “Ban all five” is a decision. None follows automatically from the previous statement.

## Build a signal register

Before adding a signal to production, document it as if it may someday appear in an appeal or incident review.

| Field | Question |
|---|---|
| Purpose | Which harm or decision is this signal intended to inform? |
| Source | Which system, client, vendor, or person produced it? |
| Subject | Does it concern a request, session, device, account, payment, or person? |
| Lineage | What transformations and joins produced the value? |
| Reliability | Under which ordinary conditions is it wrong or missing? |
| Manipulability | Can a user, attacker, intermediary, or vendor influence it? |
| Population | For whom was the signal evaluated, and who may be underrepresented? |
| Half-life | How quickly does its meaning decay? |
| Sensitivity | What privacy, security, or discrimination risk does it create? |
| Retention | How long is the raw event and each derivative needed? |
| Action ceiling | What is the most severe action this signal can support by itself? |
| Owner | Who detects breakage, drift, and unauthorized reuse? |

The **action ceiling** is especially useful. A shared IP address may justify a rate limit or a graph-expansion query. It should rarely justify permanent punishment on its own. A confirmed payment reversal may support a narrow transaction hold, but it may not establish who controlled the account.

## Server facts and client claims

The server has the strongest knowledge about state it controls. It can know that it issued an item, accepted an order, matched two players, or received a particular sequence of protocol messages. Even these records can be incomplete, duplicated, delayed, or corrupted, but their provenance is under the platform's control.

Client telemetry is different. A client can report window focus, input events, software state, device properties, or an attestation result. These reports may be valuable, but they are claims crossing a trust boundary. Legitimate clients also lose events because of crashes, old versions, privacy controls, connectivity, accessibility software, and instrumentation defects.

Consequently:

- client absence is not proof of evasion;
- client presence is not proof that the claimed event happened as represented;
- a cryptographically protected report may establish its origin and integrity without establishing that the surrounding device was benign;
- server-side invariants should protect the outcomes the platform cannot afford to trust to the client.

Chapter 14 will examine attestation. The immediate lesson is simpler: classify every field by who controls the claim.

## Missingness is evidence about the pipeline

Integrity teams are tempted to interpret missing telemetry as suspicious. Sometimes it is. Attackers do suppress or distort observations. But the same symptom can be produced by deployment gaps, regional outages, consent choices, old devices, unsupported browsers, or customers with unusual access needs.

Treat missingness as its own feature with competing hypotheses:

```text
missing = evasion | product variance | collection failure | lawful choice | unknown
```

A sudden change across an entire client version suggests instrumentation failure. Missingness concentrated in accounts already connected to confirmed abuse may raise risk. The raw fact is the same; its evidentiary weight depends on context.

## More data can make the system worse

Collection creates capability, but also liability. Persistent identifiers and cross-context linkages can make unrelated activity correlatable. [RFC 8981](https://www.rfc-editor.org/rfc/rfc8981.html), which standardizes temporary IPv6 addresses, is a useful reminder that stable identifiers themselves create tracking risk. NIST's [Privacy Framework](https://www.nist.gov/privacy-framework) treats privacy as an organizational risk-management problem, not merely a disclosure checkbox.

For each proposed signal, ask two separate questions:

1. **Can we collect it?** Is it technically available and legally authorized?
2. **Should we collect it?** Is its marginal decision value worth its privacy, security, operational, and customer costs?

These questions should be answered for raw events, derived features, and linkages independently. A platform may need a precise event briefly to investigate fraud while retaining only an aggregate for longer-term measurement. It may need to prohibit reuse of an integrity identifier for advertising or employee analytics. Retention should follow a named decision need, not the convenience of cheap storage.

Data minimization also improves defense. Unbounded telemetry expands access paths, incident impact, deletion obligations, feature ambiguity, and the number of spurious correlations an investigator can mistake for meaning.

## Evidence quality is a production concern

A model can be healthy while its evidence pipeline is broken. Integrity observability needs monitors for:

- event volume, delay, duplication, and schema changes;
- feature distributions by client version, geography, and relevant user group;
- join rates and identity-link stability;
- label age, provenance, and leakage;
- access to sensitive fields and unexpected downstream consumers;
- the rate at which reviewers find that evidence packages cannot reproduce decisions.

Preserve the version of the feature logic, policy, model, thresholds, and relevant evidence used at decision time. Recomputing a score months later with current data is not the same as explaining the original decision.

## A decision procedure for new telemetry

When a team proposes a new signal:

1. Name the harmful outcome and the decision the signal will improve.
2. Write the direct observation separately from every inferred claim.
3. Identify who controls the source and how ordinary users produce false or missing values.
4. Test incremental value against existing evidence, not merely correlation with old labels.
5. Segment error analysis across relevant populations and client conditions.
6. Assign an action ceiling and require corroboration above it.
7. Minimize collection, access, reuse, and retention.
8. Instrument pipeline health and decision reproduction.
9. Define the signal's retirement condition before it becomes permanent infrastructure.

The output is not a warehouse full of facts. It is a governed evidence supply chain.

## Research trail

- [NIST Privacy Framework note](../research/privacy/2020-nist-privacy-framework.md)
- [NIST AI Risk Management Framework note](../research/ml/2023-nist-ai-risk-management-framework.md)
- [The Abuse Sharing Economy note](../research/fraud/2016-thomas-abuse-sharing-economy.md)
- [Temporary IPv6 addresses note](../research/identity/2021-ietf-ipv6-temporary-addresses.md)

## Review questions

1. Can every enforcement feature be traced back to a direct observation and transformation version?
2. Which signal is currently being used above the action ceiling its reliability warrants?
3. What missing telemetry would reveal a collection failure rather than an attacker?
4. Which retained identifier creates more future risk than present decision value?
