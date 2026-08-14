# NIST SP 800-63-4 Digital Identity Guidelines

## Citation

National Institute of Standards and Technology. *Digital Identity Guidelines*, NIST SP 800-63-4, final July 2025. [Official online edition](https://pages.nist.gov/800-63-4/).

## What it says

The suite provides risk-based requirements for identity proofing, authentication, and federation. Its digital identity model distinguishes applicants, subscribers, claimants, credential service providers, verifiers, identity providers, and relying parties. It assigns separate assurance levels to proofing, authentication, and federation and adds requirements for continuous evaluation, fraud controls, privacy, customer experience, and redress.

## Important claims

- Proofing a claimed identity, authenticating control of an authenticator, and making an authorization decision are separate functions.
- Assurance should be selected according to the impacts of identity errors in the protected service.
- A verifier confirms possession and control of authenticators bound to a subscriber account; the relying party uses assertions and other context to grant access.
- Digital identity systems require privacy, usability, and redress considerations in addition to security.

## Evidence

This is current US federal technical guidance produced through public drafts and extensive comments. It is authoritative for its intended government scope and useful as a conceptual model elsewhere.

## Useful examples

A strongly authenticated account can still be operated abusively by its legitimate controller. Conversely, an account takeover can produce harmful behavior even though the account's earlier proofing record was accurate. These failures require different interventions.

## Assumptions

The service can identify relevant impacts and select controls appropriate to its users and transactions.

## Weaknesses / disagreements

The suite explicitly does not cover every machine-to-machine or API use case. Its government-service context does not settle private-platform policy. Higher assurance can also impose cost, exclusion, collection, and recovery burdens.

## Implications for platform defense

Do not label authentication, proofing, authorization, and behavioral attribution as one “identity” score. Store the claim each control supports. Select assurance and redress according to decision impact. For agents, separately represent the user or organization, the delegated principal, the authenticator, and the authority granted.

## Chapters this affects

Chapters 4, 5, 7, 8, 9, 14, 15, 17, and 18.

## Questions raised

- What assurance is proportionate for low-value pseudonymous participation?
- How should platforms represent delegated agent authority?
- How should identity correction propagate into integrity graphs and labels?
