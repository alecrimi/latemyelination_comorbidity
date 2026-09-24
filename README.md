# Hierarchical Detection of Neonatal Brain Pathologies Using a Two-Stage Deep Learning Framework from Magnetic Resonance Imaging

Official implementation of the paper:

> **Hierarchical Detection of Neonatal Brain Pathologies Using a Two-Stage Deep Learning Framework from Magnetic Resonance Imaging**

**Authors**

- Christian Ahwoi Ampiah
- Tina Malala
- Alessandro Crimi

---

## Overview

This repository implements a hierarchical deep learning pipeline for automated neonatal brain pathology detection from paired **T1-weighted** and **T2-weighted** MRI.

Unlike conventional flat classifiers, the proposed framework mirrors the reasoning of expert neuroradiologists through a two-stage decision process:

1. **Stage 1**
   - Estimate biological (myelin-informed) brain age
   - Compute the brain-age gap
   - Detect delayed myelination (preterm)

2. **Stage 2**
   - Classify structural brain abnormalities:
     - Normal
     - Hypoxic-Ischaemic Encephalopathy (HIE)
     - Hydrocephalus

Both stages are implemented using independent 3D ResNet-18 models.

---

## Pipeline


![architecture](https://github.com/alecrimi/latemyelination_comorbidity/blob/main/architecture.png)

---

## Features

- Hierarchical diagnosis pipeline
- Brain-age regression
- Brain-age gap computation
- Preterm screening
- Structural pathology classification
- Dual-modality MRI (T1 + T2)
- PyTorch implementation
- Pretrained models available


---

## Dataset

The experiments were conducted on the publicly available neonatal MRI dataset described in:

Akinci et al.

Please obtain the dataset from the original source and follow the preprocessing described in the paper.

---
 
# Pretrained Models

The pretrained models accompanying the paper are available on Hugging Face:

👉 **https://huggingface.co/Alecrimi/infant_pathology**

The repository contains:

| Checkpoint | Description |
|------------|-------------|
| `best_age_regressor.pth` | Stage 1: Brain-age regression model used to estimate myelin-informed age and compute the brain-age gap. |
| `best_brain_classifier.pth` | Stage 2: Structural pathology classifier (Normal / HIE / Hydrocephalus). |

---

## Download from Hugging Face

```python
from huggingface_hub import hf_hub_download

checkpoint = hf_hub_download(
    repo_id="Alecrimi/infant_pathology",
    filename="best_age_regressor.pth"
)
```

or

```python
checkpoint = hf_hub_download(
    repo_id="Alecrimi/infant_pathology",
    filename="best_brain_classifier.pth"
)
```

As a baseline without different stage classifier is given in the notebook: myelin_4class_classifier.ipynb

---
  
## Citation

If you use this repository in your work, please cite

```bibtex
@article{Ampiah2026Hierarchical,
  title={Hierarchical Detection of Neonatal Brain Pathologies Using a Two-Stage Deep Learning Framework from Magnetic Resonance Imaging},
  author={Ampiah, Christian Ahwoi and Malala, Tina and Crimi, Alessandro},
  journal={},
  year={2026}
}
```

---

## License

This project is released under the MIT License.

---

## Acknowledgements

If you use the pretrained models, please also cite the accompanying paper.

The pretrained checkpoints are hosted on Hugging Face:

https://huggingface.co/Alecrimi/infant_pathology
