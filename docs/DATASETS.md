# Dataset Research — Sweet Lime / Citrus Crop Health


## Best starting points

### 1. Citrus Leaves & Fruits Dataset (Rauf et al., 2019)
The most-used public citrus disease dataset. Not sweet-lime-specific, but
citrus-genus-level, which is the closest broad match available.
- **Diseases covered:** Black spot, Canker, Scab, Greening, Melanose, plus healthy
- **Size:** 759 images across citrus leaves and fruit
- **Sources:**
  - Mendeley Data: https://data.mendeley.com/datasets/3f83gxmv57/2  (We'll USE this one, it has images of fruit and leaves)
  - TensorFlow Datasets (`citrus_leaves`): https://www.tensorflow.org/datasets/catalog/citrus_leaves
  - Kaggle mirror: https://www.kaggle.com/datasets/myprojectdictionary/citrus-leaf-disease-image
  - Kaggle mirror: https://www.kaggle.com/datasets/jonathansilva2020/dataset-for-classification-of-citrus-diseases

### 2. Sweet Orange Leaf Dataset (Bangladesh, 2024)
*Citrus sinensis* (sweet orange) is a much closer botanical relative to
sweet lime than lemons/limes are — both are "sweet citrus" and share a lot
of the same disease pressures. This is a newer, more comprehensive dataset
than #1.
- **Diseases covered:** Citrus Canker, Citrus Greening, Citrus Mealybugs,
  Die Back, Foliage Damage, Spiny Whitefly, Powdery Mildew, Shot Hole,
  Yellow Dragon, Yellow Leaves, plus healthy
- **Source:** https://www.sciencedirect.com/science/article/pii/S2352340924006802

### 3. FruitNet — Indian Fruits Image Dataset with Quality
Indian-sourced images (shot on phone cameras), labeled Good/Bad/Mixed
quality, across 6 fruit classes **including Lime**. Useful for post-harvest
fruit-quality grading rather than orchard/leaf health, but valuable because
it's actually Indian-sourced imagery, not lab-controlled Western data.
- **Source:** https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8668825/

## Architecture reference (not a citrus dataset, but very relevant)

### Plantation Monitoring Using Drone Images (WASSAN, Hyderabad + collaborators, 2025)
This is the closest match to what was actually described in the meeting:
low-cost drone RGB images over Indian farms, classifying individual trees
as **Good health / Stunted / Dead**, annotated with CVAT, detection via
YOLOv8. Currently built on mango trees, not citrus — but it's essentially
the exact pipeline shape we want (drone image → per-tree health label), and
the authors state the dataset + code are intended to be open-sourced for
research use. Worth reading closely for the annotation/labeling approach,
and worth reaching out to the authors about extending to citrus/sweet lime.
- **Paper:** https://arxiv.org/abs/2502.08233
- **Full text:** https://arxiv.org/html/2502.08233v1


## Recommendation for phase 1

1. Start prototyping the Image Processing Agent on the **Citrus Leaves
   Dataset** (#1) since it's the smallest/easiest to get running end-to-end.
2. Expand disease coverage using the **Sweet Orange dataset** (#2) once the
   pipeline works, since it's the better botanical match and has more
   disease classes.
3. Use the **WASSAN drone paper** (above) as the architectural template for
   the "whole orchard from above" version of the pipeline, even before real
   sweet lime drone footage exists.
4. Treat all of the above as a stand-in for the real thing — flag clearly
   in any demo that results are trained on general citrus, not sweet lime
   specifically, until real/species-matched data is collected.
