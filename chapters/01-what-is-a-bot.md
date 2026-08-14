# 1. What Is a Bot?

<p class="chapter-subtitle">Choose a governable category without confusing automation, intent, identity, and harm.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part I</span><span>Decision: what to classify</span></div>

Imagine four requests arriving at a ticketing platform in the same second:

1. a customer clicks “Buy” in a browser;
2. an accessibility tool invokes the same control;
3. a shopping agent acts under the customer's instruction and budget;
4. a reseller's program rotates through fabricated accounts to defeat a purchase limit.

All four requests can be emitted by software. Their HTTP syntax may be indistinguishable. Yet the platform has strong reasons to treat them differently.

That is the first problem with the word **bot**: it appears to describe an actor, but usually describes only a mechanism. It tells us that software participated. It does not tell us who authorized the action, what rule applies, which harm may result, or what intervention is justified.

## There is no useful binary

Automation is a continuum of delegated effort:

| Form | Human contribution | Example |
|---|---|---|
| Direct interaction | Chooses and performs each action | A person completes a purchase form |
| Assisted interaction | Chooses the goal; software transforms input | Screen reader, password manager, translation tool |
| Macro or script | Defines a repeatable procedure | Spreadsheet macro, game input macro, test script |
| Supervised agent | Delegates a goal and monitors execution | Travel or shopping assistant |
| Autonomous service | Defines policy; software continuously acts | Search crawler, monitoring agent, market-making system |
| Human-assisted operation | Software scales work; people solve exceptions | Fraud farm, moderation operation, CAPTCHA-solving service |

The boundary shifts with implementation. A reseller can employ people to click; a legitimate user can employ an agent to transact. “Human-like” behavior is not legitimacy, and machine-like behavior is not abuse.

Platforms themselves depend on benign automation. Search engines use crawlers to discover the web. The IETF's [Robots Exclusion Protocol](https://www.rfc-editor.org/rfc/rfc9309.html) standardizes how cooperative crawlers discover service-owner preferences. It calls crawlers automated clients and explicitly warns that `robots.txt` is not access authorization. This is an important separation: declared identity and cooperative policy are useful, but they are not security proof.

## Policy definitions reveal different real concerns

There is no universal platform definition because ecosystems protect different things.

GitHub's [Acceptable Use Policies](https://docs.github.com/en/site-policy/acceptable-use-policies/github-acceptable-use-policies) focus on excessive automated bulk activity, inauthentic interaction, rank abuse, deception, and undue server load. The modifiers do the work: *excessive*, *inauthentic*, *abusive*. GitHub also provides APIs and automation products because automation is part of the ecosystem's value.

Valve takes a broader contractual approach. Steam's [Subscriber Agreement](https://store.steampowered.com/subscriber_agreement/) defines scripts, bots, macros, and other non-human-controlled systems as “Automation” and prohibits specified interaction with Steam services. Its examples reveal underlying concerns: fabricated statistics, rewards without genuine input, automated account creation, and scripted participation in systems that require judgment.

U.S. ticket law is narrower still. In the FTC's first [BOTS Act enforcement cases](https://www.ftc.gov/news-events/news/press-releases/2021/01/ftc-brings-first-ever-cases-under-bots-act), the alleged conduct combined automated purchasing, circumvention of posted limits, fabricated accounts, IP concealment, and a resale business. The law is not a general prohibition on fast customers or purchasing software. It addresses circumvention in a defined market.

These are not inconsistent definitions waiting for a standards committee. They are different governance choices.

## Classify the claim, not the creature

“Bot detected” often hides several distinct claims:

```text
Mechanism claim:     software generated or assisted the action
Identity claim:      these requests belong to one actor or operation
Authority claim:     the actor was or was not authorized by the account holder
Behavior claim:      the action violated a rate, sequence, or interaction rule
Intent claim:        the actor sought a prohibited outcome
Harm claim:          the behavior caused or materially risked ecosystem damage
```

Evidence rarely supports all six at once. Regular timing may support a mechanism claim. Shared payment instruments may support an identity link. Neither alone proves harmful intent. A valid account credential proves access, not current delegated authority. A prohibited outcome can sometimes be governed without resolving whether a human or program produced it.

This yields a practical rule:

> Make the narrowest claim supported by the evidence, then choose only interventions justified by that claim.

A mechanism signal might justify lower request concurrency. A strong behavior claim might justify rejecting one transaction. A permanent removal of linked accounts needs much stronger attribution and policy evidence.

## A better actor model for agents

AI agents make the binary less useful, but do not make detection obsolete. The platform needs a richer authorization envelope:

```text
principal:       who receives the benefit and bears responsibility?
delegate:        which person, program, or provider is acting?
grant:           what authority was given, by whom, and when?
action:          what operation is requested?
constraints:     budget, rate, resource, audience, and expiry
evidence:        how are identity and grant authenticated?
context:         what risk, policy, and behavioral history applies now?
```

An agent may have a legitimate grant and still be compromised, exceed its limit, or participate in coordinated abuse. Authorization, authentication, behavior analysis, and harm prevention are complementary.

## The decision procedure

Before creating a “bot” rule, answer in order:

1. **Name the protected outcome.** Fair allocation, authentic judgment, system capacity, account security, or something else?
2. **State the policy in observable terms.** What action, scale, coordination, deception, or circumvention is prohibited?
3. **Identify authorized paths.** APIs, declared crawlers, accessibility tools, agents, testing, and commercial integrations.
4. **Separate evidence claims.** Mechanism, identity, authority, behavior, intent, and harm.
5. **Choose an intervention at the supported scope.** Request, capability, transaction, account, linked operation, or organization.
6. **Test counterexamples.** Could a legitimate user, shared network, expert player, or accessibility tool produce the same evidence?

If the team cannot complete steps one and two, it is not ready to build a classifier. It does not yet know what the classifier is for.

## Research trail

- [RFC 9309 note](../research/bot-detection/2022-ietf-robots-exclusion-protocol.md)
- [GitHub policy note](../research/social-platforms/2026-github-acceptable-use.md)
- [Steam agreement note](../research/gaming/2026-valve-steam-subscriber-agreement.md)
- [FTC BOTS Act note](../research/marketplaces/2021-ftc-bots-act-enforcement.md)

## Review questions

1. Which of your current “bot” signals support mechanism, identity, behavior, or harm claims?
2. What legitimate automation would your policy prohibit accidentally?
3. Could the harmful outcome be governed without determining whether the actor is human?
