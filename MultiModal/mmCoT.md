# Multimodal Chain of Thought

## Introduction
 - vision greatly increases the world model of an MM-LLM
 - CoT with Multimodal is a performance boost?
 - 1b models with vision/cot, surpass gpt 3.5?

## background
 - CoT works for LLMs
 - problem decomposition
    - break the problem down to sub problems, run CoT on those

## Multimodal CoT
 - text only CoT at 1b size is terrible, drops accuracy (Maybe the models need to be conditioned for reasoning first?)
 - vision increases accuracy in spatial accuracy due to visuals
 - Multimodality increases convergence (hmm.. is it just a small model thing or a perhaps more modalities = more complete world model = better convergance? Gato would say otherwise, but maybe too many tasks for its size)


## future work
 - CoT + more modalities, better performance
 - need higher quality data, more data, and filtering/reasoning