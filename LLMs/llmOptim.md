# LLMs as optimizers

## Intro
 - OPRO, optimizing by prompting
 - use linear regression and travelling salesman
 - the LLM prompt is the optimizer, called the meta prompt
 - Loop the meta prompt, score generated solutions, return the best one

## llm op
 - LLM usefulness
    - language descriptions
    - tradeoff in exploration and exploitation
 - Meta prompt design
   - describe the optimization problem description
   - they can also find patterns from in context descriptions, and follow through
 - the best prompt was just the CoT one, take a deep breath and think step by step

## future work
 - more info on errors