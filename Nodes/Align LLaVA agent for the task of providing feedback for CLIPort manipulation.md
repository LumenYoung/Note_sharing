---
aliases: []
tags: [thesis, review]
title: Align LLaVA agent for the task of providing feedback for CLIPort manipulation
date created: Tuesday, October 24th 2023, 2:41:19 pm
date modified: Tuesday, October 24th 2023, 3:35:33 pm
---

Overall, we have two different approaches that can be helpful to the feedback agent. prompt engineering as well as fine-tuning the model. We should always choose the prompt engineering before the fine-tuning.

This page is **discussing only the grounding of feedback agent** on providing valuable feedback on each execution, whereas the high-level language-agent improvement on solving long-horizen task or automatically devide task into sub-tasks is not discussed in this page.

## Prompt engineering

Several aspects of the improvements could be added to the prompting of LLaVA, each of them could be helpful in solving a specific lacking of the model’s capability.

1. Image included few-show demonstration
2. Goal awareness as well as its corresponding output structure,
3. manual instruction:

### Fix 1: Image included few-shot demonstration

Previously we experimented with providing demonstration like the following:

> system: In the image {DEFAULT_IMAGE_TOKEN} is a robot several objects on the table, in {DEFAULT_IMAGE_TOKEN} is the outcome.
>
> goal:  
> Describe the color and shape of the object starting with "object:".  
> Describe the motion (most importantly direction in left, right, up, down) of the robot starting with "motion:".  
> Keep all descriptions short and simple. Reply with nothing irrelevant.
>
> example:  
> object: the object is a red, square block  
> motion: the robot arm is moving to the left

The problem is that such demonstration has very strong influence on the output of LLM. The model has very strong probability to produce exact same output as the example.

Also, the example is a partial demonstration, providing only the answer in hope that the model will establish correlation between the image token and the answer. This capability is not yet presented from LLaVA.

Therefore, We can provide several image included demo with the example answer to guide the model to focus on the variances from consecutive images.

> system: In the image {DEFAULT_IMAGE_TOKEN} is a robot several objects on the table, in {DEFAULT_IMAGE_TOKEN} is the outcome.
>
> goal:  
> Describe the color and shape of the object starting with "object:".  
> Describe the motion (most importantly direction in left, right, up, down) of the robot starting with "motion:".  
> Keep all descriptions short and simple. Reply with nothing irrelevant.
>
> example:  
> Given {DEFAULT_IMAGE_TOKEN} and {DEFAULT_IMAGE_TOKEN}.  
> object: the object is a red, square block  
> motion: the robot arm is moving to the left

**Improved aspect**:

This fix could be helpful in several aspects:

1. grounding model on egocentric terms (provided in Fix 3)
2. grounding model’s focus on task specfic aspects in the image (provided in Fix 4)

**Expected possible failure cause**: LLaVA is only trained on single image dataset, too many image token included might disturb the model and downgrade the performance.

### Fix 2: include goal of the task

The language goal in the cliport demonstration could also be presented to the LLaVA. This cloud be helpful to simplify the task of LLaVA to only assess if the condition is reached.

**Improved aspect**: CLIPort is its limitation of not able to determine if the task is accomplished or not. Adding such external criterion could turn a failed execution into a multi-round try-and-error trial.

### Fix 3: manually specified direction convention

The term left and right could be ambiguous, depended if you are putting yourself into the view of robot or the camera. We could make it clear in the demonstration.

==unsolved problem here==: We are using the front camera (the camerae in front of the robot that has full view on the table) as the observation for the feedback agent. It is possible in this case to specify left and right

### Fix 4: manually specified task specific cue

Different tasks have different criterions to its success, each of them should require different focus from the feedback model.

**Example 1**: the precise description of blocks shape is important in the task of `block-insertion`, which is not that important when executing `palletizing-boxes`.

**Example 2**: In the task of `palletizing-boxes`, for each execution, it is important if it’s placed in the goal area, providing the relative direction of manipulation is not relevant in this case.

**Example 3**: In most of the task, the criterion of each steps success is the change of objects location before and after an action.

A possible way to insert such task specific cue:

## Finetuning the model (TODO)

After we’ve collected bunch of valuable feedbacks from our demonstrations, we can use this dataset to further finetuning the LLaVA to suit our work.

This might be a

## References