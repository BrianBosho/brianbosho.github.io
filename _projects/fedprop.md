---
layout: project
title: "FedProp: Communication-Efficient Federated GNNs"
permalink: /projects/fedprop/

# For the project list page (project_item.html)
image: "assets/images/fedprop/cross-client edges.png"
context: "Graduate Research at Carnegie Mellon University Africa"
summary: "Developed a novel federated GNN framework that achieves near-centralized performance with zero extra inter-client communication, solving a key challenge in privacy-preserving graph learning."

# For the detailed project page (project.html)
subtitle: "Federated Graph Neural Networks with Feature Propagation"
code_url: "https://github.com/brianbosho/fedprop"
role: "Lead Author & Developer"
technologies:
  - Python
  - PyTorch
  - Federated Learning
date: 2025-03-20
selected: true
---

Graph Neural Networks

Cora/Citeseer/PubMed
contributions:

Novel problem formulation

Theoretical convergence guarantees

State-of-the-art performance evaluation

Zero communication overhead design

The Challenge: Training GNNs Without Sharing Private Data
Graph Neural Networks (GNNs) are incredibly powerful for learning from relational data, but they have a fundamental requirement: to process a node, they must access its neighbors. In a federated setting, where data is decentralized across many private devices (like phones or hospitals), a node's neighbors often reside on other devices. Accessing them would require direct communication, which is a major privacy risk and a communication bottleneck. How can we train a high-performance GNN if it can't see all its neighbors?

A diagram showing how FedProp locally reconstructs features, avoiding the privacy and communication costs of traditional methods.

My Solution: FedProp - Reconstructing Features Locally
I developed FedProp, a model-agnostic federated GNN framework that recasts this obstacle as a missing-feature problem. Instead of trying to communicate with other clients, FedProp uses a lightweight, iterative process to locally reconstruct the features of the missing neighbors.

My key contributions were:

Novel Formulation: I reframed the cross-client edge problem as a feature reconstruction task that can be solved locally on each device.

Theoretical Guarantees: I provided a theoretical justification for this feature propagation process, proving its convergence and linking it to Dirichlet energy minimization.

Zero Communication Overhead: The entire feature reconstruction process is local. This means FedProp adds zero extra communication rounds between clients compared to standard federated averaging, making it highly efficient and private.

Impact
FedProp provides a practical and effective solution for training GNNs in privacy-sensitive, federated environments. On benchmark datasets like Cora, it achieves 99.6% of the performance of a centralized model that has full access to the data, significantly outperforming standard federated baselines. This work enables the application of powerful graph learning techniques in domains like healthcare and finance, where data privacy is paramount.