---
layout: project
title: "Automated Cryo-ET Particle Picking Pipeline"
permalink: /projects/cryo-et/
date: 2024-10-27

image: "assets/images/cryoet/cryoet_icon.jpeg"
context: "Research Internship at XuLab, Carnegie Mellon University"
summary: "Built an automated pipeline for Cryo-ET particle picking, reducing the manual work needed to process noisy 3D tomograms."

subtitle: "Automating Noisy 3D Biological Data Processing"
code_url: "https://github.com/brianbosho/cryoet-pipeline"
role: "Primary Developer"
technologies:
  - Python
  - PyTorch
  - 3D U-Net
  - EMPIAR
  - CCP-EM Denoiser
  - DeepETPicker
selected: true
---

## At a Glance
- Processed thousands of tomograms from the EMPIAR archive  
- Integrated DeepETPicker for particle picking in 3D volumes  
- Used 3D U-Net models for denoising and preprocessing  
- Automated data wrangling and format conversion for downstream tools  

---

## The Challenge
Cryo-electron tomography (Cryo-ET) is a powerful imaging method for looking at biological structures in 3D.  
The raw data, however, is very noisy and requires a lot of manual work to identify particles like ribosomes or membrane structures.  
This slows down the research process and makes large-scale studies difficult.  

---

## What I Built
During my internship at XuLab, I put together an end-to-end pipeline that automates much of this workflow:  

- **Data acquisition**: scripts to fetch and organize tomograms from EMPIAR.  
- **Denoising**: used the CCP-EM denoiser (a 3D U-Net) to improve image quality.  
- **Particle picking**: set up DeepETPicker as the main particle detection tool.  
- **Data conversion**: wrote utilities to convert outputs into formats usable by other Cryo-ET tools like RELION.  

---

## Impact
The pipeline makes it possible to process datasets more quickly and with less manual effort.  
Instead of spending days picking particles by hand, researchers can now run automated workflows and focus on the downstream biology.  

---

## Looking Ahead
Future improvements could include semi-supervised methods to cut down on labeled data, better denoisers (e.g. diffusion-based), and expanding the workflow to cover tasks like segmentation and classification.  

---

## Resources
- [GitHub Repository](https://github.com/brianbosho/cryoet-pipeline)  
- [Notes / Report](link-if-available)  
