# W3C WebDriver

## Citation

W3C Browser Testing and Tools Working Group. *WebDriver*, Working Draft, 2 July 2026. [Specification](https://www.w3.org/TR/webdriver/).

## What it says

WebDriver is a platform- and language-neutral remote-control interface for web user agents. It lets an out-of-process program navigate, inspect documents, interact with elements, generate input, execute scripts, and manage browser sessions.

## Important claims

- Browser automation is a standardized capability.
- The specification's intended users include developers and testers building automated tests, monitoring, load testing, and other tools.
- Cooperative user agents can expose that they are under WebDriver control.

## Evidence

This is a current W3C Working Draft grounded in browser implementations. It defines capability, not the prevalence or abuse rate of automated browsers.

## Useful examples

The same interface that can drive large-scale activity can also perform release tests, synthetic monitoring, or an accessibility-support workflow. Presence of the interface identifies a mechanism under cooperative conditions, not the governing purpose of an action.

## Assumptions

Conforming implementations expose the standardized behavior. Other automation techniques need not use or accurately declare WebDriver.

## Weaknesses / disagreements

The cited version is a Working Draft and may change. The standard does not prescribe platform policy or provide a dependable bot-detection guarantee.

## Implications for platform defense

Do not equate browser automation with abuse. Govern authority, volume, behavior, and consequences. Treat declared automation state as one signal whose reliability depends on the client and use case.

## Chapters this affects

Chapters 1, 4, 7, 8, 10, 11, and 14.

## Questions raised

- When should platforms offer a supported API instead of forcing legitimate automation through a browser?
- Which accessibility and testing uses are harmed by mechanism bans?
- What evidentiary weight should cooperative declaration receive?
