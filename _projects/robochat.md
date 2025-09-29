---
layout: project
title: "RoboCHAT: LLM-Powered Human-Robot Interaction"
permalink: /projects/robochat/
date: 2025-06-01

image: "assets/images/robochat/robochat.jpg"
context: "Capstone Project, Carnegie Mellon University Africa"
summary: "Designed a two-layer system that lets a PR2 robot execute complex tasks from natural language instructions, bridging the automation gap in service robotics."

subtitle: "Natural Language Interfaces for Service Robots"
code_url: "https://github.com/brianbosho/robochat"
role: "Co-Architect & Developer"
technologies:
  - Python
  - LangChain
  - GPT-4o
  - FAISS
  - RAG
  - PyCRAM
selected: true
---

## At a Glance
- Built a system for controlling robots with **plain English commands**  
- Combined an **LLM agent** with a **robot middleware (PyCRAM)**  
- Tested on **30 household kitchen tasks** using a PR2 robot in simulation  
- Achieved **89% accuracy in command interpretation** and **85% accuracy in parameter extraction**  

---

## The Challenge
Most service robots are programmed for fixed functions.  
They can’t easily adapt to new tasks or unstructured environments, and non-expert users have no simple way to give instructions.  
We wanted to explore whether large language models could close this “automation gap.”  

---

## What We Did
We built a **two-layer architecture**:  

- **RoboCRAM (backend)**: an API layer that exposed PyCRAM’s robot functions (grasping, moving, placing) in a clean and reliable way.  
- **RoboCHAT (frontend)**: an AI agent powered by GPT-4o and LangChain, which took user commands, resolved ambiguities using RAG, and translated them into robot actions.  

We tested the setup in simulation using the PR2 robot in BulletWorld.  

---

## Results
- **89%** of user commands were interpreted correctly  
- **85%** of parameters were extracted correctly  
- Successfully carried out multi-step household tasks like fetching and delivering objects  

---

## Impact
This project showed how LLMs can make robots more accessible by removing the need for expert programming.  
A caregiver, for example, could simply say *“bring me chapati from the counter”* — and the robot would complete the task without hardcoding.  

---

## Resources
- [GitHub Repository](https://github.com/brianbosho/robochat)  
- [Slides / Demo Video](link-if-available)  
