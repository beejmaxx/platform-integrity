# 8. How Automation Interacts With Platforms

<p class="chapter-subtitle">Understand control surfaces without turning a defensive text into an abuse manual.</p>

<div class="chapter-meta"><span>Status: brief</span><span>Part III</span><span>Decision: where trust belongs</span></div>

## Reader outcome

Map how browsers, HTTP clients, APIs, sockets, native clients, emulators, input systems, modified clients, and AI agents can produce platform actions.

## Decision questions

- Which claims can the server verify independently?
- Where does the design trust client-supplied state or timing?
- Which automation paths are legitimate or accessibility-critical?
- What level of mechanism detail is necessary for defense and safe to publish?

## Safety boundary

Focus on capabilities, trust boundaries, and defensive implications. Exclude actionable bypass recipes, exploit chains, or platform-specific evasion instructions.

## Evidence needed

- Protocol and platform documentation
- Secure design guidance
- Accessibility interface behavior
- Post-incident lessons expressed at an appropriate defensive abstraction
