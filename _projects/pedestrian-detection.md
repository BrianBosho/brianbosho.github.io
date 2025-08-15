---
layout: project
title: "Computer Vision for Pedestrian Detection & Depth Estimation"
permalink: /projects/pedestrian-detection/

# For the project list page (project_item.html)
image: "assets/images/pedestrian-detection/depthest.jpg"
context: "Course Project: Applied Computer Vision"
summary: "Developed a two-stage perception system for autonomous vehicles, combining YOLOv5 for object detection and MiDaS for monocular depth estimation to identify and locate pedestrians in urban scenes."

# For the detailed project page (project.html)
subtitle: "A Two-Stage Perception System for Autonomous Vehicle Safety"
code_url: "https://github.com/brianbosho/pedestrian-detection"
role: "Co-Researcher & Developer"
technologies:
  - Python
  - PyTorch
  - YOLOv5
  - MiDaS
  - CityPersons Dataset
contributions:
  - YOLOv5 model fine-tuning
  - MiDaS integration for depth estimation
  - End-to-end pipeline development
  - Performance evaluation (precision/recall)
date: 2024-05-15
selected: false
---

### The Challenge: Ensuring Pedestrian Safety in Autonomous Driving
A primary function of an autonomous vehicle's (AV) perception system is to reliably detect vulnerable road users, especially pedestrians. This task is challenging due to varying lighting conditions, occlusions, and diverse human appearances. Our objective was to build a robust system using only a single camera (monocular vision) to not only detect pedestrians but also to estimate their distance—critical information for the vehicle's planning module.

An example of the system identifying a pedestrian with a bounding box and estimating their distance from the vehicle.

### My Solution: A Two-Stage Detection and Estimation Pipeline
I co-developed a perception pipeline that processes an image in two distinct stages:

*   **Pedestrian Detection with YOLOv5**: We first used YOLOv5, a state-of-the-art, real-time object detection model. I was responsible for fine-tuning the pre-trained model on the CityPersons dataset, a large-scale dataset specifically focused on pedestrians in urban environments. This specialization significantly improved the model's accuracy in identifying people.
*   **Monocular Depth Estimation with MiDaS**: Once a pedestrian is detected and a bounding box is drawn, the system crops that specific region of interest. We then feed this cropped image into the MiDaS model. MiDaS is a powerful deep learning model that excels at estimating the depth of objects from a single 2D image, providing the crucial distance information needed for safe navigation.

### Impact
Our integrated system successfully demonstrated the viability of a monocular, two-stage approach for pedestrian perception. After fine-tuning, the YOLOv5 detection model achieved a precision of 0.816 and a recall of 0.538 on the validation set. This project provides a strong proof-of-concept for building cost-effective yet capable perception systems for autonomous and driver-assistive technologies, contributing to the overall goal of improving traffic safety.


The Challenge: Ensuring Pedestrian Safety in Autonomous Driving
A primary function of an autonomous vehicle's (AV) perception system is to reliably detect vulnerable road users, especially pedestrians. This task is challenging due to varying lighting conditions, occlusions, and diverse human appearances. Our objective was to build a robust system using only a single camera (monocular vision) to not only detect pedestrians but also to estimate their distance—critical information for the vehicle's planning module.

An example of the system identifying a pedestrian with a bounding box and estimating their distance from the vehicle.

My Solution: A Two-Stage Detection and Estimation Pipeline
I co-developed a perception pipeline that processes an image in two distinct stages:

Pedestrian Detection with YOLOv5: We first used YOLOv5, a state-of-the-art, real-time object detection model. I was responsible for fine-tuning the pre-trained model on the CityPersons dataset, a large-scale dataset specifically focused on pedestrians in urban environments. This specialization significantly improved the model's accuracy in identifying people.

Monocular Depth Estimation with MiDaS: Once a pedestrian is detected and a bounding box is drawn, the system crops that specific region of interest. We then feed this cropped image into the MiDaS model. MiDaS is a powerful deep learning model that excels at estimating the depth of objects from a single 2D image, providing the crucial distance information needed for safe navigation.

Impact
Our integrated system successfully demonstrated the viability of a monocular, two-stage approach for pedestrian perception. After fine-tuning, the YOLOv5 detection model achieved a precision of 0.816 and a recall of 0.538 on the validation set. This project provides a strong proof-of-concept for building cost-effective yet capable perception systems for autonomous and driver-assistive technologies, contributing to the overall goal of improving traffic safety.