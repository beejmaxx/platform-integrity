# RFC 9309: Robots Exclusion Protocol

## Citation

M. Koster, G. Illyes, H. Zeller, and L. Sassman. “Robots Exclusion Protocol.” IETF RFC 9309, September 2022. [RFC Editor](https://www.rfc-editor.org/rfc/rfc9309.html). Accessed 2026-08-14.

**Source type:** technical standard  
**Evidence quality:** primary  
**Review status:** checked

## What it says

The protocol lets service owners publish rules that cooperative automated crawlers are requested to honor when accessing URIs. The standard explicitly says these rules are not access authorization and are not a substitute for security controls.

## Important claims

- A crawler is an automated client, yet the standard assumes automation can be identified and governed cooperatively.
- Identity declared in a user-agent is part of policy communication, not strong attribution.
- A service can express different rules for different crawler product tokens.

## Weaknesses / disagreements

Non-cooperative clients can ignore or spoof the protocol. Compliance does not establish beneficial intent, and noncompliance alone does not resolve authorization or legal questions.

## Implications for platform defense

Automation can be a first-class authorized participant. Policy, identity, and enforcement cannot be collapsed into human-versus-bot classification.

## Chapters this affects

Chapters 1, 4, 7–10, and 18.
