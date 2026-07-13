# Deep Learning Algorithms for Medical Image Representation Learning and Understanding

**Héctor Carrión**
PhD, Computer Science & Engineering — University of California, Santa Cruz — 2026

[![Dissertation: CC BY 4.0](https://img.shields.io/badge/Dissertation-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Venues](https://img.shields.io/badge/MICCAI-2022%20%C2%B7%202023%20%C2%B7%202026-b31b1b.svg)](#the-four-works)
[![UC Santa Cruz](https://img.shields.io/badge/UC%20Santa%20Cruz-2026-FDC700.svg)](https://engineering.ucsc.edu/)

Four papers, one throughline: **how do you build dermatological AI that is accurate, fair, and data-efficient when clean, demographically balanced labels barely exist?** This dissertation answers it as a single arc — *when there are no labels, learn from the temporal structure of healing* (**HealNet**); *when there is no temporal structure, learn from a frozen diffusion backbone* (**FEDD**); *when the data themselves are too few and too imbalanced, generate them* with sensitive-attribute control (**cgDDI**); *and to make measurements clinically real, recover metric 3D from a single image* (**DermDepth**).

Every step targets where medical AI fails first — rare diseases, under-imaged skin tones, and clinics without specialist hardware. One pattern recurs across all four works: *small, clean datasets; frozen large backbones with tiny trainable heads; and explicit, skin-tone-stratified fairness evaluation.* All synthetic data, checkpoints, annotations, code, and per-disease generative models are released openly.

---

## Committee

| Role | Member |
| --- | --- |
| **Chair & Advisor** | Prof. Narges Norouzi |
| Member | Prof. Marcella Gomez |
| Member | Prof. Leilani H. Gilpin |

---

## Defense

- 📄 **Slides (PDF):** https://drive.google.com/file/d/1LxmCbI_5ZpJpAr26gbgczajHU6kpctdI/view?usp=sharing
- 🎥 **Recording:** https://drive.google.com/file/d/1kIwDJ01-y-UNzm7bDlEmVW3gf-VpqPDR/view?usp=drive_link

---

## Abstract

Medical image analysis is constrained by a structural mismatch: clinical decision-making demands fine-grained understanding across diverse populations, body sites, and disease severities, yet expert annotations are scarce, demographic coverage is uneven, and rare presentations are nearly absent. This dissertation develops deep learning algorithms that compensate for that mismatch through four connected works in dermatology and wound care, domains where the limitations are most acute, and the downstream stakes for under-imaged populations are highest. We develop four methods spanning unsupervised, self-supervised, and supervised strategies, with both non-parametric and parametric generative paradigms. When there are no labels, we learn unsupervised from temporal structure (HealNet); when there is no temporal structure, we learn supervised from a frozen diffusion backbone (FEDD); when the data themselves are too few and too imbalanced, we generate them with sensitive-attribute control (cgDDI); and to close the loop into 3D space, we develop metric scale dermatology foundation models with non-parametric synthetic and real data (DermDepth).

**HealNet** introduces a self-supervised framework for acute wound heal-stage classification, learning biologically meaningful temporal embeddings without any human-provided labels and reaching 97.7% pre-text and 90.6% downstream stage-classification accuracy on a small longitudinal cohort. **FEDD** generalizes representation learning to the single-image clinical setting by re-tasking a frozen denoising-diffusion backbone as the encoder, achieving state-of-the-art segmentation (IoU lift 0.06–0.18) and a 14-point gain in malignancy classification accuracy on the biopsy-confirmed Diverse Dermatology Images (DDI) benchmark while using only 5–20% of the available labels, and contributes the first explicit skin-tone-stratified fairness evaluation of the work. **cgDDI** repurposes that diffusion backbone as a controllable generator, combining latent-diffusion in-painting, non-parametric lesion mapping, and textual-inversion plus LoRA prior-preservation to grow a 656-image dataset by over 400×, balancing the full Fitzpatrick spectrum and lifting DDI malignancy classification to state-of-the-art 90.9% accuracy with EOM fairness 86.6 (up from 69.6) and a +13.9% cross-dataset gain on Fitzpatrick17k. **DermDepth** closes the loop from 2D to 3D, presenting the first single-view metric-scale 3D reconstruction model for dermatology together with **D-Synth**, the first synthetic dermoscopic dataset with pixel-perfect depth, normals, and camera intrinsics; a 2.1M-parameter scale-and-normal head on top of a frozen MoGe-2 backbone corrects metric scale error from over 16× to under 1.1× on real dermoscopic data, reduces skin-tone scale disparity from 10.90 to 1.02, and validates 3D lesion width, area, and volume estimation across SKINL2, WoundsDB, and DDI against the published clinical literature.

Across the work, a pattern recurs: small, clean datasets; frozen large backbones with trainable heads; and explicit, skin-tone-stratified fairness evaluation. We believe this framework generalizes beyond dermatology to any data-constrained medical imaging domain. All synthetic data, fine-tuned checkpoints, annotation work, code, and per-disease generative models are released openly to support reproducibility and continued fairness research.

---

## The Four Works

Each method chapter is a peer-reviewed contribution that releases its code, checkpoints, and data in a dedicated repository.

| Work | Chapter | Venue | Code / Paper |
| --- | --- | --- | --- |
| **HealNet** | 3 | MICCAI MLMI 2022 | [📄 Paper](https://link.springer.com/chapter/10.1007/978-3-031-21014-3_46) |
| **FEDD** | 4 | MICCAI 2023 | [hectorcarrion/FEDD](https://github.com/hectorcarrion/FEDD) |
| **cgDDI** | 5 | MICCAI 2026 | [hectorcarrion/ControllableGenDDI](https://github.com/hectorcarrion/ControllableGenDDI) |
| **DermDepth** | 6 | MICCAI 2026 | [hectorcarrion/dermdepth](https://github.com/hectorcarrion/dermdepth) |

- **HealNet** — self-supervised heal-stage learning from the temporal structure of wound healing, with *no human labels required*.
- **FEDD** — a frozen denoising-diffusion backbone re-tasked as a single-image encoder for label-efficient, fairness-evaluated skin-lesion analysis.
- **cgDDI** — that same backbone turned into a controllable generator, growing DDI 400×+ with full Fitzpatrick balance and single-sample rare-disease coverage.
- **DermDepth** — the first single-view metric-scale 3D reconstruction model for dermatology, together with the pixel-perfect synthetic **D-Synth** dataset.

---

## Chapters

1. Introduction
2. Background and Related Work
3. Representation Learning, Heal-Stages — *HealNet*
4. Representation Learning, Fairness and Efficiency — *FEDD*
5. Controllable Generation, Fairness and Data Efficiency — *cgDDI*
6. Monocular Metric 3D Reconstruction for Dermatology — *DermDepth*
7. Conclusion and Future Work

---

## Repository layout

```
final_thesis.tex        Main LaTeX document
final_thesis.bib        Merged bibliography
ucthesis.cls            UCSC thesis class (unmodified, LPPL)
uct{10,11,12}.clo       UCSC thesis font-size options (unmodified, LPPL)
Makefile                Build rules
HealNet/ FEDD/ cgDDI/ DermDepth/   Per-chapter figures
```

---

## Build

**With `make`** (requires a TeX distribution such as TeX Live or MacTeX):

```bash
make          # pdflatex → bibtex → pdflatex → pdflatex
make clean    # remove LaTeX intermediate files
```

**With Overleaf:** upload this repository (or a zip of it) as a new project and set the main document to `final_thesis.tex`.

---

## Citation

```bibtex
@phdthesis{carrion2026deep,
  author = {Carri\'on, H\'ector},
  title  = {Deep Learning Algorithms for Medical Image Representation Learning and Understanding},
  school = {University of California, Santa Cruz},
  year   = {2026}
}
```

---

## License

The written dissertation (LaTeX source and author-created figures in this repository) is released under [**CC BY 4.0**](https://creativecommons.org/licenses/by/4.0/) — share and adapt with attribution. The bundled UCSC thesis class is redistributed under the LaTeX Project Public License; code, checkpoints, and datasets for each work live in their linked repositories under their own licenses; and figure imagery derives from public research datasets under those datasets' terms. See [`NOTICE`](NOTICE) for the full scope.
