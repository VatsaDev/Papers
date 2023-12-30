# Gato: A generalist agent

## Intro
 - Trained on 604 tasks in varying modalities (Atari, Robotics, Text, Images, 3D)
 - 1.2B parameter transformer model

## Model
 - Trained on as many varietes of data as possible
 - All the modalities are tokenized into a sequence
 - Tokenizer
    - Text: Sentencepiece tokenizer size 30K
    - Images: ViT patches
    - Discrete values: (Atari btn press, etc.), Flattened into sequences of integers
    - Continous values: (sensor inputs, joint movements), flattened into floating point sequences
 - Rather than having a tag for every task, they format the prompts to be somewhat unique per task, but with general action tokens 

## datasets
 - large amounts of high quality RL data from sota agents
 - Game play datasets
 - image/text/interleaved data

## observations
 - the agent can generalize somewhat to brand new tasks, larger models are better

## limitations
 - Robotics and RL tasks are hard to get, very limited data
 - 1024 ctx is a couple steps worth IRL actions, long term agents will require a ctx len in the millions

## Future Work
 - More CTX len
 - more tasks/scale/data
 - maybe adding some meta learning abilities to generalize better to out of distribution tasks