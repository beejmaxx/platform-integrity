# 4. Acceptable Automation

<p class="chapter-subtitle">Design a policy spectrum that preserves beneficial automation while constraining harm.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part II</span><span>Decision: what to permit</span></div>

A platform that prohibits all automation will prohibit parts of itself. Monitoring, indexing, moderation, testing, accessibility, seller operations, and customer agents all depend on software acting at machine speed.

The policy question is not whether automation exists. It is which actors may exercise which capabilities, toward which outcomes, under what constraints.

## Separate capability from permission

Technical capability answers “can this client act?” Policy answers “may it act this way here?” Detection estimates what is happening. Authorization records a grant. These systems overlap, but none substitutes for the others.

```text
capability:     client can submit 1,000 requests per minute
authorization: partner token permits 600 catalog reads per minute
policy:         reads may support price comparison but not personal-data resale
behavior:       token requests 900 records and ignores retry guidance
decision:       throttle this capability and investigate the grant
```

Rate alone does not decide legitimacy. An authorized integration can exceed its grant; an unidentified client can make low-rate harmful requests.

## Use a policy spectrum

Classify a behavior rather than an entire tool:

| Level | Meaning | Typical control |
|---|---|---|
| Allowed | Fits normal product expectations | Ordinary authentication and capacity controls |
| Allowed with limits | Valuable but creates capacity, fairness, or privacy risk | Scoped API, quota, disclosure, audit |
| Discouraged | Not forbidden, but unsupported or likely to degrade experience | Warnings, reduced guarantees, migration path |
| Restricted | Permitted only to approved actors or contexts | Registration, attestation, contractual controls |
| Prohibited | Conflicts with a core ecosystem rule or causes unacceptable harm | Prevention, reward removal, suspension, investigation |

The same mechanism can occupy different rows. Automated gameplay may be prohibited in ranked competition, permitted in a private sandbox, and necessary for testing. Scraping may be authorized for an index, limited for research, and prohibited for unsolicited targeting.

## Write rules in layers

A workable automation policy has at least four layers:

1. **Purpose:** the protected ecosystem outcome—fair allocation, authentic judgment, capacity, privacy, or security.
2. **Conduct:** observable prohibited behavior—circumvention, fabricated engagement, exceeding grants, reward extraction, impersonation.
3. **Mechanism:** relevant implementations—scripts, agents, macros, modified clients—without pretending the list is exhaustive.
4. **Exceptions and paths:** accessibility, public-interest research, testing, APIs, partners, and user-delegated agents.

GitHub's policy illustrates conduct-oriented modifiers such as *excessive*, *inauthentic*, and *undue burden*. Steam's agreement uses a broader mechanism category and examples tied to rewards and authentic judgment. Neither is universally correct; each expresses a product choice and creates a different enforcement burden.

## Authorized automation should be observable

An authorized path can improve both product value and defense:

- scoped credentials identify the principal and delegate;
- grants name permitted actions, resources, rates, and expiry;
- stable identifiers enable accountability and incident response;
- predictable quotas protect capacity;
- documentation reduces accidental violation;
- revocation targets one capability without destroying an account.

But registration is not proof of good behavior. A partner can be compromised, a customer can delegate too broadly, and a legitimate agent can violate policy. Continue to evaluate action and context.

The Robots Exclusion Protocol provides a useful negative lesson: declared crawler identity and published preferences support cooperation, but the standard explicitly says they are not authorization. Stronger actions need authenticated grants.

## Accessibility is a design test

If policy equates unusual timing, non-pointer input, or assistive transformation with abuse, the policy is underspecified. Accessibility should not appear as a late exception to “real human behavior.” It should test whether the rule actually describes the protected outcome.

Ask:

- Does the rule require a particular human motor pattern, or genuine human judgment?
- Can the platform expose an accessible authorized method without weakening the invariant?
- Is a challenge completion rate measured across assistive technologies, languages, devices, and networks?
- Can a user disclose or appeal assistive automation without surrendering sensitive information unnecessarily?

## AI agents require bounded delegation

For agents, policy should express **who may delegate what**:

```text
principal        customer account A
delegate         shopping agent provider B
scope            search and reserve; no final purchase
budget           500 USD
inventory limit  one unit per product family
expiry           24 hours
disclosure       agent identifies provider and grant
revocation       principal or platform may revoke
```

The platform can then govern the action without guessing humanity. It still detects forged grants, compromised delegates, coordinated principals, and prohibited outcomes.

## The decision procedure

1. Define the ecosystem property the policy protects.
2. Describe prohibited conduct in technology-resistant terms.
3. Map legitimate uses and affected populations before choosing a mechanism ban.
4. Provide authorized paths where automation creates value.
5. Scope grants by action, resource, rate, value, and time.
6. Pair every policy level with proportionate enforcement and recourse.
7. Version the policy and test it against new mechanisms and old harms.

## Research trail

- [Robots Exclusion Protocol note](../research/bot-detection/2022-ietf-robots-exclusion-protocol.md)
- [GitHub policy note](../research/social-platforms/2026-github-acceptable-use.md)
- [Steam agreement note](../research/gaming/2026-valve-steam-subscriber-agreement.md)
- [After Bots source note](../research/bot-detection/2026-gosschalk-after-bots.md)

## Review questions

1. Which automation does your platform depend on but your public policy appears to prohibit?
2. Can one grant be revoked without disabling the principal's entire account?
3. Which policy rule incorrectly uses “human-like” as a synonym for legitimate?
