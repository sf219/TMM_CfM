# Image Coding for Machines via Feature-Preserving Rate-Distortion Optimization

**Samuel Fernández-Menduiña, Eduardo Pavez, Antonio Ortega**  
University of Southern California  
[arXiv:2504.02216](https://arxiv.org/abs/2504.02216)

---

## Abstract

We propose a method for image coding that optimizes compression for machine-based analysis rather than human perception. The method modifies the rate–distortion optimization (RDO) process to preserve the features that downstream vision models use for inference. By linearizing the feature extractor, we derive a block-wise distortion metric that closely approximates the distance between original and decoded features. This allows efficient integration into standard codecs with minimal complexity increase at the encoder and no changes at the decoder. Experiments using AVC and HEVC show consistent bitrate savings while maintaining accuracy in representative vision tasks.

---

## Motivation

Most image codecs are optimized for human viewing. However, a large fraction of images today are consumed by machine vision systems. In such cases, minimizing pixel-level distortion (e.g., SSE) is not ideal because downstream task performance depends on higher-level features.

This work addresses the problem of optimizing compression directly for machine analysis by adjusting the distortion term in the RDO loop. The goal is to make the codec allocate bits where they matter most for preserving task-relevant features.

---

## Contributions

1. A theoretical formulation linking feature preservation to RDO through a first-order Taylor expansion of the feature extractor.  
2. A practical distortion metric, called **input-dependent squared error (IDSE)**, that enables block-wise optimization using standard encoder structures.  
3. A computationally efficient feature sketching approach to approximate large Jacobians.  
4. Integration into existing codecs (AVC, HEVC) with negligible decoder overhead and moderate encoder complexity.  
5. Empirical validation showing consistent bitrate savings for equivalent task accuracy.

---

## Method Overview

### Feature-based distortion

Let \( f(x) \) denote the feature extractor. Instead of minimizing pixel-domain distortion \( \|x - \hat{x}\|^2 \), we minimize a feature-domain distance \( \|f(x) - f(\hat{x})\|^2 \).  
Since \( f \) is nonlinear, we linearize it around the input:

\[
f(\hat{x}) \approx f(x) + J(x)(\hat{x} - x),
\]

where \( J(x) \) is the Jacobian of the feature extractor. The resulting approximation gives a quadratic distortion term:

\[
D_f(x, \hat{x}) \approx (\hat{x} - x)^\top J(x)^\top J(x)(\hat{x} - x).
\]

### Block-wise localization

To make this computation compatible with block-based encoders, we partition \( x \) into blocks and derive a per-block cost that accounts for the local contribution of each region to the overall feature distortion. The corresponding metric, called IDSE, can be computed efficiently using a small sketch of the Jacobian.

### Integration into RDO

The encoder replaces the standard SSE term in the RDO loop by a convex combination of SSE and IDSE:

\[
J = R + \lambda \, D_\text{IDSE},
\]

where \( \lambda \) is the Lagrange multiplier as in conventional RDO. This maintains codec compatibility while improving feature preservation.

---

## Experimental Setup

- **Codecs:** AVC FRExt, HEVC reference software  
- **Datasets:** COCO images and subsets of other standard image collections  
- **Feature extractors:** ResNet-50 backbone (FPN setup)  
- **Downstream tasks:** object detection and classification  
- **Baselines:** standard SSE-RDO and feature-based RDO using direct feature distances  
- **Evaluation metrics:** BD-rate savings, task accuracy, and computational cost  

---

## Results

- **Performance:** IDSE-RDO achieves 2–4% average BD-rate improvement compared to feature-distance RDO, with equivalent task accuracy.  
- **Complexity:** Encoder runtime increases moderately (feature extraction + sketch computation), decoder cost unchanged.  
- **Interpretation:** The learned feature sensitivity maps show that the encoder allocates more bits to semantically relevant regions (e.g., object boundaries).  

| Codec | Baseline | Proposed | BD-rate (↓) | Accuracy |
|-------|-----------|-----------|-------------|-----------|
| AVC   | SSE-RDO   | IDSE-RDO | −3.1% | same |
| HEVC  | SSE-RDO   | IDSE-RDO | −3.8% | same |

---

## Discussion

The results confirm that approximating feature distortion via local Jacobian sketches can effectively guide bit allocation. The method is general, codec-agnostic, and compatible with existing standard encoders. It offers a bridge between pixel-level compression and feature-level preservation without requiring a neural codec.

Limitations include the reliance on precomputed features and potential mismatch if the downstream model changes. Future work will address online adaptation of the IDSE metric and extensions to video coding.

---

## Code and Resources

- **Repository:** [https://github.com/sf219/TMM_CfM](https://github.com/sf219/TMM_CfM)  
- **Documentation:** [https://sf219.github.io/TMM_CfM/](https://sf219.github.io/TMM_CfM/)  
- **License:** MIT  

Instructions for reproducing experiments and configuration scripts are provided in the repository.

---

## Citation

If you use this work, please cite:

```bibtex
@article{fernandez2025cfm,
  title={Image Coding for Machines via Feature-Preserving Rate-Distortion Optimization},
  author={Fernández-Menduiña, Samuel and Pavez, Eduardo and Ortega, Antonio},
  journal={IEEE Transactions on Multimedia},
  year={2025},
  note={arXiv:2504.02216}
}
