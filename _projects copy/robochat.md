---
layout: project
title: "RoboCHAT: LLM-Powered Human-Robot Interaction"
permalink: /projects/robochat/

# For the project list page
image: "assets/images/robochat/robochat.jpg"
context: "Capstone Project at Carnegie Mellon University Africa"
summary: "Developed an LLM-powered system that achieved 89% command accuracy, enabling a service robot to perform complex tasks from natural language instructions."

# For the detailed project page
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
  - RAG pipeline integration
  - Evaluation on a 30-task benchmark

date: 2025-06-01
selected: true
---

### Key Achievements
- ✅ **89%** command resolution accuracy
- ✅ **85%** parameter resolution accuracy
- 🤖 Enabled a PR2 robot to perform **30 unique benchmark tasks**
- 🧠 Integrated a **RAG pipeline** for crucial contextual awareness

---

### The Challenge: The "Automation Gap" in Service Robotics
Most service robots are programmed for fixed functions and struggle with dynamic environments or novel user requests. This "automation gap" limits their usefulness, as non-expert users cannot easily command them to perform complex, multi-step tasks. My goal was to create a system that allows anyone to control a sophisticated robot using simple, natural language.

### My Contribution: A Two-Layer System for Intelligent Control
I co-architected and developed a system with two primary components designed to translate human intent into precise robot actions:

* **RoboCRAM (The Backend)**: I built the middleware API to create a stable, high-level interface for the robot. This abstracted the complex, low-level functions of the PyCRAM robotics framework into a set of clear, reliable commands.
* **RoboCHAT (The Frontend)**: We built an advanced AI agent using GPT-4o and LangChain to interpret natural language commands. To make the system context-aware, I integrated a Retrieval-Augmented Generation (RAG) pipeline with a FAISS vector store. This gives the LLM a knowledge base of the robot's capabilities and environment, enabling it to resolve ambiguous commands and ask clarifying questions.

### 🔗 Project Resources & Links
The best way to see RoboCHAT in action is to watch the demo and explore the code.

- **[▶️ Watch the Demo Video]({your_youtube_or_vimeo_link_here})**: A short video showcasing the robot executing multi-step tasks from natural language commands.
- **[💻 View the Code on GitHub]({self.code_url})**: Access the complete source code for both the RoboCRAM backend and the RoboCHAT agent.
- **[📄 Review the Presentation Slides]({link_to_your_slides.pdf})**: A detailed overview of the project architecture, methodology, and evaluation results.

---

### Impact & Results
We evaluated RoboCHAT on a benchmark of 30 complex kitchen tasks. The system achieved **89% command resolution accuracy** and **85% parameter resolution accuracy**, successfully transforming a fixed-function robot into a flexible, user-centric assistant. This work demonstrates a viable path toward making advanced service robots accessible and useful in everyday human environments.