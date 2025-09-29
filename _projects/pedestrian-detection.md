---
layout: project
title: "Pedestrian Detection and Depth Estimation for Autonomous Vehicles"
permalink: /projects/pedestrian-detection/
date: 2024-05-15

image: "assets/images/pedestrian-detection/depthest.jpg"
context: "Course Project, Carnegie Mellon University Africa"
summary: "Built a computer vision pipeline that detects pedestrians with YOLOv5 and estimates their distance using monocular depth estimation."

subtitle: "Computer Vision for Safer Autonomous Driving"
code_url: "https://github.com/brianbosho/pedestrian-detection"
role: "Team Member (Detection & Depth Integration)"
technologies:
  - Python
  - PyTorch
  - YOLOv5
  - MiDaS
  - CityPersons Dataset
  - OpenCV
selected: true
---

## At a Glance
- Fine-tuned **YOLOv5** on the CityPersons dataset for pedestrian detection  
- Integrated **MiDaS** for monocular depth estimation  
- Combined outputs to label pedestrians with both bounding boxes and distance estimates  
- Demonstrated live inference on images and video frames  

---

## The Challenge
Autonomous vehicles need to detect pedestrians quickly and accurately, even with limited sensors.  
Using just a monocular camera is cost-effective, but makes depth estimation especially challenging.  

---

## What We Did
As part of a team project, I focused on building the detection and depth pipeline:  

- **Detection**: trained YOLOv5 on the CityPersons dataset to identify pedestrians in urban scenes.  
- **Depth estimation**: used MiDaS (a monocular depth estimation model) to compute distance from single RGB frames.  
- **Integration**: combined the two outputs so each detected pedestrian was annotated with an estimated distance.  

---

## Results
- YOLOv5 achieved good detection accuracy after fine-tuning.  
- The combined system produced bounding boxes with approximate depth for each pedestrian.  
- Demonstrated the approach in a live demo, processing video frames in real time.  

---

## Impact
This project showed that it’s possible to use affordable, monocular-camera setups to improve pedestrian safety in autonomous driving.  
It’s a small step toward building robust perception systems for traffic in resource-constrained contexts.  

---

## Resources
- [GitHub Repository](https://github.com/brianbosho/pedestrian-detection)  
- [Slides / Report](link-if-available)  
