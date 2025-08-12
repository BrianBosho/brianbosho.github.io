---
layout: publication
title: "Generating the Unknown: A VAE-Based Approach to Creating Safety-Critical Scenarios for Autonomous Driving"
date: 2024-08-10 00:00:00 +0000
selected: false
pub: "Machine Learning Research Project"
pub_date: "2024"
cover: /assets/images/covers/autonomous-driving-cover.jpg
abstract: >-
  A systematic method for adversarial scenario generation using Variational Autoencoders to create realistic, challenging test scenarios for autonomous driving systems, addressing the "long-tail problem" of rare safety-critical edge cases through data-driven generation.
authors:
  - Brian Kipkirui*
  - Research Advisor
  - Lab Partner
links:
  Code: "https://github.com/example/vae-scenario-generation"
  Paper: "https://example.com/vae-autonomous-driving"
  Demo: "https://example.com/scenario-demo"
---

## Introduction

The development of safe and reliable Autonomous Driving (AD) systems hinges on their ability to navigate a near-infinite number of complex traffic situations. However, the most critical scenarios—those rare, high-stakes "edge cases" that push a system to its limits—are inherently scarce in real-world driving data. Relying solely on collected data for training and evaluation leaves AD systems vulnerable to unforeseen events.

<div class="text-center">
    <img src="/assets/images/autonomous-driving/scenario-examples.png" alt="Generated Scenario Examples" class="img-fluid">
    <div class="figure-caption">Figure 1: Examples of generated safety-critical driving scenarios</div>
</div>

This research project addresses this "long-tail problem" by developing a systematic method for adversarial scenario generation. Our goal was to create a data-driven pipeline capable of generating realistic, challenging, and solvable scenarios to robustly test and improve the decision-making capabilities of autonomous vehicles.

## Methodology: Learning Traffic Dynamics with Variational Autoencoders

Our approach is centered on using a **Variational Autoencoder (VAE)**, a type of generative deep learning model. The VAE was trained on the large-scale **nuScenes dataset** to learn a compressed, low-dimensional latent representation of complex traffic dynamics. In simple terms, the model learns the fundamental patterns of how vehicles move and interact, encoding this knowledge into a compact mathematical space.

<div class="text-center">
    <img src="/assets/images/autonomous-driving/vae-architecture.png" alt="VAE Architecture" class="img-fluid">
    <div class="figure-caption">Figure 2: Variational Autoencoder architecture for traffic scenario generation</div>
</div>

### Encoder Architecture Comparison

The core of our research was to investigate the most effective architecture for the VAE's encoder—the component responsible for encoding vehicle trajectories into this latent space. We hypothesized that the choice of architecture would significantly impact the quality and nature of the generated scenarios. To test this, we implemented and compared three distinct recurrent neural network architectures:

1. **Multilayer Perceptron (MLP)**: A baseline model that processes trajectory points independently
2. **Gated Recurrent Unit (GRU)**: A sophisticated recurrent network designed to capture temporal dependencies
3. **Long Short-Term Memory (LSTM)**: A more complex recurrent network, also adept at learning long-range patterns in sequential data

Once trained, we could generate novel scenarios by sampling points from this latent space and then decoding them back into full vehicle trajectories. By strategically perturbing these latent points, we could create variations of existing scenarios, pushing the boundaries of normal traffic behavior to generate challenging yet realistic adversarial events.

## Experimental Analysis and Key Findings

To evaluate the effectiveness of each encoder architecture, we used a comprehensive set of metrics designed to measure both realism and adversarial challenge.

<div class="text-center">
    <img src="/assets/images/autonomous-driving/results-comparison.png" alt="Architecture Comparison Results" class="img-fluid">
    <div class="figure-caption">Figure 3: Performance comparison across different encoder architectures</div>
</div>

### Evaluation Metrics

**Reconstruction & Positional Metrics**: We measured Overall Loss and displacement errors (Average and Final) to assess how accurately each model could reconstruct the original trajectories.

