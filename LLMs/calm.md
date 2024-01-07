# LLM aug LLM: Calm

## Intro
 - can one augement an LLM to the ability of the specialized LLM
 - typical approach to continue pretrain of base model, its expensive
 - working with model is better as it allows the use of existing models, cheaper
 - Calm method
    - has 1 or more LLMs
    - does not modify weights
    - needs a small amount of data showing both skills combined

## CALM
 - the goal is to learn a composition between two models
 - learn a linear transform and some cross attention layers
 - forms compositional layers
 - matches KV

## future work
 - acquiring distinct knowledge, from multiple models