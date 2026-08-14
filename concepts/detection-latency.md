# Detection Latency

## Decision problem

How long can the platform wait for better evidence before harm becomes unacceptable?

## Working model

```text
value of waiting = expected reduction in decision error
                 - expected harm accumulated while waiting
                 - operational and user cost of temporary controls
```

Separate signal availability, feature computation, model inference, decision queue, human review, action propagation, and appeal latency.

## Research questions

- Which harms are step functions, compounding processes, or recoverable losses?
- When can a reversible hold purchase information safely?
- How should review backlogs change automated thresholds?
- What is the correct latency SLO when labels arrive weeks later?

## Affected chapters

Chapters 6, 7, 15, 16, 17, and 19.
