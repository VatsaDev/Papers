# DPO: Your Language Model is Secretly a Reward Model

## Abstract
 - LLMs are broad, but hard to get precise behaviour from
 - Methods like RLHF are complex/unstable, and require human gathered prompts, need RL
 - Parameterzing the reward modelby getting corressponding closed policy
 - Solve RLHF with a simple classification task
 - DPO is lighter, faster, more stable, and better than RLHF

## Intro
 - LLMs model data, yet there is data we want them to just understand, not replicate
 - selecting a models desired responses and behavior apart from its knowledge
 - RLHF worked, but signifigantly more complex than DPO
 - DPO increases the relative logprob difference between Desired and undesired responses 

## DPO
 - estimate the divergence, and maximise it
 - get the logprobs of comparison data
 - update gradients accroding to reward function
 - reward models can be LLMs if consistent with bradley-terry
 - previous methods would use Human Baseline as normalization, bad 