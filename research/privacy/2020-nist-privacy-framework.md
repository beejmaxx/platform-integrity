# NIST Privacy Framework

## Citation

National Institute of Standards and Technology. *NIST Privacy Framework: A Tool for Improving Privacy Through Enterprise Risk Management*, Version 1.0, 2020. [Official framework](https://www.nist.gov/privacy-framework).

## What it says

The framework gives organizations a voluntary, risk-based structure for identifying and managing privacy risk. It organizes activities into Identify-P, Govern-P, Control-P, Communicate-P, and Protect-P and treats privacy as an organizational and system-design concern across a data-processing ecosystem.

## Important claims

- Data processing can create consequences for individuals even when a system is functioning as intended.
- Privacy risk management belongs alongside enterprise risk management.
- Organizations need defined purposes, governance, data-processing inventories, controls, communication, and protection—not merely a privacy notice.

## Evidence

This is normative guidance from NIST, developed through a public process. It is not an empirical evaluation of any one control.

## Useful examples

The framework's profiles can express a current state and target state. For an integrity program, a profile can expose gaps between collecting a persistent identifier and governing its purpose, access, retention, and downstream reuse.

## Assumptions

Organizations can translate high-level outcomes into controls appropriate to their legal obligations, risk tolerance, and systems.

## Weaknesses / disagreements

The framework is intentionally technology- and jurisdiction-neutral. It does not determine whether a particular integrity signal is lawful, proportionate, or effective, and compliance with it is not a legal safe harbor.

## Implications for platform defense

Integrity telemetry should have a named purpose, accountable owner, data-flow map, access policy, retention period, and deletion path. “Useful for fraud” is too broad a purpose for unlimited cross-context linkage. Privacy risk should be assessed for derived identifiers and relationship graphs, not only raw personal data.

## Chapters this affects

Chapters 5, 7, 9, 13, 17, 18, 19, and 21.

## Questions raised

- How should a platform measure the privacy harm of a false attribution link?
- Which integrity uses should be technically isolated from advertising and personalization?
- When does additional collection have negative marginal decision value?
