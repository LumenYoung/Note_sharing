---
Status:
aliases: [RoboAgent, thesis paper 14]
tags: [flashcards/thesis/todo, review, MTpaper]
title: RoboAgent
date created: Tuesday, August 15th 2023, 3:47:32 pm
date modified: Wednesday, August 30th 2023, 3:34:07 pm
trained: true
dataset: "RoboSet"
training_resource: 
reproducibility: true
baseline: 
metric_baseline: 
high_success_rate: 
open_sourced: "Yes, in progress"
traj_rep: "Action Chunks produced by CVAE"
perception_model: "integrated in MT-ACT, SAM for semantic segmentation and inpainting"
sr-due: 2023-09-04
sr-interval: 4
sr-ease: 270
---

## RoboAgent

In RoboAgent, authors propose an agent using [[MT-ACT|multi-task action-chunking transformer (MT-ACT)]]. [[Semantic segmentation using foundation model]] helps to enrich the dataset with no extra cost, **enable training on a small dataset**. [[Action-chunking provides an efficient action representation]], that enables better the learning of the action from multi-modal data into *a single multi-skill multi-task policy*.

One of the main motivation for RoboAgent is the *paucity of the robotic dataset*. They argue that the diversity of the dataset is the key reason for generalizing on limited data budget.

### Questions

Questions

- How exactly is the training process?
- Semantic Augmentation?
- Source code ready to explore?
- How it connect to the low level?

During the reading

- What policy exactly means here?

### Ideas

### Details

The work focus on **learning individual skills** of manipulation, while the **ability to compose different skills** to finish a long-horizen task is not solved.

Comparaison with other previous robot multi-task learning approach

| Previous approaches                                  | Comp. disadvantage with RoboAgent                         |
| ---------------------------------------------------- | --------------------------------------------------------- |
| RL in simulation                                     | focus on narrow domain OR only evaluate in sim            |
| Large scale sim + sim2real                           | limited generalization on real world                      |
| Large scale real teleOp dataset + imitation learning | too many data requirement AND less generalization ability |

## References