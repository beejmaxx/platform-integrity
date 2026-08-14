# 14. Client Integrity and Attestation

<p class="chapter-subtitle">Use client assurance only for claims it can support and costs the ecosystem will accept.</p>

<div class="chapter-meta"><span>Status: brief</span><span>Part IV</span><span>Decision: whether to trust the client</span></div>

## Reader outcome

Compare server authority, code signing, secure boot, anti-tamper, attestation, and privileged anti-cheat by guarantee, bypass cost, privacy, compatibility, and maintenance.

## Decision questions

- What exact claim is attested and what remains outside the trust boundary?
- Does the mechanism increase platform attack surface or privilege risk?
- Which devices and legitimate configurations are excluded?
- Can server-authoritative design remove the need for invasive assurance?

## Evidence needed

- Trusted-computing and attestation specifications
- Security reviews and bypass histories at a safe abstraction
- Compatibility and privacy impact evidence
- Gaming and high-assurance case comparisons
