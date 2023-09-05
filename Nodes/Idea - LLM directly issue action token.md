---
aliases: []
tags: []
title: Idea - LLM directly issue action token
date created: Friday, September 1st 2023, 2:05:51 pm
date modified: Friday, September 1st 2023, 2:19:08 pm
---

LLM are good next-token predictor, they can continuously predict new tokens based on current states. Suppose each token to contain information on both current desire and robot state, and suppose we have the mean the decouple the action from it, then such continously predicting machine can be suitable for the robot manipulation task.

The problem currently is **the high frequency nature of the action tokens**, such detailed control on each action at each time fully occupies the context window quickly, makes it impossible to preserve the long-horizen context.

Also, LLM are not pretrained on such semantically sparse, detailed control tasks. Therefore it can be anticipated to yield bad performance on such task.

[[RoboAgent]] provides a solution by converting robot action using action chunking, and such condensed representation created by CVAE are more efficient, more high-level, seems to be able to address the problem described above.

==Validation needed==

The original thoughts was to **build an agent to autonomously learn to interact with such tokens**. But I find it an unnecessary component to the original idea as there are more important contributions in the original idea, so I seperated this from the original idea and **this idea has very low priority**.

Anticipated obstacles

- Many studies show that code is a better, more structured interface for LLMs. Predicting raw actions are feasible only if we finetune LLM on datasets.
- It is not yet clear how to combine goal and state in each token.
- Even the action chunking can provide a condensed version of representation, trajectory language still has sparse semantic than the natural language, it is doubtful how good the performance could be.

## References