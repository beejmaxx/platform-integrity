# 5. Policy, Contracts, and Law

<p class="chapter-subtitle">Align technical enforcement with actual authority, disclosure, privacy, and user rights.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part II</span><span>Decision: what may be enforced</span></div>

An engineer can build a system that links accounts, retains device history, automatically freezes funds, and permanently removes users. Whether the company should or may operate that system cannot be answered in code.

This chapter is not legal advice. It is a guide to recognizing when architecture contains legal and policy decisions that require qualified, jurisdiction-specific review.

## Four different sources of authority

Platform action may rest on:

1. **Product rules:** community standards, marketplace rules, competitive formats, API conditions.
2. **Contract:** terms accepted by a user or partner and the remedies those terms reserve.
3. **Law:** obligations, prohibitions, consumer rights, privacy constraints, sector rules, and regulator authority.
4. **Technical control:** the practical ability to reject a request, withhold a reward, or disable an account.

Technical control is not legal authority. Contract wording is not automatically enforceable everywhere. Legal permission is not proof that an intervention is proportionate or good product policy.

## Policy must precede scalable enforcement

A defensible rule should identify:

- the behavior and relevant context;
- the protected interest;
- authorized exceptions;
- possible interventions and their scope;
- evidence and review standards;
- notice, appeal, reinstatement, and asset treatment;
- effective date, version, and governing jurisdiction.

Vague rules push policy-making into models and reviewer folklore. A classifier trained on previously banned accounts may reproduce an unstated historical policy even after the written rule changes.

## Data collection is an intervention

Before collecting device, network, behavioral, payment, identity, or relationship signals, document:

```text
purpose and necessity
data subjects and affected non-users
source and expected reliability
derived inferences
access and sharing
retention and deletion
security and misuse risk
jurisdiction and disclosure
user rights and contestability
```

“Fraud prevention” is a goal, not an unlimited retention schedule. More data can create false linkage as well as insight. Shared IP addresses, recycled devices, family payment instruments, and compromised accounts can turn a confident graph into collateral enforcement.

## Automated decisions create architectural obligations

The EU GDPR's [Article 22](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32016R0679) addresses solely automated individual decisions that produce legal or similarly significant effects and provides exceptions and safeguards. It is not a universal prohibition on models, nor a universal explanation right. Its scope is fact-specific. Still, it forces useful engineering questions:

- Did automation recommend the action or make it?
- What information did the human reviewer receive?
- Could the reviewer actually change the result?
- Was the effect significant for this user?
- Can the person express a view and contest the decision?

Do not implement “human in the loop” as a ceremonial click that ratifies a score under impossible queue pressure.

## Explanation and complaints need data models

The EU Digital Services Act requires covered services to provide reasons for specified restrictions and establishes complaint-handling duties for covered online platforms. It also makes reversal counts and other moderation information operational reporting concerns. The European Commission reported in 2026 that platforms reversed about 30% of 165 million internally appealed decisions during the first two years of DSA application. That number is not a platform-wide false-positive rate: appeal selection, service scope, decision categories, and reversal reasons matter. It is evidence that reversals occur at material scale.

Build decisions with structured provenance:

```text
decision_id
affected object and account
policy and version
facts and evidence references
automated systems used and their role
decision-maker and review path
action, scope, duration, and effective time
reason code and user-facing explanation
appeal deadline, state, outcome, and repair actions
```

Without this, explanations are reconstructed from logs, appeals cannot be consistent, and policy changes cannot be audited.

## Purchased assets and livelihoods change severity

An account may contain purchased licenses, virtual currency, seller funds, creative work, business reputation, or access to a professional audience. Steam and PlayStation terms show how platform enforcement can affect account access, subscriptions, devices, and virtual assets. The technical action “disable account” may therefore contain several remedies with different justification.

Prefer separable controls where feasible:

- stop one transaction;
- remove an improperly obtained reward;
- restrict a competitive mode;
- pause payout pending review;
- revoke an integration token;
- preserve access to purchased offline content;
- permanently remove an identity only under the corresponding standard.

## The decision procedure

For every enforcement mechanism:

1. Identify policy, contract, and legal authority separately.
2. Choose relevant jurisdictions and versions; reject timeless generic legal claims.
3. Map collected data to necessity, retention, access, and user rights.
4. Record automation's exact role in the decision.
5. Decompose the action by asset, capability, scope, duration, and reversibility.
6. Design reason, review, appeal, correction, and audit data before launch.
7. Obtain specialist review for material legal conclusions and high-impact workflows.

## Research trail

- [Digital Services Act note](../research/legal/2022-eu-digital-services-act.md)
- [GDPR Article 22 note](../research/legal/2016-eu-gdpr-article-22.md)
- [Steam contract note](../research/gaming/2026-valve-steam-subscriber-agreement.md)
- [FTC BOTS Act note](../research/marketplaces/2021-ftc-bots-act-enforcement.md)

## Review questions

1. Which of your enforcement actions combines several remedies behind one account-status field?
2. Can you reconstruct the policy version and evidence for a six-month-old decision?
3. Does human review have authority, time, and information sufficient to be meaningful?
