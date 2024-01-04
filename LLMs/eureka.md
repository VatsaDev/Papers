# Eureka, 

## Intro
 - LLMs are good robotics planners, but cant manipulate low level motions
 - RL is good, but RL rewards are difficult to design
 - design a universal reward algo, with Code LLMs
 - use code llms as programming agents to define rewards
 - The eureka algo
    - give GPT-4 Enviorment code + instructions
    - GPT-4 makes RL rewards
    - Train the RL
    - give gpt-4 feedback, update reward code
 - achieves human level performance on reward design
 - gradient free RL
 - eureka is generalizable due to 
    - enviorment as context: Zero-shot design rewards
    - evo-search: iterativly deal with train batches
    - reward reflection: allows for targeted reward edits

## Method
 - feed the model the enviorment code, with reward function
     - The enviorment source code contains more details about the env. then any inst.
     - the first draft reward isnt always right/sub-optimal
 - due to evo search, the more samples, the more buggyness decreases
 - more samples = more chances for reward mutation, less sub-optimal rewards
 - One can provide the model the reward function outputs, but the cost values dont tell the model whats wrong with the reward function, so they give scalar vals of all reward values along with cost

## Results
 - eureka outperforms humans, consistenly improves over time
 - generates novel rewards, models very differently from humans for harder tasks
 - eureka can improve/benefit from human reward functions
