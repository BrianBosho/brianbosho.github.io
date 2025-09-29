---
layout: project
title: "FedProp: Federated Graph Neural Networks with Feature Propagation"
permalink: /projects/fedprop/
date: 2025-01-15

image: "assets/images/fedprop/fedprop-conceptual.jpg"
context: "Research Project, Carnegie Mellon University Africa"
summary: "Developed FedProp, a federated learning method for graph neural networks that reconstructs missing neighbor features through local feature propagation."

subtitle: "Communication-Efficient Federated Learning on Graphs"
code_url: "https://github.com/brianbosho/fedprop"
role: "Lead Author & Developer"
technologies:
  - Python
  - PyTorch Geometric
  - Federated Learning
  - Graph Neural Networks
  - Cora / Citeseer / PubMed
  - OGBN
selected: true
---

## At a Glance
- Designed **FedProp**, a new algorithm for federated GNNs  
- Reconstructs missing cross-client features without communication  
- Achieved near-centralized accuracy on citation and OGBN datasets  
- Provided theoretical analysis via Dirichlet energy minimization  

---

## The Challenge
In federated learning on graphs, each client only has part of the graph.  
This leads to missing features from cross-client edges, which limits the performance of graph neural networks.  
Existing methods either require extra communication (hurting privacy and efficiency) or lose accuracy.  

---

## Contributions
I developed **FedProp**, a method that:  

- Uses **local feature propagation** to approximate missing neighbor features.  
- Provides **theoretical guarantees**, showing convergence through Dirichlet energy minimization.  
- Requires **no additional inter-client communication**.  
- Evaluated performance on **Cora, Citeseer, PubMed, and OGBN datasets**.  

---

## Results
- Reached up to **97–99% of centralized accuracy**.  
- Improved performance by **~17%** over baseline federated GNNs.  
- Mathematically proved that the propagated features converge to the global optimum under mild assumptions.  

---

## Impact
FedProp demonstrates that it’s possible to train effective GNNs in federated settings **without privacy trade-offs or heavy communication costs**.  
This opens the door for applications in **healthcare, finance, and mobility**, where graph data is distributed and sensitive.  

---

## Resources
- [GitHub Repository](https://github.com/brianbosho/fedprop)  
- [Paper Draft / Preprint](link-if-available)  
