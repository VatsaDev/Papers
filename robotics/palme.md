# Palm E

## Intro
 - LLM controlling robot? Curious on that, great grounding
 - Robots have sensors as modalitites
 - Multimodal sentences input to the robot

## Arch
 - PalmE is an embodied language model, 
    - constantly getting inputs from sensors/motors
    - enables the llm to make grounded descisions
 - Interleaved embeddings 
    - They start from pretrained palm, and inject the modalities through encoders

## multitask, multimodal
 - Multitask finetuning is better than single task tuning (more generalization, better at every task?)
 - MultiTask finetuning is really good for robotics, makes few-shot 1-shot etc, much better
 - Palm E 562B params, 540b palm + 22b Vit
 - Also good at Multimodal CoT, Math from images
 - Hmm emboided agent actions are based on low levels already existing for the llm to use, function calling?
 - Modalities
    - State vector (Robot body position?)
    - Vision, ViT
    - Text

## robotics
 - Co-Training every robot on its tasks + all the other robots tasks makes each robot better at their tasks
 - Robot commands in a loop
    - Instruction
    - Robot actions
    - image verification of action completion
    - more instructions

## future work
 - more robot data / data efficiency