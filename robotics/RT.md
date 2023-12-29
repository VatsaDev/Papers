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

## future work
 - imitation learning, hasnt surpassed human control
 - can only use defined actions, cannot create an entire new action
 - more data, more robots
 - scale model, faster robot 

# RT-2

## Intro
 - use web data?
 - train vision-language models to output low-level robot actions
 - tokenizing actions to text tokens
 - robotics actions are much more capable, after learning spatial comparisons through images
 - limited by robotics data, but can use actions much better from images, etc

## vision-language-actions
 - start with VLMs like Pali-x and PalmE
 - finetuned on action tokens like RT-1, discrete values
   - 256 tokens reserved robot actions, (terminate, xpos, ypos, zpos, xrot, yrot, zrot, gripper extension)
 - finetuning on both web-data and robotics data is better than just robotics data, makes the model more generalizable
 - when it has to be a robot action (<action> tag is on) then sample differently from normal, only robo action tokens pass through, making sure every action is valid

## performance
 - web data helps the model generalize to unseen backgrounds/objects
 - better understanding of semantics/visual concepts
 - better symbol understanding/reasoning
 - robotics CoT works, vision-language-action chain