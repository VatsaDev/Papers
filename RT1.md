# Robotics transformer RT-1

## Intro
 - Generalist robot data is important to making the robot better at all tasks, especially in low data robotics
    - Data is a large problem to robotics, due to each robot having specific data
    - once again mutlitask training is useful to generalization
 - images text -> robot actions 

## system
 - uses nlp(verbs, nouns, etc) to actions
    - verbs actions (open, grab, pick, etc)
    - noun identification (Apples, coke cans, etc)
 - loops through process of (images text) to (action) until it emits stop tokens

## RT-1
 - use the outputs of 6 images through imagnet to make visual output tokens
 - text is tokenization and embeddings
 - action is emitted as robot movements
