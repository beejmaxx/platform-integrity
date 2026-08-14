# IETF RFC 8981: IPv6 Temporary Addresses

## Citation

Gont, F., et al. “Temporary Address Extensions for Stateless Address Autoconfiguration in IPv6.” RFC 8981, February 2021. [RFC Editor](https://www.rfc-editor.org/rfc/rfc8981.html).

## What it says

The RFC standardizes temporary IPv6 addresses whose interface identifiers change over time. Its purpose is to reduce the ability to correlate a host's activity across time and networks through a stable address-derived identifier.

## Important claims

- Stable identifiers reused across contexts enable correlation.
- IPv6 addresses can expose such identifiers even when higher-layer payloads are encrypted.
- Temporary addresses narrow the window for trivial address-based correlation.

## Evidence

This is an IETF standards document explaining a privacy threat and protocol mechanism. It does not evaluate platform-integrity models.

## Useful examples

New temporary addresses are normally generated as older ones are deprecated. One legitimate host may therefore appear under multiple identifiers over time, while cookies or authenticated accounts preserve continuity at another layer.

## Assumptions

Implementations enable and correctly operate temporary address behavior; other stable identifiers may still permit correlation.

## Weaknesses / disagreements

Changing an address does not guarantee anonymity. DNS names, cookies, accounts, and other application-layer identifiers can remain stable. The RFC also does not imply that every changing address belongs to one device.

## Implications for platform defense

Treat a network address as time-bounded routing evidence. Do not use address churn alone as proof of evasion. More broadly, recognize that persistent integrity identifiers impose tracking costs even when created for a defensive purpose.

## Chapters this affects

Chapters 7, 9, 10, 13, and 18.

## Questions raised

- Which identity links should expire when their underlying identifiers rotate?
- How should models distinguish privacy-preserving churn from adversarial churn?
- What is the minimum persistence necessary for each integrity decision?
