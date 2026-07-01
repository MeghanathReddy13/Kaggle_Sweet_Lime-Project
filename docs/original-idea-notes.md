# Original Idea — Notes from the Meeting

Cleaned-up summary of the Google Meet discussion this project is based on.


## Core concept

A drone flies over a field/orchard and takes images. The question the team
was working through: does a single LLM (if it's multimodal) handle the image
understanding directly, or do we need a **separate image processing /
computer vision model** whose output text then feeds into an LLM?

Noted trend: language models, image models, and voice models are converging
— multimodal models are increasingly just one sequence-to-sequence
transformer under the hood. So it's plausible one model could do both image
understanding and reasoning. This needs to be tested rather than assumed —
"different crops might need different handling, we don't know yet, we'll
analyze it."

## The pipeline as discussed

1. **Image capture** — drone (or eventually just phone photos) captures
   images of the crop: leaves, whole trees, and optionally soil.
2. **Image Processing Agent** — analyzes the images and outputs text:
   plant health status, signs of disease/pests, soil condition, etc.
3. **Advisory Agent** — takes that structured output and produces the
   actual recommendation for the farmer: overall evaluation of the field,
   what's healthy / what needs attention, whether pests are present, what
   to spray, or flags specific issues like root rot.

Example of the kind of output envisioned: *"I'm looking at crop leaf
health — are there pests, what are they, what should be sprayed? Here's
what I'd suggest."* Or, at the orchard level (e.g. a whole sweet lime
grove): *"These trees show signs of pests — here's the suggestion. Also
seeing some root rot over here."*

## Scope decisions

- **Start with one crop.** Candidates discussed: sweet lime / mosambi
  (చీనీ తోట), chilli (మిరప), cotton. Sweet lime was the crop leaning towards
  first, partly because it's what's accessible/relevant right now.
- the plan is to **source images online** (public datasets, web images)
  to get the pipeline working, and swap in real field/drone data later.
- Open question raised: does the image-processing output change meaningfully
  from crop to crop (sweet lime vs. chilli vs. cotton)? Assumption is yes,
  to some degree — worth confirming empirically rather than assuming.
- Also an open question: how much per-crop agronomic knowledge needs to be
  built into the Advisory Agent (disease knowledge, treatment knowledge,
  etc.) versus what a general-purpose LLM already knows.

## Plan going in

One person to write up the full framework/architecture and create the
GitHub repo, sharing it so the rest of the team can each pick up a piece
(image agent, advisory agent, dataset work, etc.) as a "follow this
architecture" starting point rather than one person writing 100% of the
implementation solo.
