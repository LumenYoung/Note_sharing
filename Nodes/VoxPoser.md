---
Status:
aliases: [thesis paper 15]
tags: [MTpaper]
title: VoxPoser
date created: Thursday, August 17th 2023, 3:50:04 pm
date modified: Wednesday, August 30th 2023, 3:36:39 pm
trained: false
dataset: "None"
training_resource: 
reproducibility: true
baseline: 
metric_baseline: 
high_success_rate: yes, 88% stat 
open_sourced: "Yes, in progress"
traj_rep: "End effector waypoints"
perception_model: "OWL-ViT for bounding box, SAM mask, XMEM track, RGB-D -> point cloud"
---

## VoxPoser

VoxPoser uses [[LLM]], [[VLM]]s and a learning-based motion planning model to form an robot agent that is capable of accomplish many different planning skills.

Motivation: [[VoxPoser starts from the perspective to ground language instruction to robot action]]

[[VoxPoser’s visual perception pipeline involves many VLMs]]. CLIP, XMEM and SAM are all used to compose a visual pipeline. [[VoxPoser uses the LLM’s coding ability to write language model program (LMP)]], which is the mean interaction interface from LLM.

### Questions

before reading

- [ ] How does 3D vox help replacing the motion primitive?
- [ ] What function are VLM, LLM and model for planning have

after reading

### Ideas

### Details

Affordance map and Constraint map

## References