---
layout: project
title: "Safety-Critical Autonomous Driving Scenario Generation"
permalink: /projects/safety-critical/

# For the project list page (project_item.html)
image: "assets/images/autonomous-driving/strive.jpeg"
context: "Course Project: Principles and Engineering Applications of AI"
summary: "Leveraged Variational Autoencoders (VAEs) to artificially generate a rich dataset of realistic and challenging scenarios to rigorously test and improve AV decision-making."

# For the detailed project page (project.html)
subtitle: "Improving AV Safety by Generating Challenging Scenarios with Variational Autoencoders"
code_url: "https://github.com/brianbosho/safety-critical-generation"
role: "Co-Researcher & Developer"
technologies:
  - Python
  - PyTorch
  - VAEs
  - LSTMs
  - GRUs
contributions:
  - VAE model design
  - Trajectory encoder implementation (LSTM vs GRU)
  - Result analysis & benchmarking
  - Literature review
date: 2024-08-01
selected: false
---

### The Challenge: The Scarcity of "Hard Cases" for Self-Driving Cars
Autonomous vehicles (AVs) learn from data, but real-world driving data is overwhelmingly mundane. Safety-critical scenarios are extremely rare, making it difficult to robustly train and validate AV planners. Our goal was to artificially generate a rich dataset of realistic, challenging scenarios to rigorously test AV decision-making.

A diagram illustrating how a Variational Autoencoder (VAE) can learn from existing scenarios to generate new, more challenging ones.

### My Solution: Enhancing Trajectory Encoding in a VAE Framework
Building on the STRIVE framework, our work focused on a critical component: the trajectory encoder. My hypothesis was that a more powerful sequence-to-sequence architecture could capture temporal dynamics more effectively. My contributions included:

*   **Implementing a Seq2Seq Encoder**: I implemented an LSTM-based sequence-to-sequence encoder within the VAE architecture.
*   **Benchmarking Architectures**: I systematically compared the performance of our LSTM encoder against baseline GRU and MLP encoders.
*   **Analyzing Scenario Quality**: We evaluated the generated scenarios based on both realism and challenge.

### Impact
Our experiments demonstrated that using a more sophisticated sequential encoder (like an LSTM) leads to a higher-quality latent space. This allows the VAE to generate scenarios that more effectively probe the weaknesses of an AV's planning module, ultimately helping to build safer and more trustworthy autonomous vehicles.

