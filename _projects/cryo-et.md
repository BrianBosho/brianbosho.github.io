layout: project
title: "Automated Cryo-ET Particle Picking Pipeline"
permalink: /project/cryo-et/

--- For the project list page (project_item.html) ---
image: "/assets/img/projects/cryoet_thumbnail.png"
context: "Research Internship at Xulab, Carnegie Mellon University"
summary: "Engineered an end-to-end automated pipeline for Cryo-ET particle picking, addressing critical challenges of low SNR and intensive manual processing in computational biology."

--- For the detailed project page (project.html) ---
subtitle: "Accelerating Discovery in Computational Biology with a Deep Learning Workflow"
code_url: "https://www.google.com/search?q=https://github.com/brianbosho/cryoet-pipeline"
role: "Primary Developer"
technologies:

Python

PyTorch

3D U-Net

EMPIAR

ccpem-denoiser

DeepETPicker
contributions:

End-to-end pipeline architecture

Automated data acquisition scripts

Data wrangling & format conversion

Full training & inference workflow management

The Challenge: A Critical Bottleneck in Structural Biology
Cryo-electron tomography (Cryo-ET) allows scientists to visualize the molecular machinery of life in 3D. However, the raw images are extremely noisy, making the manual process of identifying individual protein particles a major bottleneck that slows down scientific discovery. My goal was to engineer a robust, automated pipeline to solve this problem.

A high-level overview of the automated pipeline, from raw data to final particle coordinates.

My Solution: Orchestrating a State-of-the-Art Deep Learning Workflow
As the primary developer, I designed and built an end-to-end system that integrated several powerful, specialized tools. My key contributions included:

Automated Data Acquisition: I wrote custom Python scripts to automatically download and organize tomograms from public archives like the EMPIAR database.

Intelligent Denoising: The pipeline integrates ccpem-denoiser, a 3D U-Net model, to dramatically reduce noise in the raw tomograms.

Deep Learning-Based Particle Picking: At the core is DeepETPicker. I orchestrated the entire workflow around it, from preprocessing to running inference.

Seamless Data Conversion: I developed numerous utility scripts to handle data integrity and automatically convert annotation formats to be compatible with downstream tools like RELION.

Impact
This project transformed a complex, manual process into a streamlined, reproducible, and automated system. My work directly contributes to accelerating the pace of discovery in structural biology, allowing researchers to move from raw data to meaningful insights more efficiently.