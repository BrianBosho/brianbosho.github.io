---
layout: project
title: "FedProp: Federated GNN Training with Spectral Feature Propagation"
permalink: /projects/fedprop/

# For the project list page (project_item.html)
image: "assets/images/fedprop/fedprop-conceptual.jpg"
context: "Research Project"
summary: "A model-agnostic framework for training GNNs in a federated setting by recasting cross-client edges as a missing-feature problem and solving it with spectral propagation."

# For the detailed project page (project.html)
abstract: >
  This document details FedProp, a model-agnostic framework for training Graph Neural Networks (GNNs) in a federated setting. We address the fundamental challenge of "cross-client edges" by recasting it as a missing-feature problem. The proposed solution, spectral feature propagation, reconstructs the necessary 1-hop features locally via power iteration, eliminating the need for direct inter-client communication. This method comes with theoretical convergence and approximation guarantees and empirically achieves 99.6% of the performance of a centralized model on the Cora dataset without additional communication overhead or privacy risks.
---
## <i class="fas fa-bullseye mr-2"></i>Introduction: The Privacy Dilemma in Federated GNNs
Graph Neural Networks (GNNs) have become the standard for learning on relational data. However, training them in privacy-preserving, federated settings presents a fundamental conflict: the core GNN operation, message passing, requires access to a node's direct neighbors, but in a federated graph, these neighbors may reside on another client's device, making their data inaccessible due to privacy constraints. These cross-client edges create information gaps that severely degrade model performance.

Prior solutions introduce significant privacy risks or communication overhead. The central problem this project addresses is: How can we perform effective graph convolution across client boundaries without sharing sensitive graph structure or node features?

This work presents FedProp, a framework that solves this dilemma by recasting the communication problem as a local missing-feature problem. Our thesis is that we can forgo direct communication by using spectral feature propagation to reconstruct the required 1-hop features locally. This method is model-agnostic, supported by theoretical guarantees, and requires no additional learnable parameters.

## <i class="fas fa-sitemap mr-2"></i>Methodology & Design Rationale
The core innovation of FedProp is to replace direct, privacy-violating message passing with a local, data-driven approximation that is mathematically grounded in the spectral properties of the graph.

<figure class="figure w-100 text-center my-4">
<img src="https://www.google.com/search?q=https://placehold.co/800x400/28a745/ffffff%3Ftext%3DFedProp%2Bvs%2BStandard%2BMessage%2BPassing" class="figure-img img-fluid rounded shadow-sm" alt="FedProp vs Standard Message Passing">
<figcaption class="figure-caption text-center mt-2">Conceptual comparison: Standard message passing (left) is blocked by client boundaries. FedProp (right) locally reconstructs the necessary feature information before the GNN step.</figcaption>
</figure>

<h4>1. The Intuition: From Message Passing to Feature Propagation</h4>
A single layer of a GCN can be expressed as 
mathbfhatAXW, where 
mathbfhatA is the normalized adjacency matrix. In federation, we only have the local 
mathbfhatA_local. Our key insight is that the goal is not to reconstruct 
mathbfhatA, but to approximate the product 
mathbfhatAX. We reframe this as a feature reconstruction task: for each client, we want to find a feature matrix 
mathbftildeX such that 
mathbftildeX
approx
mathbfhatAX.

<h4>2. The Algorithm: Spectral Propagation via Power Iteration</h4>
We achieve this approximation using a fixed number of power iteration steps, a classical method for finding the dominant eigenvector of a matrix. By iteratively applying the local normalized adjacency matrix to the feature matrix (
mathbfX∗k+1=
mathbfhatA∗local
mathbfX_k), we diffuse the feature information across the local graph. This process effectively incorporates multi-hop neighborhood information into each node's feature vector, serving as a powerful proxy for the information that would have been gained from a single round of global message passing.

This pre-processing step "bakes in" a richer structural context into the node features before they are fed to the client's GNN model, significantly closing the information gap from missing cross-client edges.

<h4>3. Theoretical Guarantees</h4>
This is not merely a heuristic. The work includes mathematical proofs establishing convergence and approximation guarantees for the feature propagation process. This proves that the iterative method is stable and that the resulting features are a sound approximation of what would be achieved with full graph access, providing a strong theoretical foundation for the empirical results.

## <i class="fas fa-chart-line mr-2"></i>Evaluation & Results
FedProp was benchmarked on standard graph datasets (Cora, Citeseer, PubMed) against multiple state-of-the-art federated GNN methods. The experiments show that FedProp consistently outperforms methods that rely on generating synthetic data or sharing structural information.

On the Cora dataset, using a standard GCN backbone with K=3 propagation steps, FedProp achieved 80.8% accuracy, which is 99.6% of the performance of a centrally trained model.

<figure class="figure w-100 text-center my-4">
<img src="https://www.google.com/search?q=https://placehold.co/800x450/495057/ffffff%3Ftext%3DBar%2BChart:%2BFedProp%2Bvs%2BOther%2BMethods%2Bon%2BCora" class="figure-img img-fluid rounded shadow-sm" alt="Performance Comparison of Federated GNN Methods on Cora">
<figcaption class="figure-caption text-center mt-2">FedProp consistently outperforms other federated learning methods, closely approaching the performance of a centralized model without compromising privacy.</figcaption>
</figure>

## <i class="fas fa-code-branch mr-2"></i>Resources & Reproducibility
The source code and the full research paper are available for review and reproduction.

<ul>
<li><a href="#link-to-fedprop-repo" target="_blank"><strong><i class="fab fa-github mr-2"></i>View the Code on GitHub</strong></a></li>
<li><a href="#link-to-fedprop-paper.pdf" target="_blank"><strong><i class="fas fa-file-pdf mr-2"></i>Read the Full Paper</strong></a></li>
</ul>