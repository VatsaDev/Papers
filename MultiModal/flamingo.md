# Flamingo: VLM

## Intro
 - shows zero-shot adaptations to new tasks
 - performance increases few-shot
 - built from two frozen models, vision+LM
 - uses perciever resamplers

## model
 - LM+vision
 - perciever resampler
    - coverts the feature map to a couple tokens
 - Data
    - M3W(interleaved)
    - collected image/video

## future work
 - pretrain from scratch
 - more data more tasks