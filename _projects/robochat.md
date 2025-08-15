---
layout: project
title: "RoboCHAT: LLM-Powered Human-Robot Interaction"
permalink: /projects/robochat/

# For the project list page (project_item.html)
image: "assets/images/robochat/robochat.jpg"
context: "Capstone Project at Carnegie Mellon University Africa"
summary: "Architected a two-layer system to bridge the 'automation gap' in service robotics, enabling a PR2 robot to perform dynamic, multi-step tasks via natural language."

# For the detailed project page (project.html)
subtitle: "Enabling Natural Language Control for Complex Robotic Tasks"
code_url: "https://github.com/brianbosho/robochat"
role: "Co-Architect & Developer"
technologies:
  - Python
  - LangChain
  - GPT-4o
  - FAISS
  - RAG
  - PyCRAM
contributions:
  - System architecture design
  - RoboCRAM backend API development
  - RAG pipeline integration for contextual awareness
  - Evaluation on a 30-task kitchen benchmark

date: 2025-06-01
selected: false
---

The Challenge: The "Automation Gap" in Service Robotics
Most service robots are programmed for fixed functions and struggle with dynamic environments or novel user requests. This "automation gap" limits their usefulness, as non-expert users cannot easily command them to perform complex, multi-step tasks. Our goal was to create a system that allows anyone to control a sophisticated robot using simple, natural language.

A diagram showing the two-layer architecture of RoboCHAT, with the LLM-agent translating user commands into executable robot actions.

My Solution: A Two-Layer System for Intelligent Control
I co-architected a system with two primary components:

RoboCRAM (The Backend): I developed a middleware API that abstracted the complex, low-level functions of the PyCRAM robotics framework into a set of clear, high-level commands.

RoboCHAT (The Frontend): We built an advanced AI agent using GPT-4o and the LangChain framework. This agent interprets a user's natural language commands.

To make the system context-aware, I integrated a Retrieval-Augmented Generation (RAG) pipeline using a FAISS vector store. This allows the LLM to access a knowledge base of the robot's capabilities and the objects in its environment, enabling it to resolve ambiguous commands.

Impact
We evaluated RoboCHAT on a benchmark of 30 complex kitchen tasks. The system achieved 89% command resolution accuracy and 85% parameter resolution accuracy, successfully transforming a fixed-function robot into a flexible, user-centric assistant. This work demonstrates a viable path toward making advanced service robots accessible and useful in everyday human environments.