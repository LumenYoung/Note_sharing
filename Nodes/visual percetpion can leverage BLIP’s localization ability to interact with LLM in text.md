---
aliases: []
tags: []
title: visual percetpion can leverage BLIP’s localization ability to interact with LLM in text
date created: Saturday, September 2nd 2023, 1:38:53 am
date modified: Saturday, September 2nd 2023, 1:44:35 am
---

Blip can output a attention heat map given a prompt. This is a very versatile and powerful tool to interact with LLM.

In the static camera setup for example, the attention map between “object” and “end effector” can be used to compute the relative position between objects and robot arm.

Such interaction can be very smoothly integrated into the LLM since it doesn’t involve injecting image token.

## References