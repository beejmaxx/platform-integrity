# 9. Identity and Attribution

<p class="chapter-subtitle">Act on the entity the evidence identifies—not the person an identifier merely suggests.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part III</span><span>Decision: what entity to act on</span></div>

A hundred abusive accounts share an IP address. Is that a bot farm, a university residence, a mobile carrier, a corporate network, a VPN exit, or some mixture of them?

The platform has found a relationship. It has not yet identified the actor.

## Keep the entity ladder intact

Integrity systems routinely collapse several layers:

```text
request -> session -> client instance -> device -> account -> person -> organization
```

A request is one attempted interaction. A session groups interactions under a platform convention. A client instance is an installation or storage context. A device is a physical or virtual execution environment. An account is a platform principal. A person may control several accounts or share one. An organization coordinates people, infrastructure, and capital.

These are relationships, not synonyms.

| Identifier or evidence | Strongest ordinary claim | What it does not prove |
|---|---|---|
| Request ID | One recorded attempt | Same controller as another request |
| Session token | Control of a session credential | Original account owner or unique device |
| Cookie or app-install ID | Same retained storage context | Same hardware or person |
| Public IP address | Traffic observed through a network endpoint | Unique household, device, or person |
| Device fingerprint | Similar observed properties under a method | Stable physical device or controller |
| Account credential | Control of an authenticator or session | Beneficial owner, intent, or uncompromised use |
| Payment instrument | A funding relationship | Unique purchaser or organization |
| Identity-proofing record | Evidence matched to a claimed identity at a point in time | Who performs every later action |

This table should influence enforcement scope. If the strongest claim concerns a session, revoke or challenge the session. If it concerns a transaction, hold the transaction. Expanding immediately to every account ever connected to an IP turns a weak relation into collective punishment.

## Network addresses are routing evidence

IP addresses are useful. They support velocity controls, rough network reputation, incident correlation, and graph investigation. They are not durable personal identifiers.

[RFC 6598](https://www.rfc-editor.org/rfc/rfc6598.html) reserves shared IPv4 address space specifically to support carrier-grade network address translation. Many subscribers can therefore appear behind shared network infrastructure. In the other direction, one device may change networks frequently. [RFC 8981](https://www.rfc-editor.org/rfc/rfc8981.html) defines temporary IPv6 addresses whose identifiers vary over time to reduce cross-activity correlation.

The practical result is asymmetric:

- a shared address can merge unrelated actors;
- changing addresses can split one actor into many apparent identities;
- a proxy can deliberately separate the apparent network from the controller;
- a compromised host can make an innocent device part of abusive infrastructure.

IP evidence remains valuable when its claim is stated narrowly and combined with time, protocol, account, device, payment, and behavioral context.

## Authentication, proofing, and authorization answer different questions

NIST's [Digital Identity Guidelines](https://pages.nist.gov/800-63-4/) separate identity proofing, authentication, and federation into different assurance processes. In its model, a verifier confirms possession and control of authenticators bound to a subscriber account; a relying party then uses identity information and other factors for authorization decisions.

That separation matters for integrity engineering:

- **Identity proofing:** what evidence supports the claimed real-world identity?
- **Authentication:** what confidence do we have that the claimant controls the account's authenticator now?
- **Authorization:** what may this authenticated principal do?
- **Attribution:** what evidence links the observed harmful activity to a controller or organization?

Strong authentication can reduce account takeover while leaving automated misuse by the legitimate account holder untouched. Strong proofing can raise account replacement cost while creating exclusion, privacy, and recovery burdens. Neither proves intent.

An account's controller can also change over time through theft, sale, delegation, shared use, or recovery. Attribution edges therefore need timestamps, not just confidence scores.

## Model attribution as a graph of claims

Represent each link explicitly:

```text
(entity A) -[relationship, source, time window, confidence]-> (entity B)
```

Examples include “session authenticated to account,” “requests used the same payment token,” “device estimate observed both accounts,” or “reviewer confirmed coordinated operation.” Store the source and time window because relationships decay and methods change.

Confidence should reflect competing explanations, not only match strength. Two accounts sharing a rare device signal and a payment instrument in the same hour may support a stronger link than two accounts using the same IP over a year. Negative evidence matters too: simultaneous activity in distant contexts may contradict a single-device hypothesis, while a public cloud range may explain a dense network hub.

Do not convert the graph into guilt by association. High-degree infrastructure—mobile gateways, workplaces, libraries, payment processors, and hosting providers—naturally connects unrelated actors. Graph expansion should usually produce candidates for additional evidence, not automatic enforcement.

## Separate coordinated control from common characteristics

Integrity teams often seek “account farms,” but several phenomena can look similar:

- one operator controls many accounts;
- many contractors follow the same playbook;
- unrelated users run the same commercial tool;
- compromised accounts receive commands from shared infrastructure;
- ordinary users converge on a popular strategy;
- a platform experiment or software update changes behavior at once.

Coordination is a claim about dependence. Similarity is only one possible sign. Stronger evidence includes shared scarce resources, synchronized action serving a common objective, money flows, repeated handoffs, and consistent infrastructure reuse—evaluated against benign base rates.

The 2013 study *Trafficking Fraudulent Accounts* documented specialized participants creating, selling, and using accounts. Its enduring lesson is that the account visible to a platform may be one replaceable asset in a larger production chain. The platform may need to intervene against the capability or economic network, not merely delete the presented account.

## Choose the intervention scope by claim strength

When deciding whether to act on a request, session, account, device cluster, household, or organization, ask:

1. Which entity is directly implicated in the harmful event?
2. Which links are observed, which are derived, and which are inferred?
3. What benign process could produce each link?
4. How current is the relationship?
5. What additional harm will occur while evidence is gathered?
6. Can the intervention be narrowed to the capability or value transfer at risk?
7. How will a wrongly linked user separate themselves and recover?

Confidence and scope interact. An uncertain account link may justify observation. A confirmed compromised session may justify immediate revocation. Organization-wide removal demands evidence of coordinated control and policy responsibility proportionate to that breadth.

## Recourse must be able to repair attribution

An appeal system that only asks “was the model score correct?” cannot fix a mistaken identity graph. Reviewers need to see which entity was acted upon, the links that expanded the action, their age and source, and plausible shared-infrastructure explanations.

Correction must propagate. If a device cluster is split, future features, watchlists, reviewer tools, and training labels should not silently preserve the old association. Otherwise an overturned decision becomes a permanent shadow record.

Attribution is probabilistic, temporal, and purpose-specific. Good integrity systems make that uncertainty operational instead of hiding it behind an identifier.

## Research trail

- [NIST Digital Identity Guidelines note](../research/identity/2025-nist-digital-identity-guidelines.md)
- [Shared IPv4 address space note](../research/identity/2012-ietf-shared-address-space.md)
- [Temporary IPv6 addresses note](../research/identity/2021-ietf-ipv6-temporary-addresses.md)
- [Fraudulent-account markets note](../research/fraud/2013-thomas-fraudulent-account-market.md)
- [The Abuse Sharing Economy note](../research/fraud/2016-thomas-abuse-sharing-economy.md)

## Review questions

1. Which production identifier is treated as a person even though it identifies something narrower?
2. Where can shared infrastructure cause enforcement to expand across innocent users?
3. Does the attribution graph preserve time, source, uncertainty, and contradictory evidence?
4. Can an appeal actually remove a bad link from every downstream system?
