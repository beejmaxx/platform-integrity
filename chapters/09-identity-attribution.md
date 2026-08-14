# 9. Identity and Attribution

<p class="chapter-subtitle">Do not collapse request, session, device, account, person, organization, and bot farm.</p>

<div class="chapter-meta"><span>Status: brief</span><span>Part III</span><span>Decision: what entity to act on</span></div>

## Reader outcome

Express attribution as a confidence-bearing relationship and choose an intervention scope that tolerates shared infrastructure and uncertain identity.

## Decision questions

- What entity does each signal actually identify?
- How do NAT, VPNs, proxies, shared devices, recycled identifiers, and account transfer affect inference?
- When does linking evidence justify graph expansion or only added monitoring?
- How can a wrongly linked person or household recover?

## Evidence needed

- Device and network measurement limitations
- Entity-resolution calibration
- Account-farm and synthetic-identity studies
- Privacy and discrimination risks from persistent linkage
