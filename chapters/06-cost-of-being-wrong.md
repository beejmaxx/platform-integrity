# 6. The Cost of Being Wrong

<p class="chapter-subtitle">Match evidence thresholds to asymmetric error costs and intervention severity.</p>

<div class="chapter-meta"><span>Status: brief</span><span>Part II</span><span>Decision: when confidence is enough</span></div>

## Reader outcome

Create a cost-sensitive decision policy instead of using one detection threshold for every action.

## Starting model

```text
expected decision cost = P(false positive) * cost(false positive, action)
                       + P(false negative) * cost(false negative, delay)
                       + legitimate-user friction
```

## Decision questions

- How do reversibility, scope, duration, and collateral effects change the evidence standard?
- Whose costs count and over what time horizon?
- Are probabilities calibrated for the population receiving the intervention?
- What monitoring or challenge is justified before punitive action?

## Evidence needed

- Calibration and base-rate examples
- Appeal overturns and downstream user harm
- Decision-theory and procedural-justice research
- Cases where aggregate accuracy concealed subgroup or severity failures
