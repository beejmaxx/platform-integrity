# The Abuse Sharing Economy

## Citation

Kurt Thomas et al. “The Abuse Sharing Economy: Understanding the Limits of Threat Exchanges.” RAID, 2016. [Google Research](https://research.google/pubs/the-abuse-sharing-economy-understanding-the-limits-of-threat-exchanges/). Accessed 2026-08-14.

**Source type:** measurement research  
**Evidence quality:** primary  
**Review status:** checked

## What it says

Using 45 million IP addresses observed abusing six Google services during a two-week 2015 snapshot, the authors studied infrastructure reuse across spam, fake-account registration, malicious hosting, and other abuse. Cross-service intelligence could identify some abusive traffic, but outright IP blacklisting produced an untenable false-positive volume.

## Important claims

- Adversaries reuse infrastructure across abuse types.
- Each service observes a biased slice of the same ecosystem.
- A predictive signal can be useful for added evidence while being unsafe as a direct ban rule.

## Assumptions and weaknesses

The observation window was short, limited to Google services, and IP meaning has continued to change with mobile networks, cloud services, proxies, and shared infrastructure.

## Implications for platform defense

Separate signal usefulness from enforcement sufficiency. Cross-context reputation can raise risk without establishing that a particular user or action is abusive.

## Chapters this affects

Chapters 6, 7, 9, 10, 12, 13, and 15.
