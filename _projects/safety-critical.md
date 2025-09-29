---
layout: project
title: "Adversarial Scenario Generation for Autonomous Driving"
permalink: /projects/scenario-generation/
date: 2024-04-20

image: "assets/images/autonomous-driving/strive.jpeg"
context: "Course Project, Carnegie Mellon University Africa"
summary: "Explored adversarial generation of rare driving scenarios using sequence models and latent space perturbations to improve robustness of autonomous planners."

subtitle: "Generating Safety-Critical Driving Scenarios"
code_url: "https://github.com/brianbosho/adversarial-scenarios"
role: "Team Member (Model Design & Experiments)"
technologies:
  - Python
  - PyTorch
  - LSTM / GRU
  - Variational Autoencoders (VAE)
  - nuScenes Dataset
selected: true
---

## At a Glance
- Built a pipeline to **generate rare, safety-critical driving scenarios**  
- Encoded traffic scenes into a **latent space** using VAEs  
- Applied **adversarial perturbations** to generate challenging variations  
- Tested different sequence encoders (MLP, GRU, LSTM) on nuScenes data  

---

## The Challenge
Most autonomous driving datasets capture regular, safe situations.  
But autonomous planners also need to handle **rare, dangerous events** (e.g. sudden braking, collisions, near-misses).  
The goal was to generate such scenarios automatically for testing and training.  

---

## What We Did
Our approach used a **variational autoencoder (VAE)** framework:  

- **Encoding**: represented past and future agent trajectories in a latent space.  
- **Traffic modeling**: incorporated agent interactions using sequence models.  
- **Adversarial perturbations**: modified latent vectors to produce new, harder scenarios.  
- **Evaluation**: compared encoder types (MLP, GRU, LSTM) on reconstruction quality and scenario realism.  

---

## Results
- **LSTMs** achieved the lowest overall loss, capturing sequential patterns well.  
- **GRUs** performed better on positional accuracy and produced fewer collisions.  
- The generated scenarios were diverse, including more challenging corner cases than the original dataset.  

---

## Impact
This project showed how adversarial generation can enrich datasets with **rare but important driving situations**, making autonomous systems more robust and safer to deploy.  

---

## Resources
- [GitHub Repository](https://github.com/brianbosho/adversarial-scenarios)  
- [Slides / Report](link-if-available)  
