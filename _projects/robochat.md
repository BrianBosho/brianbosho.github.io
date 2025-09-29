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
  - PyCRAM
  - FastAPI
---
## <i class="fas fa-bullseye mr-2"></i>Introduction: The Automation Gap
The demand for autonomous service robots is rapidly increasing, driven by needs in healthcare, logistics, and domestic assistance. However, the utility of current systems is severely limited by what we term the "automation gap." Most service robots excel at executing static, pre-programmed tasks in highly structured environments but fail when faced with the need to adapt to dynamic conditions or interpret novel commands from non-expert users. This reliance on expert programming and hard-coded behaviors creates a significant barrier to widespread adoption.

The central problem this project addresses is: How can we enable a sophisticated robot to understand and execute complex, multi-step tasks described in natural language, without requiring the user to have any programming expertise?

This work presents RoboCHAT, a system that bridges this gap by leveraging the reasoning capabilities of Large Language Models (LLMs). Our thesis is that by creating a decoupled, two-layer architecture—separating the high-level reasoning (LLM agent) from the low-level execution (robotics framework)—we can create a system that is both intelligent and robust. The core of this solution lies in a novel RAG pipeline that grounds the LLM agent in the robot's specific capabilities and its immediate environmental context.

## <i class="fas fa-sitemap mr-2"></i>System Architecture & Design Rationale
The core challenge is translating high-level, often ambiguous human language into the precise, low-level commands a robot can execute. The solution is a decoupled, two-layer system designed for modularity and robustness. This separation of concerns—an intelligent agent for intent translation and a stable API for robot execution—was a critical design choice to simplify development and debugging.

<figure class="figure w-100 text-center my-4">
<img src="https://www.google.com/search?q=https://placehold.co/800x400/007bff/ffffff%3Ftext%3DSystem%2BArchitecture%2BDiagram" class="figure-img img-fluid rounded shadow-sm" alt="RoboCHAT System Architecture Diagram">
<figcaption class="figure-caption text-center mt-2">A high-level diagram of the RoboCHAT architecture. The frontend agent interprets user intent, while the backend API executes the commands.</figcaption>
</figure>

## <i class="fas fa-cogs mr-2"></i>Methodology & Implementation
1. The Foundation: PyCRAM
The system's execution layer is built upon PyCRAM (Cognitive Robot Abstract Machine), a powerful framework for designing and executing complex robotic plans. PyCRAM, based on probabilistic programming, allows for defining flexible, goal-oriented behaviors rather than hard-coded scripts. This was selected as the foundation because it provides the robustness needed to handle variability in a real-world environment.

2. The Backend: RoboCRAM Middleware
While PyCRAM is powerful, its interface is not directly accessible to a modern LLM. To solve this, a middleware API named RoboCRAM was developed. Built using Python and FastAPI, RoboCRAM exposes PyCRAM's core functionalities as a clean, high-level HTTP REST API. FastAPI was chosen for its high performance, automatic documentation generation, and native support for asynchronous operations, which is crucial for managing long-running robotics tasks.

The API translates web-friendly JSON commands into the symbolic plan language that PyCRAM understands. Below is an example of the communication protocol:

{
  "action": "move-to",
  "parameters": {
    "target": "kitchen_counter",
    "speed": 0.8
  }
}

3. The Frontend: RoboCHAT AI Agent
The "brain" of the system is the RoboCHAT agent, which interprets natural language. Constructed using LangChain and powered by the GPT-4o model, its primary function is to convert a user's request (e.g., "get me the milk from the fridge") into a structured series of calls to the RoboCRAM API.

A simple LLM call is insufficient for this task. Therefore, a Retrieval-Augmented Generation (RAG) pipeline was integrated. Using FAISS as the vector store (chosen for its speed and low memory footprint), the agent was provided with a knowledge base containing:

Robot Capabilities: A set of Markdown files, each documenting a RoboCRAM API endpoint, its function, and its required parameters.

Environmental Context: A dynamically updated JSON file representing the objects, surfaces, and their states within the robot's current environment.

This allows the agent to reason about commands, resolve ambiguity, and dynamically generate valid, multi-step execution plans.

<div class="tech-stack-card">
<h4><i class="fas fa-tools mr-2"></i>Key Technologies</h4>
<div class="row">
<div class="col-md-6"><strong class="tech-item">Programming Language:</strong> Python</div>
<div class="col-md-6"><strong class="tech-item">AI Framework:</strong> LangChain</div>
<div class="col-md-6"><strong class="tech-item">LLM Backbone:</strong> GPT-4o</div>
<div class="col-md-6"><strong class="tech-item">Vector Store:</strong> FAISS (for RAG)</div>
<div class="col-md-6"><strong class="tech-item">Robotics Framework:</strong> PyCRAM</div>
<div class="col-md-6"><strong class="tech-item">API Framework:</strong> FastAPI</div>
</div>
</div>

## <i class="fas fa-chart-line mr-2"></i>Evaluation & Results
The system's performance was evaluated on a benchmark of 30 complex kitchen tasks within the Bullet World simulation environment. The benchmark included tasks for manipulation, perception, and environmental queries.

<div class="results-card">
<div class="row">
<div class="col-md-6 mb-3 mb-md-0">
<div class="stat"><span class="stat-value">89%</span>Command Resolution Accuracy</div>
</div>
<div class="col-md-6">
<div class="stat"><span class="stat-value">85%</span>Parameter Resolution Accuracy</div>
</div>
</div>
</div>

The results confirm that the two-layer architecture provides a robust and effective method for translating natural language into successful robotic actions. Key failure modes were observed in tasks requiring complex spatial reasoning (e.g., "place the cup behind the bowl"), highlighting an area for future work.

## <i class="fas fa-code-branch mr-2"></i>Resources, Reproducibility & Future Work
This project was designed with reproducibility in mind. The complete source code, presentation slides, and other resources are available below. We encourage others to build upon this work.

<ul>
<li><a href="https://github.com/brianbosho/robochat" target="_blank"><strong><i class="fab fa-github mr-2"></i>View the Code on GitHub</strong></a></li>
<li><a href="#link-to-your-presentation.pdf" target="_blank"><strong><i class="fas fa-file-powerpoint mr-2"></i>View the Final Presentation Slides</strong></a></li>
<li><a href="#link-to-your-demo-video" target="_blank"><strong><i class="fas fa-video mr-2"></i>Watch the Demo Video</strong></a></li>
</ul>

Future work will focus on improving spatial reasoning capabilities, potentially by integrating a Vision-Language Model (VLM) for richer scene understanding, and exploring multi-robot coordination through the API.