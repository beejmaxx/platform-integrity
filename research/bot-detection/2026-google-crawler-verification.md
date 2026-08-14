# Google Crawler Verification Guidance

## Citation

Google. “Verify Requests from Google Crawlers and Fetchers.” Google Crawling Infrastructure documentation, accessed August 2026. [Official guidance](https://developers.google.com/crawling/docs/crawlers-fetchers/verify-google-requests).

## What it says

Google documents methods for verifying whether requests that claim to come from its crawlers and fetchers actually originate from Google-controlled infrastructure. Methods include checking published IP ranges or performing forward-confirmed reverse DNS for relevant crawler categories.

## Important claims

- A request's declared crawler name is not sufficient verification.
- Mechanism identity can be backed by network or DNS evidence.
- Different crawler and fetcher categories have different verification patterns.

## Evidence

This is first-party operational documentation for Google infrastructure. It demonstrates one verification design, not a universal crawler identity standard.

## Useful examples

A platform may permit a verified search crawler while limiting an unverified request presenting the same user-agent string. Even verified identity does not remove the need for rate and behavior policy.

## Assumptions

Operators correctly implement the verification procedure and keep dependencies current.

## Weaknesses / disagreements

Network and DNS verification binds requests to infrastructure, not to beneficial intent in every transaction. It is specific to Google and can fail operationally if implemented carelessly.

## Implications for platform defense

Separate declared, verified, and behaviorally trusted automation. Prefer scoped application credentials or documented verification over names in client-controlled headers. Continue monitoring verified integrations for compromised authority or policy violations.

## Chapters this affects

Chapters 1, 4, 7, 8, 10, and 18.

## Questions raised

- What interoperable mechanism should future agents use to present delegated identity and authority?
- How should verification failures degrade service without causing broad outages?
- Which information can a platform disclose without creating an evasion oracle?
