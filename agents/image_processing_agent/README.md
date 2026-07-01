# Image Processing Agent

**Job:** take raw images (leaf close-ups, whole-tree/drone shots, soil) and
turn them into structured text findings that the Advisory Agent can reason
over.

## Open design question

Two possible approaches — worth prototyping both before picking one:

1. **Dedicated vision model** (e.g. a fine-tuned classifier/detector) that
   outputs labels/scores, which get templated into text before being handed
   to the LLM.
2. **Multimodal LLM directly** (image + text in, text out) — skip the
   separate vision model entirely and let the model reason over the image.

## Suggested first prototype

- Input: a handful of images from the Citrus Leaves Dataset
  (see `../../docs/DATASETS.md`)
- Output: structured text per image, e.g.
  ```json
  {
    "crop": "citrus (sweet lime proxy)",
    "part": "leaf",
    "health_status": "diseased",
    "suspected_issue": "canker",
    "confidence": "medium",
    "notes": "dark lesions with yellow halo on leaf margin"
  }
  ```
- This structured output is what gets passed to the Advisory Agent.

## TODO

- [ ] Decide on approach 1 vs 2 above
- [ ] Load and preview sample images from the dataset
- [ ] Build a first pass classifier/prompt
- [ ] Define the exact structured output schema (align with `advisory_agent/`)
