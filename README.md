# Solar Filament Segmentation

## Task Description

The goal is to develop an algorithm that generates accurate segmentation masks for individual solar filaments. For each filament, the predicted mask should capture its full extent, including fine-scale structures, while minimizing the inclusion of non-filament regions. The task aims to reliably and accurately characterize filament morphology across different solar observations.

## What Are the Main Challenges?

Although recent advances in object segmentation have achieved impressive performance across many domains, solar filament segmentation remains challenging for several reasons:

- **Fine-scale structures.** Accurately capturing fine filament structures, such as barbs, remains difficult. Barbs are thin, thread-like features that extend from the main body of a filament in characteristic directions. Their orientation relative to the filament spine provides important information about the filament’s magnetic field configuration.
- **Background noise and image quality.** Distinguishing filament material (dark regions) from background structures and noise is challenging. Since the observations used in this competition come from ground-based observatories, they are affected by various sources of noise and imaging artifacts. Accurately identifying fine-scale filament structures while suppressing background noise remains a major challenge.
- **Structural continuity.** Existing segmentation algorithms often struggle to identify solar filaments as continuous physical structures. Instead, they may produce fragmented segmentations or group nearby dark regions (“islands”) into clusters, resulting in incomplete or physically inconsistent representations of filament morphology.

Submissions will be evaluated on ground-based observations from the MAGFiLO dataset using the Panoptic Quality (PQ) metric, defined as follows:

```math
\mathrm{PQ}(Y,\hat{Y}) =
\frac{
\displaystyle\sum_{(y,\hat{y})\in\mathrm{TP}}
\mathrm{IoU}(y,\hat{y})
}{
|\mathrm{TP}| + 0.5|\mathrm{FP}| + 0.5|\mathrm{FN}|
}
```

where:

- \(Y\) is the set of all ground-truth segments \(y\).
- \(\hat{Y}\) is the set of all predicted segments \(\hat{y}\).
- \(\mathrm{IoU}\) denotes intersection over union.
- \(\mathrm{TP}\), \(\mathrm{FP}\), and \(\mathrm{FN}\) denote the sets of matched ground-truth and predicted segment pairs, unmatched predicted segments, and unmatched ground-truth segments, respectively.
- \(|\cdot|\) denotes the cardinality of a set.
