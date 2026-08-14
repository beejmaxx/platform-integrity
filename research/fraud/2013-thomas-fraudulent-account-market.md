# Trafficking Fraudulent Accounts

## Citation

Kurt Thomas, Damon McCoy, Chris Grier, Alek Kolcz, and Vern Paxson. “Trafficking Fraudulent Accounts: The Role of the Underground Market in Twitter Spam and Abuse.” USENIX Security, 2013. [Google Research](https://research.google/pubs/trafficking-fraudulent-accounts-the-role-of-the-underground-market-in-twitter-spam-and-abuse/). Accessed 2026-08-14.

**Source type:** measurement research  
**Evidence quality:** primary  
**Review status:** checked

## What it says

The authors observed 27 merchants selling fraudulent Twitter accounts over ten months, measured prices and availability, and collaborated with Twitter to identify and disable millions of accounts associated with the market. The observed merchants appeared responsible for a material share of accounts later flagged for spam during active months.

## Important claims

Accounts are production inputs with a market price. Registration defenses, account survival, buyer demand, and replacement cost jointly shape abuse economics. Individual accounts are less informative than the supply operation and campaign.

## Assumptions and weaknesses

The market, platform, and defenses date to 2012–2013. Merchant coverage was incomplete, classification and takedown relied on platform collaboration, and current prices cannot be inferred from the study.

## Implications for platform defense

Measure attacker capacity, account replacement time, campaign survival, and market substitution rather than celebrating raw account-removal counts.

## Chapters this affects

Chapters 3, 6, 9, 13, 15, 19, and 20.
