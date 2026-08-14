# IETF RFC 6598: Shared IPv4 Address Space

## Citation

Weil, J., et al. “IANA-Reserved IPv4 Prefix for Shared Address Space.” RFC 6598, April 2012. [RFC Editor](https://www.rfc-editor.org/rfc/rfc6598.html).

## What it says

RFC 6598 reserves `100.64.0.0/10` for service-provider shared address space used in carrier-grade NAT deployments. The design allows providers to continue supporting IPv4 growth by placing customer networks behind shared translation infrastructure.

## Important claims

- Shared address space is deliberately reusable and not globally routable.
- Carrier-grade NAT introduces an additional translation boundary between subscribers and the public internet.
- Network topology can make address-based assumptions fail.

## Evidence

This is an IETF Best Current Practice defining operational address space, not a measurement of abuse detection accuracy.

## Useful examples

Several subscribers can reach a platform through shared provider infrastructure. A platform that interprets a public-facing network address as a household, device, or person can therefore merge unrelated actors.

## Assumptions

The platform sees the external endpoint after network translation and typically lacks the provider's internal subscriber mapping.

## Weaknesses / disagreements

The RFC alone does not quantify how many users share a particular observed address or how long assignments persist. IP reputation can still be predictive at an aggregate level.

## Implications for platform defense

Use IP evidence for routing context, rate controls, correlation, and investigation while preserving its entity ambiguity. Add time, account, session, device, payment, and behavior evidence before expanding severe enforcement. Calibrate network-level controls for the legitimate population behind shared infrastructure.

## Chapters this affects

Chapters 7, 9, 10, 13, 15, and 16.

## Questions raised

- Which network interventions remain safe at very high sharing factors?
- Can a platform estimate sharing without increasing privacy risk?
- How quickly should negative network reputation decay?