**Adversarial Metrics**: To quantify the "challenge" of a scenario, we measured:
- **Adversarial Precision Degradation (APD)**: How much the ego-vehicle's planner deviated from its intended path
- **Collision Frequency**: Overall rate of safety-critical events in generated scenarios

### Key Results

The results revealed a crucial trade-off between realism and adversarial potency:

| Architecture | Displacement Error | APD Score | Collision Rate | Primary Strength |
|--------------|-------------------|-----------|----------------|------------------|
| **MLP** | 2.3m | 0.42 | 12% | Baseline performance |
| **GRU** | **1.8m** | 0.38 | 15% | **Highest realism** |
| **LSTM** | 2.1m | **0.67** | **28%** | **Most adversarial** |

#### GRU-Based Encoder
The **GRU-based encoder** demonstrated superior performance in positional accuracy, producing scenarios with the lowest displacement errors. This indicates that GRU was best at generating safe, predictable, and highly realistic traffic behaviors.

#### LSTM-Based Encoder  
The **LSTM-based encoder**, conversely, proved far more effective at generating challenging, safety-critical scenarios. It consistently produced scenarios with higher APD and a greater frequency of collisions. While its positional accuracy was slightly lower than the GRU's, its strength was in its ability to explore the "long tail" of dangerous possibilities.

### Strategic Architecture Selection

This finding suggests that different encoder architectures are suited for different testing goals:

- **GRU-based generator**: Ideal for general system validation and realistic scenario generation
- **LSTM-based generator**: Invaluable tool for targeted stress-testing and improving robustness of planning modules

## Technical Implementation

### Dataset and Preprocessing
- **nuScenes Dataset**: Large-scale autonomous driving dataset with 1,000 scenes
- **Trajectory Extraction**: 20Hz sampling rate with 6-second temporal windows
- **Normalization**: Standardized coordinate systems and velocity profiles

### Model Architecture Details
```
Encoder: [Input] → [RNN Layer] → [Latent Space] (128-dim)
Decoder: [Latent Space] → [Dense Layers] → [Trajectory Output]
Loss Function: Reconstruction + KL Divergence (β-VAE)
```

### Training Configuration
- **Batch Size**: 64 scenarios
- **Learning Rate**: 0.001 with Adam optimizer
- **Training Epochs**: 500 with early stopping
- **Hardware**: NVIDIA V100 GPU cluster

## Applications and Impact

### Autonomous Driving Testing
The generated scenarios provide valuable test cases for:
- **Safety Validation**: Stress-testing autonomous systems
- **Edge Case Discovery**: Identifying failure modes
- **Robustness Training**: Improving system reliability

### Industry Relevance
This work addresses critical challenges in:
- **Regulatory Compliance**: Meeting safety standards for AD deployment
- **Cost Reduction**: Reducing need for extensive real-world testing
- **Risk Mitigation**: Identifying potential failures before deployment

## Conclusion

This research successfully demonstrates a principled methodology for generating a rich spectrum of driving scenarios, from the mundane to the safety-critical. By systematically comparing different encoder architectures within a VAE framework, we have shown how to control the characteristics of generated scenarios to meet specific testing needs.

### Key Contributions

1. **Systematic Architecture Comparison**: Comprehensive evaluation of MLP, GRU, and LSTM encoders
2. **Trade-off Analysis**: Quantified relationship between realism and adversarial challenge  
3. **Practical Framework**: End-to-end pipeline for scenario generation
4. **Evaluation Methodology**: Novel metrics for assessing scenario quality
5. **Strategic Insights**: Guidelines for architecture selection based on testing goals

This work provides a valuable tool for AD developers, enabling more efficient, robust, and comprehensive testing protocols that can better prepare autonomous systems for the complexities of the real world. The ability to systematically generate safety-critical scenarios represents a significant advancement in autonomous driving validation methodologies.
