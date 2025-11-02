---
layout: default
title: Image Coding for Machines via Feature-Preserving RDO
description: “We propose a method for image coding that compresses images while preserving performance in computer vision methods by preserving task-relevant features via a modified rate-distortion optimization framework.”
---

<div align="center">

# TMM_CfM  
**Image Coding for Machines via Feature-Preserving Rate-Distortion Optimization**  
[Samuel Fernández-Menduiña](mailto:sf219@usc.edu) · Eduardo Pavez · Antonio Ortega  
[arXiv:2504.02216](https://arxiv.org/abs/2504.02216)

</div>

# Image Coding for Machines via Feature-Preserving Rate-Distortion Optimization  
**Samuel Fernández-Menduiña, Eduardo Pavez, Antonio Ortega**  
University of Southern California  
[arXiv:2504.02216](https://arxiv.org/abs/2504.02216)

---

## At a Glance  
Our method introduces a feature-preserving rate–distortion optimization (RDO) metric that targets machine-vision performance rather than human viewing. By linearizing the feature extractor, we derive a block-wise metric (IDSE) compatible with standard codecs. Experiments with AVC and HEVC show consistent bitrate savings with no decoder changes.

---

## Overview  
### What’s new  
- We derive a distortion metric in feature space using a first-order Taylor expansion of the extractor.  
- We localize the metric block-wise (IDSE) so it can be integrated into existing encoder structures.  
- We apply sketching to approximate large Jacobian matrices efficiently.  
- We implement the method with standard image codecs, maintaining decoder compatibility while improving machine-task performance.

---

## Experimental Setup  
- **Codecs used**: AVC FRExt, HEVC reference software  
- **Datasets**: COCO images, additional standard image sets  
- **Feature extractors**: ResNet-50 backbone (FPN context)  
- **Downstream tasks**: object detection, image classification  
- **Baselines**: SSE-RDO, feature-distance RDO  
- **Metrics**: BD-rate savings, task accuracy, encoder overhead

---

## Results  
- The proposed IDSE-RDO achieves on average 2 %–4 % BD-rate improvement compared to feature-distance RDO, while maintaining task accuracy.  
- Encoder complexity increases moderately (due to feature extraction and sketching), and decoder complexity is unchanged.  
- Analysis shows that bit allocation focuses more on semantically important regions (e.g., object boundaries, high-feature-sensitivity areas).

---

## For Whom  
This work is relevant for researchers and engineers working on image/video compression for machine consumption (rather than human viewing), especially in scenarios where downstream vision tasks (detection, classification) are central and existing codecs are used.

---

## Cite  
If you use this work, please cite:

```bibtex
@article{fernandez2025cfm,
  title     = {Image Coding for Machines via Feature-Preserving Rate-Distortion Optimization},
  author    = {Fernández-Menduiña, Samuel and Pavez, Eduardo and Ortega, Antonio},
  journal   = {IEEE Transactions on Multimedia},
  year      = {2025},
  note      = {arXiv:2504.02216}
}
