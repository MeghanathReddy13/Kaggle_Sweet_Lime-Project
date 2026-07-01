# Advisory Agent

**Job:** take the structured findings from the Image Processing Agent
(across one or more images — leaves, whole-tree, soil) and produce the
actual farmer-facing recommendation.

## Expected input (from Image Processing Agent)

A list of structured findings, e.g. one entry per image/tree analyzed.
Schema should be agreed jointly with `image_processing_agent/`.

## Expected output

Something like:

```json
{
  "overall_health_score": "7/10",
  "summary": "Most of the orchard looks healthy. A few trees show early signs of canker.",
  "issues_detected": [
    {"issue": "canker", "severity": "low", "affected_area": "north-east section"}
  ],
  "recommendations": [
    "Apply copper-based spray to affected trees",
    "Monitor north-east section weekly for spread"
  ]
}
```

## Open questions

- How much crop-specific agronomic knowledge do we need to hand-build vs.
  rely on the base LLM's existing knowledge?
- Do we want a numeric health score, a qualitative summary, or both?
- How do we handle uncertainty (e.g. "possibly root rot, recommend manual
  inspection") vs. confident diagnoses?

## TODO

- [ ] Agree on the input schema with `image_processing_agent/`
- [ ] Build a first prompt/pipeline that takes structured findings → advice
- [ ] Test against a few known-answer cases (obviously healthy / obviously diseased)
- [ ] Start building a small crop-specific knowledge base (sweet lime diseases,
      common treatments) to ground the recommendations
