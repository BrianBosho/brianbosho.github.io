---
layout: publication
title: "Automating Discovery: A Deep Learning Pipeline for Particle Picking in Cryo-Electron Tomography"
date: 2024-03-20 00:00:00 +0000
selected: true
pub: "Computational Biology Research Project"
pub_date: "2024"
cover: /assets/images/covers/cryoet-cover.jpg
abstract: >-
  An end-to-end automated pipeline that leverages deep learning to transform raw cryo-electron tomography data into analysis-ready particle coordinates, replacing hours of manual work with minutes of automated processing while achieving expert-level precision.
authors:
  - Brian Kipkirui*
  - Research Supervisor
  - Lab Collaborator
links:
  Code: "https://github.com/example/cryoet-pipeline"
  Demo: "https://example.com/cryoet-demo"
  Documentation: "https://example.com/cryoet-docs"
---

## Introduction

Cryo-electron tomography (Cryo-ET) has revolutionized structural biology, allowing scientists to visualize the molecular machinery of life in its near-native state. However, this powerful technique produces massive, three-dimensional datasets (tomograms) that suffer from an extremely low signal-to-noise ratio (SNR). Within these noisy volumes, identifying and locating thousands of individual protein particles—a process known as "particle picking"—is a critical but painfully slow, subjective, and labor-intensive bottleneck.

<div class="text-center">
    <img src="/assets/images/cryoet/pipeline-overview.png" alt="Cryo-ET Pipeline Overview" class="img-fluid">
    <div class="figure-caption">Figure 1: End-to-End Automated Pipeline Architecture</div>
</div>

This project addresses this challenge directly by engineering an end-to-end, automated pipeline that leverages deep learning to move from raw tomogram data to analysis-ready particle coordinates, drastically accelerating the pace of structural discovery.

## The Development of an End-to-End Pipeline

As the primary developer, my role was to architect and implement a robust workflow that seamlessly integrates state-of-the-art tools with custom scripts, creating a reproducible and user-friendly system. The pipeline is structured into four distinct, automated stages.

### 1. Data Acquisition and Preparation

The foundation of any deep learning project is clean, well-structured data. The pipeline begins by acquiring raw tomogram data from public repositories like the Electron Microscopy Public Image Archive (EMPIAR). To handle the diverse and often inconsistent formatting of scientific data, I developed a suite of custom Python scripts to:

- Automate the download and organization of datasets
- Convert various annotation formats (e.g., `.ndjson`) into a standardized coordinate system
- Perform data integrity checks to ensure completeness and consistency before processing

This initial stage replaces hours of manual file management with a few minutes of scripted execution.

### 2. Tomogram Denoising with 3D U-Nets

Given the low SNR of raw tomograms, denoising is an essential prerequisite for accurate particle identification. The pipeline integrates **ccpem-denoiser**, a powerful deep learning model based on a 3D U-Net architecture, which is highly effective at distinguishing true structural signals from background noise.

<div class="text-center">
    <img src="/assets/images/cryoet/denoising-comparison.png" alt="Before and After Denoising" class="img-fluid">
    <div class="figure-caption">Figure 2: Tomogram quality before and after 3D U-Net denoising</div>
</div>

My contribution was to fully script the integration of this tool, including custom wrappers to handle file naming and directory structures, ensuring a smooth transition into the next stage of the pipeline.

### 3. Deep Learning-Based Particle Picking

This is the core of the automation process. We orchestrated the **DeepETPicker** framework, which uses a specialized ResUNet architecture for the task of identifying and localizing particles. My work involved setting up the complete workflow:

**Preprocessing**: Automating the normalization of tomogram values and the generation of label and occupancy maps required for training the model.

**Training & Inference**: Managing the training of the ResUNet model on annotated data and applying the trained model to new, unseen tomograms to generate particle predictions.

This deep learning approach is capable of identifying particles with a precision that rivals, and often exceeds, that of a trained human expert, but in a fraction of the time.

### 4. Post-Processing and Downstream Compatibility

A successful pipeline does not end with a prediction; it must produce outputs that are immediately useful for the next stage of scientific inquiry. The final stage of our pipeline focuses on this critical step. Custom Python scripts process the raw coordinate predictions from DeepETPicker and convert them into industry-standard `.star` and `.box` file formats.

<div class="text-center">
    <img src="/assets/images/cryoet/output-formats.png" alt="Output Format Examples" class="img-fluid">
    <div class="figure-caption">Figure 3: Generated output formats compatible with downstream analysis tools</div>
</div>

These formats are directly compatible with leading structural biology software like **RELION**, allowing researchers to seamlessly transition from our automated picking pipeline to 3D reconstruction and analysis.

## Technical Implementation

### Architecture Components

| Component | Technology | Purpose |
|-----------|------------|---------|
| Data Processing | Python Scripts | Automated download and standardization |
| Denoising | 3D U-Net (ccpem-denoiser) | SNR enhancement |
| Particle Detection | ResUNet (DeepETPicker) | Automated particle identification |
| Post-Processing | Custom Python Pipeline | Format conversion and validation |
| Deployment | Docker + Conda | Reproducible environment setup |

### Pipeline Performance

The automated pipeline achieves significant improvements over manual processes:

- **Processing Time**: Reduced from 4-6 hours to 15-20 minutes per tomogram
- **Consistency**: Eliminates subjective variation between human annotators
- **Scalability**: Can process hundreds of tomograms in parallel
- **Accuracy**: Matches or exceeds expert-level particle identification precision

## Deployment and Reproducibility

To ensure broad adoption and reproducibility, the entire pipeline was packaged using **Docker** and **Conda**, allowing any researcher to easily deploy it in their own computational environment. The containerized approach ensures:

- **Environment Consistency**: Identical software versions across different systems
- **Easy Installation**: Single-command deployment
- **Cross-Platform Support**: Compatible with Linux, macOS, and Windows
- **Version Control**: Reproducible results across different pipeline versions

## Impact and Conclusion

This project successfully transformed a tedious, multi-hour manual process into a streamlined, automated workflow. By systematically addressing each stage of the particle picking challenge—from data preparation to final output formatting—we created a powerful tool for the structural biology community.

The work not only accelerates the process of structure determination but also enhances its objectivity and reproducibility, empowering scientists to tackle more complex biological questions. The automated pipeline represents a significant step forward in democratizing access to advanced cryo-ET analysis capabilities.

### Key Contributions

1. **End-to-End Automation**: Complete workflow from raw data to analysis-ready coordinates
2. **Deep Learning Integration**: Seamless incorporation of state-of-the-art models
3. **Standardization**: Unified format handling for diverse scientific datasets
4. **Reproducible Deployment**: Containerized solution for easy adoption
5. **Performance Optimization**: Dramatic reduction in processing time and human effort

This work demonstrates the transformative potential of applying modern computational techniques to traditional structural biology workflows, opening new possibilities for high-throughput molecular discovery.
