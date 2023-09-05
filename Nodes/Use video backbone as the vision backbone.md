---
aliases: []
tags: [review]
title: Use video backbone as the vision backbone
date created: Friday, September 1st 2023, 1:25:34 pm
date modified: Monday, September 4th 2023, 11:40:41 am
---
In our [[202308092107|Thesis Proposal newest]], the task of visual backbone is to provide tokenizable, visual information to the agent, such that the agent can know the **environmental change** happened during the intervention.

A video backbone like [[Vid2seq]], which provides dense captioning on the video can be helpful, but the environment for vid2seq to work is a bit unstable.

You can also consider [[VideoMAE]] which is directly available on the huggingface for the sack of simplicity of the experiment. But this potentially **requires tokenization**.

## References