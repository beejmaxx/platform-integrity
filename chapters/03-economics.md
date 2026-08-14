# 3. The Economics of Abuse

<p class="chapter-subtitle">Model defense as a contest over expected value, capacity, and replacement cost.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part I</span><span>Decision: where to change incentives</span></div>

An attack can be technically possible and economically irrelevant. Another can survive a 99% account-removal rate because accounts are cheap and the remaining 1% pays for the entire operation.

Platform defense therefore needs two models: how the attack works and how the operation stays viable.

## Start with the production function

An abuse operation converts inputs into monetizable outcomes:

```text
infrastructure + identities + accounts + software + human labor
    -> attempts
    -> successful actions
    -> monetizable assets or influence
    -> realized revenue
```

Every arrow has yield, delay, variance, and capacity. Revenue may require resale, money mules, affiliate conversion, reward withdrawal, or an audience. The apparent technical step—creating an account or defeating a challenge—may not be the bottleneck.

Research on phishing and fraudulent accounts repeatedly illustrates this. Thomas and colleagues observed an underground market selling accounts in bulk, making accounts a priced production input rather than durable identities. Other work on phishing found that converting compromised credentials into irreversible value can depend on scarce intermediaries. Defense should target the limiting production step, not automatically the most visible one.

## Model expected profit, not attacker inconvenience

A starting model is:

```text
expected profit per cycle
  = P(success) * revenue_if_success
  - account and identity cost
  - infrastructure and tooling
  - human labor
  - inventory or capital at risk
  - expected enforcement loss
  - monetization and laundering cost
```

Then add time and scale:

```text
return on constrained resource
  = expected profit / scarce attacker input over time
```

An intervention can reduce success probability, raise marginal cost, cap throughput, increase variance, delay payout, seize accumulated value, or make targeting less efficient. These are different effects.

A challenge that costs an attacker one cent but a legitimate user thirty seconds may be economically backwards. A delayed reward can be powerful when it gives the platform time to detect a network before value exits. A ban can be negligible if replacement is instant, yet meaningful when reputation, inventory, or payout history is costly to rebuild.

## Count operations, not just accounts

In the 2013 study [*Trafficking Fraudulent Accounts*](https://research.google/pubs/trafficking-fraudulent-accounts-the-role-of-the-underground-market-in-twitter-spam-and-abuse/), researchers observed 27 merchants over ten months and collaborated with Twitter to identify millions of fraudulent accounts. The historical prices are not current benchmarks. The enduring lesson is structural: account creation, maturation, sale, campaign use, and replacement form a supply chain.

Account-removal metrics can reward the defender for repeatedly cutting disposable leaves while the operation persists. Better measures include:

- time and cost to replace an enforced asset;
- campaign throughput and survival;
- fraction of value removed before monetization;
- attacker labor per successful outcome;
- migration to other surfaces, accounts, or victims;
- time required to regain reputation or payout eligibility.

## Economics also explains false positives

Defenses impose costs on legitimate users:

```text
legitimate burden
  = added time + failed completion + privacy cost + exclusion
  + support effort + delayed funds + trust loss
```

Attackers may specialize, automate around friction, or pay low-cost labor; legitimate users face the control infrequently and cannot amortize the learning. A mechanism that “raises attacker cost” can raise defender and customer cost faster.

The relevant objective is not maximum attacker pain. It is favorable **cost asymmetry**:

```text
attacker cost or harm reduction gained
---------------------------------------
legitimate-user and platform cost added
```

Even this ratio is incomplete when burdens fall on different populations. Accessibility, geography, device quality, language, banking access, and shared networks change who pays.

## The defender has an economic system too

Ross Anderson's [economic account of security](https://www.cl.cam.ac.uk/archive/rja14/Papers/econ.pdf) emphasizes misaligned incentives and externalities. On a platform:

- a growth team may receive credit for accounts that integrity later removes;
- a marketplace may collect fees while sellers absorb fraud;
- an anti-abuse team may optimize blocks while support absorbs appeals;
- a model vendor may sell detection volume rather than prevented harm;
- one service may reject risky traffic that migrates to another service.

Allocate costs to make the whole outcome visible. Otherwise each team can improve its dashboard while the ecosystem worsens.

## Shared infrastructure creates both leverage and error

The Google study [*The Abuse Sharing Economy*](https://research.google/pubs/the-abuse-sharing-economy-understanding-the-limits-of-threat-exchanges/) measured IP reuse across six services. Cross-service intelligence identified some abusive traffic, but direct IP blacklisting created an unacceptable false-positive volume.

This illustrates a general economic temptation: a cheap, broad control can appear attractive because it moves investigative cost onto legitimate users. Signal sharing may improve risk estimates. It does not make the signal sufficient for punishment.

## Displacement is not victory

An intervention can:

1. **suppress** the harmful outcome;
2. **substitute** one attacker input for another;
3. **displace** activity to another surface, victim group, or platform;
4. **concentrate** the market among more capable attackers;
5. **transform** the business model.

Short evaluation windows confuse these. After a new control, observed attacks often drop immediately because attackers are testing alternatives. Measure long enough to see the new equilibrium.

## The decision procedure

For one abuse operation:

1. **Draw the value chain** from inputs to realized value.
2. **Estimate ranges**, not fictional point precision, for yield, cost, capacity, and delay.
3. **Find constrained inputs** such as trusted accounts, payout channels, human judgment, inventory, or victim attention.
4. **Map each intervention** to success probability, throughput, delay, variance, seizure, or replacement cost.
5. **Calculate legitimate and defender burden** using the same seriousness.
6. **Measure operation-level outcomes** and displacement over an appropriate horizon.
7. **Revisit after adaptation.** The model describes a temporary equilibrium, not a permanent attacker.

The economic goal is not necessarily to make all abuse impossible. It is to prevent expected harm efficiently, make large-scale abuse unattractive or capacity-constrained, and preserve a platform worth using.

## Research trail

- [Security economics note](../research/fraud/2001-anderson-information-security-economics.md)
- [Fraudulent-account market note](../research/fraud/2013-thomas-fraudulent-account-market.md)
- [Abuse-sharing economy note](../research/fraud/2016-thomas-abuse-sharing-economy.md)

## Review questions

1. Which attacker input is actually scarce in your current abuse operation?
2. Does your principal metric count disposable accounts or durable reduction in harm?
3. Which legitimate population pays the highest cost for your cheapest defense?
