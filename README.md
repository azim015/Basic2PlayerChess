# Basic2PlayerChess
The project was created as a hobby in 2019. It is a simple two-player chess game in C#. 
It just need to be loaded into C# IDE and run!


```mermaid
flowchart LR
  subgraph INPUTS[Input Data]
    I1[Microscopy<br/>(BF/DF/±Fluor)]
    I2[SERS Spectral Maps<br/>(points or (x,y,λ))]
    I3[Open-Source Microscopy<br/>+ Annotations]
    I4[Synthetic Data<br/>(VAE/GAN/Physics)]
    I5[Calibration & Metadata<br/>(PSF, flat-field, beads, site tags)]
  end

  subgraph PRE[Preprocessing & Alignment]
    P1[QC + Flat-field/Color Norm]
    P2[Cosmic-ray Removal<br/>Baseline/Norm (SERS)]
    P3[Registration SERS↔Image<br/>+ Confidence (TRE/MI)]
    P4[Feature Maps: Gradients, OD,<br/>Texture, SR/Deconv (+uncertainty)]
  end

  subgraph SEG[Segmentation (Transfer Learning)]
    S1[U-Net / UNet++ / HRNet<br/>(Original + SR branches)]
    S2[Boundary / CRF Refinement]
    S3[Metrics: IoU, Dice, Boundary-F]
  end

  subgraph FUSE[Multimodal Fusion & Multi-Task]
    F1[Cross-Attention (Perceiver/Transformer)<br/>Image tokens ↔ SERS tokens]
    F2[Heads: Composition (MDN),<br/>PSD (&lt;200nm), Shape, Transparency]
    F3[Intensity-Correction Head<br/>(per-pixel gain/offset)]
    F4[Uncertainty/Calibration<br/>(Deep Ensembles, ECE)]
  end

  subgraph LOOP[Robustness Loop]
    L1[SSL Pretrain (Microscopy/SERS)]
    L2[Active Learning<br/>(uncertainty + diversity)]
    L3[Domain Adaptation / TTA<br/>(CORAL / MMD / BN)]
  end

  I1 --> P1 --> P4 --> S1
  I2 --> P2 --> P3 --> F1
  I3 --> S1
  I4 --> P4 --> S1
  I5 --> P1
  I5 --> F3
  S1 --> S2 --> S3 --> F1
  F1 --> F2 --> F4
  F3 --> F4
  L1 --> S1
  L2 --> I1
  L3 --> S1
