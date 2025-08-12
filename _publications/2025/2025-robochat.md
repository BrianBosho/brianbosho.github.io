---
layout: publication
title: "RoboCHAT: Bridging the Automation Gap with LLM-Guided Robotic Execution"
date: 2024-05-15 00:00:00 +0000
selected: true
pub: "Senior Capstone Project"
pub_date: "2024"
cover: /assets/images/covers/robochat-cover.jpg
abstract: >-
  RoboCHAT introduces a sophisticated, two-layered architecture that leverages Large Language Models (LLMs) to create an intuitive, natural language interface for controlling complex robots, achieving 89% command resolution accuracy and making robotics more accessible to non-expert users.
authors:
  - Brian Kipkirui*
  - Team Member 1
  - Team Member 2
links:
  Demo: "https://example.com/robochat-demo"
  Code: "https://github.com/example/robochat"
  Report: "https://example.com/robochat-report"
---

## Introduction

Modern robotic platforms possess incredible mechanical capabilities, yet their adoption in dynamic service environments is often hindered by a significant "automation gap." The complexity of programming these systems places them beyond the reach of non-expert users, limiting their practical utility. To perform even simple tasks, a user typically requires deep knowledge of robotics frameworks like ROS and symbolic planners.

<div class="text-center">
    <img src="/assets/images/robochat/architecture.png" alt="RoboCHAT System Architecture" class="img-fluid">
    <div class="figure-caption">Figure 1: RoboCHAT Two-Layered Architecture Overview</div>
</div>

Our capstone project, **RoboCHAT**, confronts this challenge directly. It introduces a sophisticated, two-layered architecture that leverages the power of Large Language Models (LLMs) to create an intuitive, natural language interface for controlling complex robots, making them more adaptable, versatile, and accessible.

## System Architecture: A Two-Layered Approach

The RoboCHAT system is composed of two primary components that work in tandem: a powerful backend API (**RoboCRAM**) and an intelligent, user-facing chat interface (**RoboCHAT**).

### 1. RoboCRAM: The High-Level Robotics Backend

The foundation of our system is RoboCRAM, a backend API built with **FastAPI**. Its purpose is to abstract away the immense complexity of the underlying robotics framework. Instead of requiring a user to write low-level Lisp code or ROS commands, RoboCRAM exposes a set of high-level, human-understandable functions like `move_to()`, `pick_up()`, or `place()`. 

This API acts as the crucial bridge to **PyCRAM**, a robotic planning framework that enables a simulated PR2 robot to perform complex manipulation and perception tasks within the **BulletWorld** physics simulator.

### 2. RoboCHAT: The Natural Language Interface

The user interacts with RoboCHAT, a chat interface built with **Chainlit**. This layer is powered by **GPT-4o**, orchestrated through the **LangChain** framework. RoboCHAT's primary role is to interpret a user's intent from unstructured, natural language commands (e.g., "Can you please grab the red bowl from the counter?"). It then intelligently translates this request into the precise, structured API calls that RoboCRAM understands.

## Technical Innovation: Grounding LLMs with Retrieval-Augmented Generation (RAG)

A key challenge when using LLMs for robotic control is their potential to "hallucinate" or generate commands with incorrect parameters. An LLM has no inherent knowledge of the robot's immediate, real-world environment.

<div class="text-center">
    <img src="/assets/images/robochat/rag-pipeline.png" alt="RAG Pipeline" class="img-fluid">
    <div class="figure-caption">Figure 2: RAG Pipeline for Grounding LLM Commands</div>
</div>

To solve this, we integrated a **Retrieval-Augmented Generation (RAG)** pipeline. We use a **FAISS** vector database to store real-time information about the robot's environment, including the names, locations, and properties of all objects. When a user issues a command, the RAG system first retrieves the most relevant contextual information from this database. This context is then injected into the prompt provided to GPT-4o, effectively "grounding" the model in the current reality of the scene. 

This significantly enhances the accuracy of command and parameter resolution, ensuring the robot acts on facts, not fiction.

## Validation and Quantitative Results

We rigorously evaluated the RoboCHAT system's ability to interpret a wide range of commands.

<div class="text-center">
    <img src="/assets/images/robochat/results.png" alt="Performance Results" class="img-fluid">
    <div class="figure-caption">Figure 3: System Performance Evaluation Results</div>
</div>

### Benchmark Setup

The system was tested on a suite of **172 distinct test cases** covering diverse manipulation and navigation tasks within a simulated kitchen environment.

### Performance Metrics

We measured two key performance indicators:

1. **Command Resolution Accuracy**: The system's ability to correctly identify the intended high-level command (e.g., distinguishing a `pick_up` from a `place` command).
2. **Parameter Resolution Accuracy**: The system's ability to correctly extract all necessary parameters (e.g., identifying the correct object, `red bowl`, and destination).

### Results

The results demonstrated the robustness of our approach:

| Metric | Accuracy |
|--------|----------|
| Command Resolution | 89% |
| Parameter Resolution | 85% |
| Overall System Performance | 87% |

This high level of performance validates the effectiveness of the two-layer architecture and the RAG pipeline in translating ambiguous human language into precise, executable robotic actions.

## Key Technical Contributions

1. **Two-Layer Architecture**: Separation of concerns between natural language processing and robotic execution
2. **RAG Integration**: Grounding LLM responses with real-time environmental context
3. **High-Level API Design**: Abstraction of complex robotics frameworks for accessibility
4. **Comprehensive Evaluation**: Rigorous testing across diverse robotic manipulation tasks

## Conclusion

The RoboCHAT project successfully demonstrates a powerful and accessible paradigm for human-robot interaction. By abstracting complexity through a backend API and leveraging an LLM grounded by a real-time RAG pipeline, it empowers non-expert users to command sophisticated robotic systems through simple, natural language. 

This work represents a significant step toward closing the automation gap and unlocking the full potential of service robots in everyday human environments.
