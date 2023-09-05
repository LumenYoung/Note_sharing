---
aliases: []
tags: []
title: The choice of the LLM for our agent
date created: Tuesday, September 5th 2023, 10:18:31 am
date modified: Tuesday, September 5th 2023, 11:09:56 am
---

The primary concern when it comes to the choice of LLM is its **code writing ability**. GPT-4 is winning in this aspect for its prodominant coding ability among all other LLMs.

However, it is possible that our experiments would require large numbers of token. **Due to the budgetary concern, we can also switch to locally host Code LLAMA**. Eventhough Code LLAMA is still eclipsed by GPT-4, its 35B model has surpassed the GPT-3.5 on coding ability and therefore can be considered to use in local cases.

In terms of the resource requirement, LLAMA 2 quantized version can run 65B model with 35 GB of ram on CPU. The inference speed of model run on CPU could pose a limitation, as too slow token generation constraints the conduct of experiments.

Using the speculative sampling, a 30B model aided by a 7B model (totoal 24 GB of ram in quantized version) run on CPU can [output token at 180ms/token](https://github.com/ggerganov/llama.cpp/issues/2030#issuecomment-1694585487), roughly 5 token per second, which is definitely usable for most of the use cases.

## References

The [speedup estimation](https://github.com/ggerganov/llama.cpp/pull/2926#issuecomment-1700992137) of using Speculative Sampling from the llama.cpp author:

> ~2x speedup for 34B/7B and ~1.5x speedup for 13B/7B pairs using `--top_k 1` sampling. In such scenarios, the acceptance rate is above 75% which helps a lot.  
> If you try to generate free-form text, then the acceptance rate drops significantly and the method does not offer any benefit. My gut feeling is that this might be very efficient for cases where we have a very constrained grammar.

Code LLAMA for llama.cpp checkpoints [here](https://huggingface.co/TheBloke/CodeLlama-34B-GGUF)