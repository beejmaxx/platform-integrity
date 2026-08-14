# 8. How Automation Interacts With Platforms

<p class="chapter-subtitle">Map capabilities and trust boundaries without confusing mechanism with legitimacy.</p>

<div class="chapter-meta"><span>Status: first draft</span><span>Part III</span><span>Decision: where trust belongs</span></div>

The same marketplace purchase can be produced by a person clicking a button, an accessibility tool generating input, a browser test, a script calling an API, or an AI agent acting under delegated authority. At the server, these paths eventually become requests that attempt to change platform state.

The mechanism matters because it changes observability and attack cost. It does not, by itself, determine whether the action is permitted or harmful.

## Start with the action, then trace the path

For every high-value action, map:

```text
principal -> authority -> controller -> client -> protocol -> service -> state change
```

The **principal** is the account or actor represented to the platform. **Authority** describes what that principal may do. The **controller** may be a person, script, organization, or agent. The **client** packages actions. The **protocol** carries them. The **service** validates them and changes state.

This map prevents two common errors. First, teams sometimes put policy in a client that an adversary controls. Second, they classify an entire surface—an API, emulator, or automation framework—as abusive even when legitimate users depend on it.

## Browsers and direct HTTP clients

Browser automation is ordinary infrastructure. The W3C [WebDriver specification](https://www.w3.org/TR/webdriver/) defines a remote-control interface for browsers and identifies testing, monitoring, and load testing as intended uses. A browser under automation can navigate, locate elements, execute scripts, and generate input through standardized commands.

A direct HTTP client skips the rendered interface and constructs requests itself. This can be cheaper and faster, but the server's security obligation is unchanged: authorize each meaningful operation, validate state transitions, enforce economic and concurrency constraints, and distrust client-supplied facts it can calculate itself.

Signals that a particular automation interface is active can be useful context. They are not stable proof of abuse. Cooperative software may declare itself; adversarial software may not; legitimate tools may resemble either. The [Robots Exclusion Protocol](../research/bot-detection/2022-ietf-robots-exclusion-protocol.md) illustrates the same boundary for crawlers: declaration communicates a preference but is not access authorization.

## APIs are policy surfaces

An official API makes automation legible. It can express scoped permissions, quotas, idempotency, audit identifiers, application identity, and revocation. This does more than improve developer experience: it lets a platform distinguish automation operating inside an explicit contract from clients improvising against a consumer interface.

But “used the API” still does not mean “safe.” A legitimate credential can be stolen, an authorized application can exceed user expectations, and individually valid calls can form a harmful campaign. API governance needs both authorization controls and behavior controls.

For human-directed and AI agents, define an **authority envelope**:

- which principal delegated authority;
- which actions and resources are in scope;
- monetary, volume, and time limits;
- whether further delegation is allowed;
- how the platform displays, revokes, and audits the authority;
- which actions require renewed confirmation.

This is stronger than trying to infer afterward whether each request “looked human.”

## Persistent protocols do not create trust

WebSockets, streaming APIs, and native binary protocols keep sessions open and can support rapid sequences of actions. Persistence changes rate measurement and incident containment: a single authenticated connection may produce thousands of state transitions without repeated handshakes.

It does not make client claims more trustworthy. Authorization, quotas, sequencing rules, and server-side invariants must apply to messages and state transitions, not only to connection establishment.

## Native, mobile, and game clients

Native clients can expose richer signals than browsers: build identity, local integrity state, input streams, device properties, and platform attestations. They can also be modified, instrumented, emulated, or run in unexpected environments. The defender should assume that a motivated user controls the endpoint while still recognizing that raising client-manipulation cost can be valuable.

The architectural priority is **server authority over scarce or fairness-critical state**. A game server should decide whether movement and resource changes obey the game's rules. A marketplace should decide whether inventory remains available and a purchase satisfies limits. A financial service should decide whether an instruction is authorized and within risk controls.

Client integrity mechanisms can add evidence and raise cost; they should not substitute for enforceable server invariants. Chapter 14 develops this tradeoff.

## Input automation, accessibility, and emulation

Macros, assistive technologies, remote desktops, emulators, and testing harnesses can produce atypical timing or interaction sequences. Their users may be disabled customers, support engineers, developers, commercial operators, or attackers.

Mechanism-only policy is sometimes justified—for example, a competitive game may prohibit all macros that alter the intended skill test. But that is a product and fairness decision, not a discovery that unusual input is inherently malicious. The platform should specify the protected outcome and provide an accessible path wherever possible.

An emulator similarly establishes an execution environment, not intent. If the environment undermines a required security control, restrict the capability that depends on that control. Avoid using the label as a proxy for guilt across unrelated actions.

## Declared identity requires verification

Some beneficial automation identifies itself. A crawler may send a recognizable user-agent string; a partner integration may present an application credential. Declaration improves coordination only when the platform can verify it. Google's [crawler verification guidance](https://developers.google.com/crawling/docs/crawlers-fetchers/verify-google-requests), for example, tells site operators to verify source networks or DNS rather than relying only on a request's name.

This produces three useful categories:

| Category | Meaning | Treatment |
|---|---|---|
| Declared and verified | The mechanism presents identity backed by a trusted method | Apply the policy and limits for that integration |
| Declared but unverified | The request asserts an identity | Treat the declaration as untrusted input |
| Undeclared or unknown | No reliable mechanism identity is available | Govern behavior, authority, and harm with other evidence |

None of the categories proves beneficial intent over time. Verification answers “which integration?”; monitoring still asks “what is it doing?”

## Review each surface systematically

For each client and protocol:

1. Identify the valuable state changes it can request.
2. Identify the principal and how authority is established, scoped, and revoked.
3. Mark every client-supplied claim the server cannot independently verify.
4. Define server-side invariants for safety, scarcity, fairness, and accounting.
5. Inventory legitimate automation, testing, accessibility, and partner use.
6. Decide which mechanism signals are corroboration and which are policy facts.
7. Add rate, economic, and campaign-level controls above individual requests.
8. Design containment that can revoke authority or capability without unnecessarily destroying identity.

The purpose of this map is defensive design. It does not require publishing bypass recipes, exploit chains, or platform-specific evasion instructions. A useful integrity book should explain where trust fails without lowering the cost of abuse.

## Research trail

- [W3C WebDriver note](../research/bot-detection/2026-w3c-webdriver.md)
- [IETF Robots Exclusion Protocol note](../research/bot-detection/2022-ietf-robots-exclusion-protocol.md)
- [Google crawler verification note](../research/bot-detection/2026-google-crawler-verification.md)
- [Acceptable automation](04-acceptable-automation.md)

## Review questions

1. Which platform invariant currently depends on honest client behavior?
2. Which legitimate users would be harmed by treating an automation surface as an abuse category?
3. Can an agent's authority be understood and revoked independently of its account credential?
4. Does verifying an integration identity change its limits, or merely its label?
